---
title: "Kubuntu Hardy slow at booting up"
date: 2008-05-05
forum: General Help
---

### Post by TWO on 2008-05-05
Does anyone else find that Kubuntu Hardy Heron is slower than Gutsy when it comes to booting up? 

I also find that it's slower than my Windows XP at booting.

I'm not obsessive about start up times or anything like that but it's just a bit inconvenient say if I want to nip on and check some e-mails. 

(I suppose some might say just boot into Windows XP then but that's besides the point. I would like Kubuntu to boot up just as quickly.)

TWO

---

### Post by p_quarles on 2008-05-05
How long are we talking, here? If it's in the 25 - 50 second range, it's normal. A lot more than that and there may be something wrong with a module, etc.

To get small boosts in bootup speed, there are a few things you can do, including disabling unneeded startup services. E.g., if you don't use any Bluetooth devices, you can turn off that service.

---

### Post by TWO on 2008-05-05
> **p_quarles said:**
> How long are we talking, here? If it's in the 25 - 50 second range, it's normal. A lot more than that and there may be something wrong with a module, etc.

To get small boosts in bootup speed, there are a few things you can do, including disabling unneeded startup services. E.g., if you don't use any Bluetooth devices, you can turn off that service.

It took just over a minute so maybe it's not as bad as I thought? 

The thing is that I know that Kubuntu Gutsy was slightly quicker and my previous installs of Ubuntu were quicker still. I just checked, and my Windows XP boots in like 20 seconds from the GRUB menu. 

Kubuntu is more light-weight than XP is it not, so what could be slowing it down so much? I think I've already disabled Bluetooth, but I'm pretty sure that new things have popped up since the distro upgrade so I'm not sure what else I can disable.

---

### Post by p_quarles on 2008-05-05
> **TWO said:**
> It took just over a minute so maybe it's not as bad as I thought? 
Just means that nothing is seriously wrong, not that you can't get things working better.

> Kubuntu is more light-weight than XP is it not, so what could be slowing it down so much? I think I've already disabled Bluetooth, but I'm pretty sure that new things have popped up since the distro upgrade so I'm not sure what else I can disable.
Remember, XP was released 7 years ago. While Ubuntu is certainly lighter than the proprietary OSes released last year (Windows Vista and OS X Leopard), it is prone to taking up more resources than XP. Of course, this depends entirely on the configuration, and it's relatively easy to get Ubuntu or any Linux to be extremely light on resources.

There are several graphical front-ends for controlling startup services, but it's been a while since I've used them, so I can only give you the old fashioned way:
```
ls /etc/rc2.d/ 
```
The contents of this directory will show you what gets initiated during the boot process. If you want to paste the output here, I can tell you how to disable some of the commonly unneeded services.

---

### Post by retrow on 2008-05-05
Another small change which might cut a few seconds would be by disabling fsck of NTFS partitions in /etc/fstab.

---

### Post by TWO on 2008-05-06
Here is the output of ls /etc/rc2.d/

> 
README                                           
S01policykit                                         
S05vbesave                                            
S10acpid                                            
S10powernowd.early                            
S10sysklogd                                   
S10xserver-xorg-input-wacom                        
S11klogd                                     
S12dbus                                          
S13kdm                                               
S17mysql-ndb-mgm                                    
S18avahi-daemon              
S18mysql-ndb
S19mysql
S20apmd
S20apport
S20hotkey-setup
S20kde-guidance
S20makedev
S20nvidia-kernel
S20powernowd
S20rsync
S24dhcdbd
S24hal
S50cupsys
S50guarddog
S89anacron
S89atd
S89cron
S98usplash
S99acpi-support
S99laptop-mode
S99rc.local
S99rmnologin
S99stop-readahead


> Another small change which might cut a few seconds would be by disabling fsck of NTFS partitions in /etc/fstab.

That sounds interesting. How essential is the fsck of NTFS partitions?

---

### Post by p_quarles on 2008-05-06
> **TWO said:**
> Here is the output of ls /etc/rc2.d/
A few things to consider here. cupsys is only necessary if you are operating a printer with this machine. wacom support is only needed for, umm, wacom tablets. The nvidia-kernel service ships with Ubuntu, but is obviously not needed unless you are actually using an nVidia graphics card. You don't need both ACPI and APM (newer laptops are almost all ACPI) support. I can't remember exactly what apport does, but at some point I determined that I didn't need it, and disabled it. You can also disable the bootsplash screen if you don't care about that part. 

> That sounds interesting. How essential is the fsck of NTFS partitions?
It's not. 

> EDIT: I added in the '#' to split up the sections.
Better is to use the [noparse]```
...
```[/noparse] tags. That will leave the spaces in formatted text such as that output.

---

### Post by TWO on 2008-05-06
> **p_quarles said:**
> It's not.

Is it worth being disabled anyway? 

> 
Better is to use the [noparse]```
...
```[/noparse] tags. That will leave the spaces in formatted text such as that output.
 
Thanks for that, I'll use that in future. 

I'll give your suggestions a try and see what happens.

TWO

Edit: If I disable cupsys, when I come to need a printer which I infrequently do, will it detect it as normal?

---

### Post by p_quarles on 2008-05-06
> **TWO said:**
> Is it worth being disabled anyway? 
It won't speed up normal boots, but it will get rid of the interval checks that fsck performs on that partition. So, yes. 

> Edit: If I disable cupsys, when I come to need a printer which I infrequently do, will it detect it as normal?
Yeah, disabling it as a bootup service does not remove it from the system. Most installed services still have a run script in /etc/init.d. You can start cupsys by typing:
```
sudp /etc/init.d/cupsys start
```
I do this with several services I use only occasionally.

---

### Post by TWO on 2008-05-06
OK. I've just disabled some of the one's you've suggested but I can' find anything related to the nvidia-kernel or to the NTFS fsck in the System Services menu. Is there an alternate way to look at start-up services and disable them?

---

### Post by p_quarles on 2008-05-06
> **TWO said:**
> OK. I've just disabled some of the one's you've suggested but I can' find anything related to the nvidia-kernel or to the NTFS fsck in the System Services menu. Is there an alternate way to look at start-up services and disable them?
Yes. To turn off fsck on the ntfs partition, edit the fstab file:
```
gksu gedit /etc/fstab
```
Find the row for the ntfs partition, and change the last item/column to "0" (zero).

To turn off other services, you have a couple options. One is a semi-graphical (ncurses) program:
```
sudo apt-get install sysv-rc-conf
```
And then run it:
```
sudo sysv-rc-conf
```
You can turn off services by unchecking the boxes the in [2] column.

The other way is to change the name of the startup shortcuts. The "files" in /etc/rc2.d/ are actually symbolic links (i.e., shortcuts) to other files, and the way they are run is determined by the name. The key is like so:
```
D     Disable
S    Start
K    Kill
```
The numbers following indicate the priority of the script, with 01 being the highest and 99 being the lowest priority. The easiest way to disable a service you don't want is to open up a root file manager:
```
gksu nautilus
```
navigate to /etc/rc2.d/, and replace the "S" in the relevant link with a "D." For instance, to disable CUPS, you would change
```
/etc/rc2.d/S50cupsys
```
to
```
/etc/rc2.d/D50cupsys
```
Deleting the link would also disable the service, but I recommend against that, since you may change your mind at some point.

---

### Post by TWO on 2008-05-06
OK. Tried to install that program but it proved a bit too hard to navigate for me. Just kept bringing up gibberish if I tried to move either with my mouse or the keyboard. I've disabled the NTFS fsck at least so I'll reboot now and see what difference this makes.

---

### Post by TWO on 2008-05-06
Well, the difference seems to be like 10 or so seconds quicker but it is very inconsistent! On one reboot attempt, it did so in 40 seconds which was much better, but the next time it went back to being slow. It's pretty odd!

---

### Post by inportb on 2008-05-06
You can also try profiling the boot process to speed up future boots.

---

### Post by TWO on 2008-05-07
> **inportb said:**
> You can also try profiling the boot process to speed up future boots.

Firstly, what is 'profiling' and how would I go about doing that?

Thanks

TWO

---

### Post by p_quarles on 2008-05-07
> **TWO said:**
> Firstly, what is 'profiling' and how would I go about doing that?

Thanks

TWO
Profiling your bootup is accomplished by entering the GRUB command line from the menu, and adding "profile" to the kernel command, at the very end. 

Again, changing the fsck priority of an NTFS partition will not speed up your normal boot times -- it will just prevent the slow downs occasionally caused by the fscks (filesystem checks -- they occur every ~20-30 boots, and take a while). 

If you didn't care for the sysv-rc-conf program, I'd recommend giving the other alternative (gksu nautilus /etc/rc2.d/ ) a try. That will have a definite positive (but not necessarily dramatic) impact on your boot time.

EDIT: A couple of links that may help:
[http://darkox-weblog.blogspot.com/2007/10/improve-ubuntu-boot-time-and.html](http://darkox-weblog.blogspot.com/2007/10/improve-ubuntu-boot-time-and.html)
[http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)

---

### Post by AldenIsZen on 2008-05-09
Thanks p_quarles, I will check out that second link later.

 I haven't tried this, but you can check this out, I plan to later:

[Speed up boot process, the way you can feel it!]("http://ubuntuforums.org/showthread.php?t=89491&highlight=slow+windows+boot")

 I have an issue with XP booting up slow, but I was useing the SuperGrub disk. I think I may have reinstalled it wrong, and now windows is taking quite a bit longer. From 3-4 seconds to 20-30 just to pull up the loading bar.. .. ..

---

