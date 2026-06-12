---
title: "error during a update"
date: 2016-10-16
forum: General Help
---

### Post by ryadav on 2016-10-16
I got an error during an update, so I rebooted and performed a "sudo apt-get install -f" and got the following error:


~:$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic linux-headers-4.4.0-38 linux-headers-4.4.0-38-generic linux-image-4.4.0-31-generic linux-image-4.4.0-38-generic linux-image-extra-4.4.0-31-generic linux-image-extra-4.4.0-38-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-extra-4.4.0-43-generic (4.4.0-43.63) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-43-generic

gzip: stdout: No space left on device                                                                                                                                                                                                                           
E: mkinitramfs failure cpio 141 gzip 1                                                                                                                                                                                                                          
update-initramfs: failed for /boot/initrd.img-4.4.0-43-generic with 1.                                                                                                                                                                                          
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1                                                                                                                                                                                     
dpkg: error processing package linux-image-extra-4.4.0-43-generic (--configure):                                                                                                                                                                                
 subprocess installed post-installation script returned error exit status 1                                                                                                                                                                                     
dpkg: dependency problems prevent configuration of linux-image-generic:                                                                                                                                                                                         
 linux-image-generic depends on linux-image-extra-4.4.0-43-generic; however:                                                                                                                                                                                    
  Package linux-image-extra-4.4.0-43-generic is not configured yet.                                                                                                                                                                                             
                                                                                                                                                                                                                                                                
dpkg: error processing package linux-image-generic (--configure):                                                                                                                                                                                               
 dependency problems - leaving unconfigured                                                                                                                                                                                                                     
dpkg: dependency problems prevent configuration of linux-generic:                                                                                                                                                                                               
 linux-generic depends on linux-image-generic (= 4.4.0.43.45); however:                                                                                                                                                                                         
  Package linux-image-generic is not configured yet.                                                                                                                                                                                                            
                                                                                                                                                                                                                                                                
dpkg: error processing package linux-generic (--configure):                                                                                                                                                                                                     
 dependency problems - leaving unconfigured                                                                                                                                                                                                                     
No apport report written because the error message indicates its a followup error from a previous failure.                                                                                                                                                      
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.                                            
                                                                                                                                                                                                                    Errors were encountered while processing:   
 linux-image-extra-4.4.0-43-generic                                                                                                                                                                                                                             
 linux-image-generic                                                                                                                                                                                                                                            
 linux-generic                                                                                                                                                                                                                                                  
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ryadav on 2016-10-16
Just noticed the actual error message :) ... my boot partition just ran out of space.

Fixed with: sudo apt-get autoremove

To be safe I also did a, "autoclean" and "purge" then 

sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

Followed with a system reboot!

---

