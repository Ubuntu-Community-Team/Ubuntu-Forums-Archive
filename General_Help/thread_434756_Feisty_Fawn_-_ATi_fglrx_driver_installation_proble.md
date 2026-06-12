---
title: "Feisty Fawn - ATi fglrx driver installation problem"
date: 2007-05-06
forum: General Help
---

### Post by AdHavoc on 2007-05-06
I have been following [this guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Disable_Composite_Extension) in order to install the ATi fglrx driver for my Feisty machine, but when I reach the step that says to build the kernel module (sudo module-assistant build fglrx --kernel-dir=/usr/src/linux-headers-2.6.17-10/), it outputs a few error messages.  [Note: I have to use the --kernel-dir command because if I do not, it shows this text error message, even though I *have* installed the headers:

 ```
Bad luck, the kernel headers for the target kernel version could     
not be found                                                         
and you did not specify other valid kernel headers to use.    

 If the running kernel has been shipped with the Debian              
distribution, please install the package                           
linux-headers-2.6.17-11-386. If your kernel source tree (or           
headers) is located in some non-usual location, please set the        
KERNELDIRS environment variable to the path of this directory, or     
(alternatively) specify the source directory we build for with       
the --kernel-dir option in module-assistant calls.
```       

Here is the build log file I get after using  $ sudo module-assistant build fglrx --kernel-dir=/usr/src/linux-headers-2.6.17-10/:

 ```
dh_testroot                                                                
 &#9474; rm -f configure-stamp                                                      
 &#9474; rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a                               
 &#9474; rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd                        
 &#9474; rm -rf .tmp_versions                                                       
 &#9474; rm -rf patch                                                               
 &#9474; dh_clean                                                                   
 &#9474; rm /usr/src/modules/fglrx/debian/control                                   
 &#9474; rm /usr/src/modules/fglrx/debian/dirs                                      
 &#9474; if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \           
 &#9474;         cat /usr/src/modules/fglrx/debian/control.template >               
 &#9474; /usr/src/modules/fglrx/debian/control; \                                   
 &#9474;         fi                                                                 
 &#9474; if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \                   
 &#9474;         mv /usr/src/modules/fglrx/debian/postinst 
 &#9474; /usr/src/modules/fglrx/debian/fglrx-kernel-2.6.17-10.postinst; \         
 &#9474;         fi                                                                 
 &#9474; dh_testdir                                                                 
 &#9474; touch configure-stamp                                                    
 &#9474; dh_testdir                                                                 
 &#9474; /usr/bin/make -C /usr/src/linux-headers-2.6.17-10/                         
 &#9474; SUBDIRS=/usr/src/modules/fglrx modules                                     
 &#9474; make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10'             
 &#9474;                                                                            
 &#9474;   WARNING: Symbol version dump                                             
 &#9474; /usr/src/linux-headers-2.6.17-10/Module.symvers                            
 &#9474;            is missing; modules will have no dependencies and modversions.  
 &#9474;                                                                            
 &#9474;   CC [M]  /usr/src/modules/fglrx/firegl_public.o                           
 &#9474; In file included from /usr/src/modules/fglrx/drm_proc.h:41,  
 &#9474;                  from /usr/src/modules/fglrx/firegl_public.c:357:          
 &#9474; /usr/src/modules/fglrx/drmP.h:126:1: warning: "DRM_DEBUG_CODE" redefined   
 &#9474; /usr/src/modules/fglrx/firegl_public.c:177:1: warning: this is the         
 &#9474; location of the previous definition                                        
 &#9474; /usr/src/modules/fglrx/firegl_public.c:475: warning: initialization from   
 &#9474; incompatible pointer type                                                  
 &#9474; /usr/src/modules/fglrx/firegl_public.c: In function &#8216;firegl_stub_open&#8217;:    
 &#9474; /usr/src/modules/fglrx/firegl_public.c:598: warning: assignment discards   
 &#9474; qualifiers from pointer target type                                        
 &#9474; /usr/src/modules/fglrx/firegl_public.c: In function &#8216;KAS_ExecuteAtLevel&#8217;:   
 &#9474; /usr/src/modules/fglrx/firegl_public.c:4789: warning: &#8216;flags&#8217; may be  
 &#9474;  used uninitialized in this function         
 &#9474;   LD [M]  /usr/src/modules/fglrx/fglrx.o                                   
 &#9474;   Building modules, stage 2.                                               
 &#9474;   MODPOST                                                                  
 &#9474; /bin/sh: scripts/mod/modpost: not found                                    
 &#9474; make[2]: *** [__modpost] Error 127                                         
 &#9474; make[1]: *** [modules] Error 2                                             
 &#9474; make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10'              
 &#9474; make: *** [build] Error 2                                                  
 &#9474; ^Y 
```                           

I'm very new to Linux, so if someone could give me a hand I'd be appreciative :)

---

### Post by rbmorse on 2007-05-06
Any reason you're not using the FGLRX package available in repository (and which installs fine)?  It's set to use the 2.6.20-15 kernel that ships with Fesity. 

Also available through add/remove programs...see "system" and then check "ATI binary  X.org driver"

---

### Post by AdHavoc on 2007-05-06
Well, you see, the problem with that is that the 2.6.20 kernel does not function correctly on my computer.  I had to upgrade from Dapper to Edgy to Feisty just to get Feisty to work, and even then, I have to use the 2.6.17 kernel, because on 2.6.20, it always freezes before it is fully booted.  The load bar will get to about 95% and then the caps lock light will flash on my keyboard and the system freezes.  Once, I got the system to boot up, but then it froze about 2 minutes into booting up.  This issue is what has caused so many other issues with compatibility etc.

---

