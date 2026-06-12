---
title: "Recovering Windows files with Ubuntu LiveCD"
date: 2012-11-18
forum: General Help
---

### Post by adamfangman on 2012-11-18
I was getting error messages when trying to boot Windows 7 - first "disk read error" and now "Operating system not found." So Windows 7 is gone.

I have a Ubuntu LiveCD so I'm going to recover my files from the hard drive, put them on my external hard drive, and then install Ubuntu. But I'm not sure how to accomplish this. When I boot the LiveCD, under "Places" all I see is File System for my hard drive. It shows this:

[http://img690.imageshack.us/img690/2765/screenshotat20121118194.png](http://img690.imageshack.us/img690/2765/screenshotat20121118194.png)

When I try to open the root folder, where I believe all my files are, I get this:

[http://img703.imageshack.us/img703/2765/screenshotat20121118194.png](http://img703.imageshack.us/img703/2765/screenshotat20121118194.png)

I guess I can't directly gain access to my files because Windows 7 isn't around anymore. How can I fix this and get access to my hard drive to back it up?

---

### Post by The Cog on 2012-11-18
That looks disappointing - "File System" is the virtual in-memory file system that the live CD creates for itself. There is no sign of you hard disk there. I would expect to see it listed on the left hand panel as something like "250G Disk.

Can you open a command prompt and enter the command
```
sudo fdisk -l
```which should list all the hard disk it can see. I am hoping it will list a /dev/sda with some partitions on it". 

Or gparted should also be able to show you all your hard drives - gparted should be there in the GUI somewhere, but I'm not sure how you would find it.

---

### Post by adamfangman on 2012-11-18
Gparted isn't showing any devices.

I'm not seeing anything when I enter that command. Do I enter that all those commands at the same time?

---

### Post by adamfangman on 2012-11-18
My hard drive is also making a persistent "chirping" noise inside my computer when it's on. It did that the last time my hard drive died (I had to replace it once already with this laptop). I've got some pretty vital files on here, what can I do if the hard drive is corrupted?

---

### Post by apmcd47 on 2012-11-18
OK Ignore this post. From those other posts it looks like you have a dead drive

===================

I think you were looking at the virtual file system of your live CD there. Try opening a terminal window and type:```

cd /tmp
mkdir mnt
mount /dev/sda1 /tmp/mnt


```
You should now be able to see the Windows file system under /tmp/mnt.

If you have a spare computer I would advise downloading and burning the parted magic CD. I think that one loads entirely into RAM allowing you to burn the data to a CD or DVD.

Andrew

---

### Post by adamfangman on 2012-11-18
> **apmcd47 said:**
> OK Ignore this post. From those other posts it looks like you have a dead drive

===================

I think you were looking at the virtual file system of your live CD there. Try opening a terminal window and type:```

cd /tmp
mkdir mnt
mount /dev/sda1 /tmp/mnt


```You should now be able to see the Windows file system under /tmp/mnt.

If you have a spare computer I would advise downloading and burning the parted magic CD. I think that one loads entirely into RAM allowing you to burn the data to a CD or DVD.

Andrew

mount: only root can do that

is what I get.

---

### Post by The Cog on 2012-11-18
> I'm not seeing anything when I enter that command. Do I enter that all those commands at the same time?Yes, it is a one-line command. **Sudo** effectively means "run as administrator", **fdisk** is a disk formatting utility, and **-l** tells it to just list all the drives it can find.

Sorry, but I think at this stage you probably need the services of a data recovery company.

---

### Post by adamfangman on 2012-11-18
> **The Cog said:**
> Yes, it is a one-line command. **Sudo** effectively means "run as administrator", **fdisk** is a disk formatting utility, and **-l** tells it to just list all the drives it can find.

Sorry, but I think at this stage you probably need the services of a data recovery company.

That's how it's lookin to me too. Gonna install ubuntu on an old iPod hard drive and see if the professionals can get stuff off my drive.

---

### Post by Mark Phelps on 2012-11-19
In my own experience, Windows data recovery utilities are best at recovering Windows partitions; Linux utilities, at recovering Linux partitions.

If you want to try something else, connect your drive to a Windows PC, download and install the TRIAL version of RecoverMyFiles (from Runtime Software), run it in the deepest discover mode (will take HOURS) -- and see what it finds.

If it finds what you want to recovery, purchasing a license online is a LOT cheaper than paying for professional data recovery services.

---

