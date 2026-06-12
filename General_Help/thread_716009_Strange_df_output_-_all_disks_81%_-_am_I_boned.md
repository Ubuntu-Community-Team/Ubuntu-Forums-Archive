---
title: "Strange df output - all disks 81% - am I boned?"
date: 2008-03-05
forum: General Help
---

### Post by Vcount on 2008-03-05
I run Edgy 6.10.  I was trying to get USB working on my VirtualBox virtual machines, and following the tutorial at [www.arsgeek.com/?p=2776](www.arsgeek.com/?p=2776), created a usbuser and edited /etc/udev/rules.d/40-permissions.rules and uncommented the proc/bus/usb lines in /etc/init.d/mountdevsubfs.sh.  

It seemed to work, as I then had a "USB" option in the virtual machine settings.  However, whenever I restarted my computer, it totally lost everything.  It couldn't find my splash image on my GRUB screen, and then it would tell me that my volume didn't exist when I tried to boot.  Using Super Grub Disk, I still couldn't get in even using the "boot directly" option, as it would hang at "Target filesystem doesn't have /sbin/init".  

Figuring things were royally screwed, I booted up a liveCD, mounted my hard drive, and tried to reinstall udev and upgrade and update.  This did not fix the problem.  

I then ran df to see what my disks looked like.  I got this output:

root@ubuntu:/# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1            240362656 183698628  44454228  81% /
/sys                 240362656 183698628  44454228  81% /sys
varrun               240362656 183698628  44454228  81% /var/run
varlock              240362656 183698628  44454228  81% /var/lock
df: `/proc/bus/usb': No such file or directory
udev                 240362656 183698628  44454228  81% /dev
devshm               240362656 183698628  44454228  81% /dev/shm
devpts               240362656 183698628  44454228  81% /dev/pts
lrm                  240362656 183698628  44454228  81% /lib/modules/2.6.17-11-generic/volatile
/dev/sda2            240362656 183698628  44454228  81% /media/praxis
df: `/proc/fs/nfsd': No such file or directory
df: `/proc/sys/fs/binfmt_misc': No such file or directory
/dev/sdc1            240362656 183698628  44454228  81% /media/KINGSTON

You may notice that *every single disk* is at 81%.  There's no way this is true.  

This does not look good, and I can't find anything googling about all disks being 81%.  Am I royally screwed?  What can I do from here?

---

### Post by jeffus_il on 2008-03-05
> **Vcount said:**
> I run Edgy 6.10.  I was trying to get USB working on my VirtualBox virtual machines, and following the tutorial at [www.arsgeek.com/?p=2776]("http://www.arsgeek.com/?p=2776"), created a usbuser and edited /etc/udev/rules.d/40-permissions.rules and uncommented the proc/bus/usb lines in /etc/init.d/mountdevsubfs.sh.  

It seemed to work, as I then had a "USB" option in the virtual machine settings.  However, whenever I restarted my computer, it totally lost everything.  It couldn't find my splash image on my GRUB screen, and then it would tell me that my volume didn't exist when I tried to boot.  Using Super Grub Disk, I still couldn't get in even using the "boot directly" option, as it would hang at "Target filesystem doesn't have /sbin/init".  

Figuring things were royally screwed, I booted up a liveCD, mounted my hard drive, and tried to reinstall udev and upgrade and update.  This did not fix the problem.  

I then ran df to see what my disks looked like.  I got this output:

```
root@ubuntu:/# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1            240362656 183698628  44454228  81% /
/sys                 240362656 183698628  44454228  81% /sys
varrun               240362656 183698628  44454228  81% /var/run
varlock              240362656 183698628  44454228  81% /var/lock
df: `/proc/bus/usb': No such file or directory
udev                 240362656 183698628  44454228  81% /dev
devshm               240362656 183698628  44454228  81% /dev/shm
devpts               240362656 183698628  44454228  81% /dev/pts
lrm                  240362656 183698628  44454228  81% /lib/modules/2.6.17-11-generic/volatile
/dev/sda2            240362656 183698628  44454228  81% /media/praxis
df: `/proc/fs/nfsd': No such file or directory
df: `/proc/sys/fs/binfmt_misc': No such file or directory
/dev/sdc1            240362656 183698628  44454228  81% /media/KINGSTON

```You may notice that *every single disk* is at 81%.  There's no way this is true.  

This does not look good, and I can't find anything googling about all disks being 81%.  Am I royally screwed?  What can I do from here?

Make it a little more readable!
I would enter the lottery, 81 seems to be your lucky number, I have no idea how such a thing could happen.

---

### Post by Vcount on 2008-03-05
Thanks, I didn't know how to keep the spaces formatted, they were there when I pasted, but went away when I posted.  How did you do that?

---

### Post by pointone on 2008-03-05
Have you tried undoing the change to 40-permission.rules?

Encode terminal output in [ code ] [ /code ] tags, but without the spaces.

---

### Post by gerscht on 2008-03-05
> **Vcount said:**
> Thanks, I didn't know how to keep the spaces formatted, they were there when I pasted, but went away when I posted.  How did you do that?

Do a ```
df -h
``` to get it 'human readable'

---

### Post by jeffus_il on 2008-03-06
> **Vcount said:**
> Thanks, I didn't know how to keep the spaces formatted, they were there when I pasted, but went away when I posted.  How did you do that? 

Highlight the text then click on the "#" (code) button above the message editor, it's nice but unfortunately does not solve your problem, I was hoping that making it easily readable would attract a more capable helper.

---

### Post by Vcount on 2008-03-07
I still don't know what happened with that strange "df" output, but I got my computer working again.  

GRUB got messed up somehow after I made those changes, I'm not sure how, but it was pointing to the wrong hard disk for boot, and after manually pointing it to the right hard drive I was able to boot into my system again.  

Thanks for telling me how to post code, **jeffus** and **pointone**.

---

### Post by Oldsoldier2003 on 2008-03-07
> **pointone said:**
> Have you tried undoing the change to 40-permission.rules?

Encode terminal output in [ code ] [ /code ] tags, but without the spaces.

LOL I love it, command line tutorial for the forum "terminal" :) +1 for you!

---

