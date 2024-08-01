## My YouTube Channel
https://www.youtube.com/@JeganathanSwaminathan/videos

## My Blogs
<pre>
https://medium.com/@jegan_50867/docker-overview-be840f727b3

https://medium.com/tektutor/container-engine-vs-container-runtime-667a99042f3

https://medium.com/@jegan_50867/docker-commands-ba19387383b4

https://medium.com/tektutor/kubernetes-3-node-cluster-setup-50943378be41

https://medium.com/@jegan_50867/kubernetes-lightweight-developer-setup-using-rancher-k3d-a3a94e9b5eb4

https://medium.com/tektutor/kubernetes-3-node-cluster-using-k3s-with-docker-e325cc82fd50

https://medium.com/@jegan_50867/kubernetes-3-node-cluster-using-k3s-d28b2c09e2f7
</pre>


## References
<pre>
https://blog.networktocode.com/post/kubernetes-collection-ansible/

https://network-insight.net/2022/05/11/openshift-security-best-practices/ 

https://www.densify.com/openshift-tutorial/openshift-route/  
</pre>


# Installing Openshift on your laptop with Code Ready Containers(CRC)
```
https://developers.redhat.com/products/openshift-local/getting-started
```

## If you need openshift cluster setup on the RedHat cloud (free)
```
https://developers.redhat.com/developer-sandbox?source=sso
```


## Demo - ⛹️‍♀️ Installing Code Ready Containers - OpenShift Local in your Laptop/Desktop for learning purpose

Please do not attempt this exercise in our lab.  This will corrupt our existing OpenShift cluster.

The instructions are for your future reference purpose.  Feel free to try this in your home lab.

```
cd ~/Downloads

wget https://developers.redhat.com/content-gateway/rest/mirror/pub/openshift-v4/clients/crc/latest/crc-linux-amd64.tar.xz

tar xvf crc-linux-amd64.tar.xz

cd crc-linux-2.8.0-amd64/
sudo mv crc /usr/local/bin
```

### Starting the CRC setup
```
crc setup
```

Expected output
<pre>
[jegan@localhost ~]$ crc setup
INFO Using bundle path /home/jegan/.crc/cache/crc_libvirt_4.11.1_amd64.crcbundle 
INFO Checking if running as non-root              
INFO Checking if running inside WSL2              
INFO Checking if crc-admin-helper executable is cached 
INFO Checking for obsolete admin-helper executable 
INFO Checking if running on a supported CPU architecture 
INFO Checking minimum RAM requirements            
INFO Checking if crc executable symlink exists    
INFO Checking if Virtualization is enabled        
INFO Checking if KVM is enabled                   
INFO Checking if libvirt is installed             
INFO Installing libvirt service and dependencies  
INFO Using root access: Installing virtualization packages 
[sudo] password for jegan: 
INFO Checking if user is part of libvirt group    
INFO Adding user to libvirt group                 
INFO Using root access: Adding user to the libvirt group 
INFO Checking if active user/process is currently part of the libvirt group 
INFO Checking if libvirt daemon is running        
INFO Checking if a supported libvirt version is installed 
INFO Checking if crc-driver-libvirt is installed  
INFO Installing crc-driver-libvirt                
INFO Checking if systemd-networkd is running      
INFO Checking if NetworkManager is installed      
INFO Checking if NetworkManager service is running 
INFO Checking if /etc/NetworkManager/conf.d/crc-nm-dnsmasq.conf exists 
INFO Writing Network Manager config for crc       
INFO Using root access: Writing NetworkManager configuration to /etc/NetworkManager/conf.d/crc-nm-dnsmasq.conf 
INFO Using root access: Changing permissions for /etc/NetworkManager/conf.d/crc-nm-dnsmasq.conf to 644  
INFO Using root access: Executing systemctl daemon-reload command 
INFO Using root access: Executing systemctl reload NetworkManager 
INFO Checking if /etc/NetworkManager/dnsmasq.d/crc.conf exists 
INFO Writing dnsmasq config for crc               
INFO Using root access: Writing NetworkManager configuration to /etc/NetworkManager/dnsmasq.d/crc.conf 
INFO Using root access: Changing permissions for /etc/NetworkManager/dnsmasq.d/crc.conf to 644  
INFO Using root access: Executing systemctl daemon-reload command 
INFO Using root access: Executing systemctl reload NetworkManager 
INFO Checking if libvirt 'crc' network is available 
INFO Setting up libvirt 'crc' network             
INFO Checking if libvirt 'crc' network is active  
INFO Starting libvirt 'crc' network               
INFO Checking if CRC bundle is extracted in '$HOME/.crc' 
INFO Checking if /home/jegan/.crc/cache/crc_libvirt_4.11.1_amd64.crcbundle exists 
INFO Getting bundle for the CRC executable        
INFO Downloading crc_libvirt_4.11.1_amd64.crcbundle 
3.23 GiB / 3.23 GiB [-------------------------------------------------------------------------------------------------] 100.00% 9.16 MiB p/s
INFO Uncompressing /home/jegan/.crc/cache/crc_libvirt_4.11.1_amd64.crcbundle 
crc.qcow2: 12.49 GiB / 12.49 GiB [-------------------------------------------------------------------------------------------------] 100.00%
oc: 118.13 MiB / 118.13 MiB [------------------------------------------------------------------------------------------------------] 100.00%
Your system is correctly setup for using CRC. Use 'crc start' to start the instance
</pre>

### Starting the Local Openshift CRC single node cluster
```
crc start
```

Expected output
<pre>
[jegan@localhost ~]$ crc start
INFO Checking if running as non-root              
INFO Checking if running inside WSL2              
INFO Checking if crc-admin-helper executable is cached 
INFO Checking for obsolete admin-helper executable 
INFO Checking if running on a supported CPU architecture 
INFO Checking minimum RAM requirements            
INFO Checking if crc executable symlink exists    
INFO Checking if Virtualization is enabled        
INFO Checking if KVM is enabled                   
INFO Checking if libvirt is installed             
INFO Checking if user is part of libvirt group    
INFO Checking if active user/process is currently part of the libvirt group 
INFO Checking if libvirt daemon is running        
INFO Checking if a supported libvirt version is installed 
INFO Checking if crc-driver-libvirt is installed  
INFO Checking if systemd-networkd is running      
INFO Checking if NetworkManager is installed      
INFO Checking if NetworkManager service is running 
INFO Checking if /etc/NetworkManager/conf.d/crc-nm-dnsmasq.conf exists 
INFO Checking if /etc/NetworkManager/dnsmasq.d/crc.conf exists 
INFO Checking if libvirt 'crc' network is available 
INFO Checking if libvirt 'crc' network is active  
INFO Loading bundle: crc_libvirt_4.11.1_amd64...  
CRC requires a pull secret to download content from Red Hat.
You can copy it from the Pull Secret section of https://console.redhat.com/openshift/create/local.
? Please enter the pull secret *************************************************************************************************************
INFO Creating CRC VM for openshift 4.11.1...      
INFO Generating new SSH key pair...               
INFO Generating new password for the kubeadmin user 
INFO Starting CRC VM for openshift 4.11.1...      
INFO CRC instance is running with IP 192.168.130.11 
INFO CRC VM is running                            
INFO Updating authorized keys...                  
INFO Check internal and public DNS query...       
INFO Check DNS query from host...                 
INFO Verifying validity of the kubelet certificates... 
INFO Starting kubelet service                     
INFO Waiting for kube-apiserver availability... [takes around 2min] 
INFO Adding user's pull secret to the cluster...  
INFO Updating SSH key to machine config resource... 
INFO Waiting for user's pull secret part of instance disk... 
INFO Changing the password for the kubeadmin user 
INFO Updating cluster ID...                       
INFO Updating root CA cert to admin-kubeconfig-client-ca configmap... 
INFO Starting openshift instance... [waiting for the cluster to stabilize] 
INFO 3 operators are progressing: image-registry, network, openshift-controller-manager 
INFO 3 operators are progressing: image-registry, network, openshift-controller-manager 
INFO 3 operators are progressing: image-registry, network, openshift-controller-manager 
INFO 3 operators are progressing: image-registry, network, openshift-controller-manager 
INFO 2 operators are progressing: image-registry, openshift-controller-manager 
INFO 3 operators are progressing: image-registry, node-tuning, openshift-controller-manager 
INFO Operator openshift-controller-manager is progressing 
INFO Operator openshift-controller-manager is progressing 
INFO Operator openshift-controller-manager is progressing 
INFO Operator openshift-controller-manager is progressing 
INFO 2 operators are progressing: authentication, openshift-controller-manager 
INFO Operator authentication is progressing       
INFO Operator authentication is progressing       
INFO Operator authentication is progressing       
INFO Operator authentication is progressing       
ERRO Cluster is not ready: cluster operators are still not stable after 10m10.227355941s 
INFO Adding crc-admin and crc-developer contexts to kubeconfig... 
Started the OpenShift cluster.

The server is accessible via web console at:
  https://console-openshift-console.apps-crc.testing

Log in as administrator:
  Username: kubeadmin
  Password: gwifD-9W6K9-Hn3ey-h2Wwe

Log in as user:
  Username: developer
  Password: developer

Use the 'oc' command line interface:
  $ eval $(crc oc-env)
  $ oc login -u developer https://api.crc.testing:6443
</pre>
