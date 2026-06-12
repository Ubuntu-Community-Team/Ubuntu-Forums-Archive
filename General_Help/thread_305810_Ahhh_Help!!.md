---
title: "Ahhh Help!!"
date: 2006-11-23
forum: General Help
---

### Post by tankertuff on 2006-11-23
OK, I made a goof. I installed windows after multiple attempts to get Reason 3.0 to work via vmware and wine to no avail. My problem is I installed windows on a striped IDE raid with a couple hard drives laying around. Well, I could get windows to boot fine by selecting to boot from Nvidia raid in startup options (ESC during POST sequence), and Ubuntu by selecting my SATA drive. Well, I musta fiddled with the wrong settings because grub can't find either drive. I'm fine with editing my config files if I have to , really , I think I have to totally rebuild grub. I wouldn't mind installing windows again, but Ubuntu is my main operating system so that's not an option, can anyone please help!!  :oops: 

here's a layout of my drives/partitions.

/dev/sda1 - swap
/dev/sda3 - /

/dev/mapper/nvidia_fdebicde1 - Windows (this is the proper labeling for a                                        
                                          nvidia raid from what I've read)

I have tried multiple configurations of the device map, and I think I may have goofed and removed the windows MBR ](*,) , that's ok, I can deal with that later, I just want my Ubuntu back. Again, thanks ahead of time, and happy thanksgiving.

---

### Post by bollix47 on 2006-11-24
Maybe [_this page_]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") will help.

---

