---
title: "Hard drive full?"
date: 2014-12-07
forum: General Help
---

### Post by trotter-danny on 2014-12-07
I currently am using a ASUS Laptop with a 250 gig hard drive in it.  I formatted my latest install to give the whole hard drive to Ubuntu, so I do not have any other OS's on the computer.  I have really only installed a few programs ( Chrome/Filezilla/Pidgin/Gimp/VLC/Shutter/Spotify/ a couple remote desktop things for my wife's work) and that is about it.  We really do not use this computer to download massive files or store photos/music/videos.  So I'm trying to figure out where all of my space went.  I went to do a normal system update and it told me that I do not have sufficient amount of space left on my drive, which according to Ubuntu is about 232 gigs.  Where did it go?  Like I said, we don't download anything crazy on this computer its mainly remote desktop things or just internet browsing.  Any ideas??

Thanks!

---

### Post by matt_symes on 2014-12-07
Hi

Open a terminal and type these commands

```
df -h
df -i

```

Post the results back here

Kind regards

---

### Post by trotter-danny on 2014-12-07
Here is the output
[IMG]http://i.imgur.com/RS9hZhN.png[/IMG]

Thank you for helping me look into this! :)

---

### Post by nerdtron on 2014-12-07
/boot partition is full possibly because of older kernels are not cleaned up. 
See here: [http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu)

---

### Post by trotter-danny on 2014-12-07
Thanks for the tip.  I followed the instructions on the page and it cleared up some space on the /boot, but didn't do much for the problem I am having.
[IMG]http://i.imgur.com/BbEWkTN.png[/IMG]

---

### Post by matt_symes on 2014-12-08
Hi

@trotter-danny. 

You removed the output from the commands i asked you to post ? They are not there now.

If you did do that and if you keep doing that then it is going to be very hard indeed to help you. I currently have no idea how your system is partitioned as i was asleep when you posted. Timezones and all that.

If you're worried about any sensitive information then redact your output but please don't remove it.

Bear in mind that if we solve your problem then it may help others in the future that have a similar problem. These are public forums for that reason.

Kind regards

---

### Post by Impavidus on 2014-12-08
You now only use 45MiB on your /boot partition of 243MiB. It is no longer full, so your problem has been solved.

Don't be fooled by the full /dev/sda5 partition. You use LVM partitioning, which is why you have a /boot partition in the first place. LVM is a partitioning layer on top of the normal partitioning. /dev/sda5 will always appear full.

---

### Post by trotter-danny on 2014-12-08
Sorry about that.  I originally just copy/pasted the output from the terminal, but the formatting was all messed up.  I just screen shotted the window and posted it.  Here's the output in text form.

dtrot@Ubuntu-Lappy:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  225G  6.8G  207G   4% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         2.0G  4.0K  2.0G   1% /dev
tmpfs                        404M  1.3M  403M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         2.0G   17M  2.0G   1% /run/shm
none                         100M   44K  100M   1% /run/user
/dev/sda1                    236M   38M  186M  17% /boot
dtrot@Ubuntu-Lappy:~$ df -i
Filesystem                    Inodes  IUsed    IFree IUse% Mounted on
/dev/mapper/ubuntu--vg-root 14991360 213835 14777525    2% /
none                          212448      2   212446    1% /sys/fs/cgroup
udev                          207457    499   206958    1% /dev
tmpfs                         212448    532   211916    1% /run
none                          212448      4   212444    1% /run/lock
none                          212448     77   212371    1% /run/shm
none                          212448     27   212421    1% /run/user
/dev/sda1                      62248    302    61946    1% /boot
dtrot@Ubuntu-Lappy:~$ 


Here is a window screenshot incase the formatting is horrible in text form
[IMG]http://i.imgur.com/MJemfWy.png[/IMG]

I didn't really do too much with the partitioning, I just gave the whole hard drive to Ubuntu when I installed and it did the rest
[IMG]http://i.imgur.com/BbEWkTN.png[/IMG]

---

### Post by nerdtron on 2014-12-08
As stated by matt_symes and impadivus, there's an improvement on your disk usage.
From the latest terminal screenshot, Disk usage is very low now. With regards to the Gparted screenshot showing 100% usage that is because of the LVM partition. You don't have to worry about that because that's the way it is.

---

### Post by matt_symes on 2014-12-09
Hi

> **nerdtron said:**
> As stated by matt_symes and impadivus, there's an improvement on your disk usage.
From the latest terminal screenshot, Disk usage is very low now. With regards to the Gparted screenshot showing 100% usage that is because of the LVM partition. You don't have to worry about that because that's the way it is.

I agree with this. It looks like you have plenty of space available.

You you still getting issues with the disk saying it's full ?

Kind regards

---

### Post by leunam12 on 2014-12-09
Check the Disk Usage Analyzer, it will tell you what's taking up disk space.

---

