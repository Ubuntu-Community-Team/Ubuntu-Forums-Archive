---
title: "Defaults Services enabled in 13.04"
date: 2013-04-15
forum: General Help
---

### Post by Marcelo Ramone on 2013-04-15
Hello,
 
After upgrade to ubuntu desktop 13.04 i have these services enabled (i reviewed with rcconf):
                                                                                                                                   &#9474;    
[*] acpi-support                                                                                                               
     &#9474;    
[*] brltty                       Braille terminal driver                                                                       
     &#9474;    
[*] grub-common                  Record successful boot for GRUB                                                               
     &#9474;    
[*] kerneloops                   Tool to automatically collect and submit kernel crash signatures                               
     &#9474;    
[*] ondemand                     Set the CPU Frequency Scaling governor to "ondemand"                                      
     &#9474;    
[*] pppd-dns                     Restore resolv.conf if the system crashed.                                                  
     &#9474;    
[*] rsync                        fast remote file copy program daemon                                                         
     &#9474;    
[*] sudo                         Provide limited super user privileges to specific users                                       
     &#9474;    
[*] x11-common   
     |     [ ] acpid                                                                                                                       
     &#9474;    [ ] alsa-restore                                                                                                              
     &#9474;    [ ] alsa-store                                                                                                                  
     &#9474;    [ ] anacron                                                                                                                  
     &#9474;    [ ] apparmor                     AppArmor initialization                                                                       
     &#9474;    [ ] apport                                                                                                                   
     &#9474;    [ ] avahi-cups-reload                                                                                                         
     &#9474;    [ ] avahi-daemon                                                                                                                
     &#9474;    [ ] bluetooth                                                                                                               
     &#9474;    [ ] console-font                                                                                                                
     &#9474;    [ ] console-setup                                                                                                          
     &#9474;    [ ] cron                                                                                                                    
     &#9474;    [ ] cups                                                                                                                     
     &#9474;    [ ] cups-browsed                                                                                                              
     &#9474;    [ ] dbus                                                                                                                     
     &#9474;    [ ] dmesg                                                                                                                 
     &#9474;    [ ] failsafe-x                                                                                                                 
     &#9474;    [ ] friendly-recovery    
     |     [ ] hostname                                                                                                                   
     &#9474;    [ ] hwclock                                                                                                                 
     &#9474;    [ ] hwclock-save                                                                                                                
     &#9474;    [ ] irqbalance                                                                                                             
     &#9474;    [ ] kmod                                                                                                                   
     &#9474;    [ ] lightdm                                                                                                               
     &#9474;    [ ] modemmanager                                                                                                          
     &#9474;    [ ] network-interface                                                                                                         
     &#9474;    [ ] network-interface-container                                                                                              
     &#9474;    [ ] network-interface-security                                                                                             
     &#9474;    [ ] network-manager                                                                                                           
     &#9474;    [ ] plymouth                                                                                                                 
     &#9474;    [ ] plymouth-log                                                                                                              
     &#9474;    [ ] plymouth-splash                                                                                                           
     &#9474;    [ ] plymouth-stop                                                                                                        
     &#9474;    [ ] plymouth-upstart-bridge                                                                                              
     &#9474;    [ ] procps                                                                                                                    
     &#9474;    [ ] pulseaudio                                                                                                             
     &#9474;    [ ] resolvconf                                                                                                          
     &#9474;    [ ] rfkill-restore                                                                                                           
     &#9474;    [ ] rfkill-store                                                                                                         
     &#9474;    [ ] rsyslog                                                                                                                    
     &#9474;    [ ] saned                        SANE network scanner server                                                                  
     &#9474;    [ ] setvtrgb       
           [ ] speech-dispatcher            Speech Dispatcher                                                                           
     &#9474;    [ ] udev                                                                                                                       
     &#9474;    [ ] udev-fallback-graphics                                                                                                  
     &#9474;    [ ] udev-finish                                                                                                                 
     &#9474;    [ ] udevmonitor                                                                                                                
     &#9474;    [ ] udevtrigger                                                                                                             
     &#9474;    [ ] ufw                                                                                                                         
     &#9474;    [ ] whoopsie              
 
My question is, Which services are enabled by default in Ubuntu 13.04?
Maybe some body can take a look in a fresh 13.04 install with rcconf utility (rcconf is not installed by default)
 
Thanks in advance.

---

