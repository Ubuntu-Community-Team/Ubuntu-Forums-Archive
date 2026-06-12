---
title: "mounting /home on an external usb drive"
date: 2007-04-09
forum: General Help
---

### Post by bradford72 on 2007-04-09
I don't know if this is the right forum for this question, but here's the situation:
My desktop system has a 10GB HDD inside of it, and I have connected a 200GB external USB HDD, which I am about to format ext3.  I would like to save the space on my internal drive for kernel updates and system files and mount my home directory and other accounts' home directories on the external drive.  Is it better to try to unmount /home and remount it on the usb drive, or just put a pointer to the external drive in /home?  What is the best way to do either, and which is preferrable?  I plan to switch to fiesty once it becomes stable.  How will this effect this situation?

---

### Post by mssever on 2007-04-10
> **bradford72 said:**
> My desktop system has a 10GB HDD inside of it, and I have connected a 200GB external USB HDD, which I am about to format ext3.  I would like to save the space on my internal drive for kernel updates and system files and mount my home directory and other accounts' home directories on the external drive.  Is it better to try to unmount /home and remount it on the usb drive, or just put a pointer to the external drive in /home?  What is the best way to do either, and which is preferrable?  I plan to switch to fiesty once it becomes stable.  How will this effect this situation?

Mounting your USB drive on /home is definitely the easiest option, and it's the option that I would likely choose if it were an internal drive. However, because the drive is removable, there's a possibility that you might need to use the machine at some time when the USB drive wasn't available. In such a case, I'm not exactly sure what would happen, but it probably wouldn't be pretty. Also, since USB is considerably slower, mounting it on /home might cause performance issues, depending on which programs you use. (Most programs store their settings--and sometimes their temp files--in your home directory in files or folders whose names begin with a dot.)

Probably the most robust solution would be to mount the drive somewhere other than /home and set up a system of symlinks to make acess to it convenient.

---

### Post by bradford72 on 2007-04-10
> **mssever said:**
> Mounting your USB drive on /home is definitely the easiest option, and it's the option that I would likely choose if it were an internal drive. However, because the drive is removable, there's a possibility that you might need to use the machine at some time when the USB drive wasn't available. In such a case, I'm not exactly sure what would happen, but it probably wouldn't be pretty. Also, since USB is considerably slower, mounting it on /home might cause performance issues, depending on which programs you use. (Most programs store their settings--and sometimes their temp files--in your home directory in files or folders whose names begin with a dot.)

Probably the most robust solution would be to mount the drive somewhere other than /home and set up a system of symlinks to make acess to it convenient.

Thanks very much!  I am a little bit confused now...could you give me an example of why I might need to use the machine without the USB drive available?  I am currently using my machine almost solely for learning linux, and just about never disconnect the USB drive.  I can understand the speed issues too, but have no real need for blazing fast program speeds at this point (the machine is almost a dinosaur anyway, so waiting a few seconds longer for programs to run is not such a big deal to me...I am dipping my toes into python, and assembly...I also like to keep some music in the box to listen to while I work)

I suppose the question then becomes how do I go about mounting the drive to /home?  If having the drive accessible or speed become a really big deal, it's no problem for me to start over with a fresh install.

Thanks again, this community rocks!

---

### Post by mssever on 2007-04-10
> **bradford72 said:**
> Thanks very much!  I am a little bit confused now...could you give me an example of why I might need to use the machine without the USB drive available?  I am currently using my machine almost solely for learning linux, and just about never disconnect the USB drive.If you don't anticipate running with the drive disconnected, then don't worry about it.
> I can understand the speed issues too, but have no real need for blazing fast program speeds at this point (the machine is almost a dinosaur anyway, so waiting a few seconds longer for programs to run is not such a big deal to me...I am dipping my toes into python, and assembly...I also like to keep some music in the box to listen to while I work)The biggest issue would probably be if you're using USB 1 or 2. For me at least, USB 1 (which is all my desktop supports) is quite painful. But, it's up to you, and mounting the frive on /home is certainly the simplest approach.
> I suppose the question then becomes how do I go about mounting the drive to /home?  If having the drive accessible or speed become a really big deal, it's no problem for me to start over with a fresh install.It's simply a matter of determining the permanant name for your partition(s) (like the UUID, LABEL, or something in /dev/disks/by-id) and editing your /etc/fstab. See [How to fstab]("http://ubuntuforums.org/showthread.php?t=283131") for an excellent tutorial. Also, if you find it necessary to change your layout later, there's no need to re-install. Simply copy the files over to your new /home using cp -a and edit your fstab.

---

