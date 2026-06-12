---
title: "login surprise......."
date: 2007-10-11
forum: General Help
---

### Post by cvcuse on 2007-10-11
"GDM could not write to your authorization file. This common out of disk space home directory could not be opened for writing. Not possible to log in. Please contact system administrator."

This was message after reboot. Had just installed new driver for wireless  which was successful and able to setup wifi network for 1st time.

Thanks

---

### Post by taurus on 2007-10-11
Boot into recovery mode from GRUB menu and post the output of this command.  Need to see if you still have some space left on your machine.

```
df -h
```

---

### Post by cvcuse on 2007-10-11
thanks for reply


/dev/sda7                      size 2.1g       used 2.0            avail 0        use% 100
varrun                                                                                                            
varlock                                                                                                            
procbususb                                                                                                     
udev                                                                                                               
devshm                                                                                                           
lrm                                                                                                                  
the bottom six are all 760m size and % used 1,0,1,1,0,5 
thanks again......

---

### Post by taurus on 2007-10-11
> **cvcuse said:**
> thanks for reply


**[COLOR="Blue"]/dev/sda7                      size 2.1g       used 2.0            avail 0        use% 100[/COLOR]**
varrun                                                                                                            
varlock                                                                                                            
procbususb                                                                                                     
udev                                                                                                               
devshm                                                                                                           
lrm                                                                                                                  
the bottom six are all 760m size and % used 1,0,1,1,0,5 
thanks again......

There's your problem.  You have maxed out your 2.1GB of space!  If you are using Gnome, you need at least 2.5GB and if you plan to install more stuff later, you need more space.  So, you can get some space with

```
apt-get clean
df -h
```

---

### Post by cvcuse on 2007-10-11
Thanks again. Got back in and deleted items I had placed on desktop from usb drive. They included nvidia driver, 'envy' to install , and others, etc. All were for purpose of getting 'nic' ,wifi, and video (resolution 640x480) changed. Now that I'm using wifi have 122 updates available so began downloading and almost immediately got message that disk space zero. Stopped download and realized same ol' same ol' unless I enlarge  dev/sda7 as you suggested.  Will say that before the downloads I did  install gnome partition editor to get picture of hard drive and hopefully it might be of use to resize what needs to be done. All advice  appreciated.

---

### Post by om1 on 2007-10-11
your Ubuntu live CD has gnome partition editor on it.... plus you will need to have the HDD unmounted anyway so a live CD of some sort will be required

---

