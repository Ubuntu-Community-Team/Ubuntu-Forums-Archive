---
title: "VMWare Workstation on Edgy 64 bit"
date: 2006-12-16
forum: General Help
---

### Post by sjstafford on 2006-12-16
Hope this is the correct topic to post this.

I have an Acer 5002WLMi. Just installed Edgy 64 bit, and have installed VMWare Workstation (latest version). All went well with the installation, at least I didn't see any errors during the installation. During configuration, I got this:

[INDENT]The following virtual networks have been defined:

. vmnet0 is bridged to eth0

Do you wish to make additional changes to the current virtual networks 
settings? (yes/no) [yes] no

Trying to find a suitable vmnet module for your running kernel.

The module bld-2.6.17-10-x86_64generic-Ubuntu6.10 loads perfectly in the 
running kernel.

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed

The configuration of VMware Workstation 5.5.3 build-34685 for Linux for this 
running kernel completed successfully.

You can now run VMware Workstation by invoking the following command: 
"/usr/bin/vmware".

Enjoy,

--the VMware team[/INDENT]

Notice that vmnet0 failed. VMWorkstation will not start and kicks out an error indicating that the app is not configured correctly.

Any ideas??

---

### Post by ture_atlantis on 2006-12-19
i got this same error, but i was using the 64bit version of ubuntu, i had to do a

sudo apt-get install ia32-libs

and it worked fine after that.  i got that clue from this web page.... 

[http://users.piuha.net/martti/comp/ubuntu/server.html#6](http://users.piuha.net/martti/comp/ubuntu/server.html#6)


hope that helps

---

