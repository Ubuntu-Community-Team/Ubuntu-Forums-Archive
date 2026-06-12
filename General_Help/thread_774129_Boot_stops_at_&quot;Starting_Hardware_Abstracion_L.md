---
title: "Boot stops at &quot;Starting Hardware Abstracion Layer Hald&quot;"
date: 2008-04-29
forum: General Help
---

### Post by quincasmetall on 2008-04-29
Hi,

I started to use Ubuntu about 2 years ago, and I still think that I'm a newbie. I love the system, the stability and the 3d graffic stuffs (such as Compiz). 

But yesterday I was trying to do a backup of whole sytem, including my user data, with Remastersys application. I'm using the 2.0.5 version, wich have GUI. After the whole process of image creation I've burned in DVD and put in my drive to see the Live Option. While booting there was not errors, but stops in the line:

*Starting Hardware Abstracion Hald

How can I fix this problem?


Ps: Sorry about my english. :(

---

### Post by quincasmetall on 2008-04-29
I have a suggestion about my problem here. In this afternoon I verified the free space of my partition, that contains about 2.3GB. So, the image that the Remastersys has created have the same size of my free space in system partition. But the question is: Before the creation of the backup process I changed the "Working Directory", in the program options, to a partition that haves 20GB free. Sufficient to create an image without problems.

The program still uses the partition system?

---

### Post by quincasmetall on 2008-04-30
Discard the previous post. I made my own distribution based on my system with Remastersys, without my user data and documents, and I receive the same problem that I've reported in the first post. 

Can anyone help me? I know, there is a lot of threads and questions of other users, but I need to fix that problem. 

Thanks.

---

### Post by warp99 on 2008-04-30
> **quincasmetall said:**
> Discard the previous post. I made my own distribution based on my system with Remastersys, without my user data and documents, and I receive the same problem that I've reported in the first post. 

Can anyone help me? I know, there is a lot of threads and questions of other users, but I need to fix that problem. 

Thanks.
If hal is trying to start twice then that could be the error. If you stop the service at boot you can troubleshoot the problem much easier, then re-enable the service or even start hal manually as a last resort. So first get to a console (crtl+alt+F2), login and issue the following:
```
sudo update-rc.d -f hal remove
```
that's going to clear out the hal symlinks on startup with any duplicates at the various runlevels, then issue the following:
```
sudo update-rc.d hal defaults
```
this will install the runlevel defaults for the hal service to start at boot. If that does not solve the problem then issue another 'sudo update-rc.d -f hal remove' to remove the service at boot, then try starting it manually after you boot to a login prompt:
```
sudo /etc/init.d/hal start
```
to see if that works.

---

### Post by quincasmetall on 2008-04-30
When the DVD was booting I've tried to do your steps. But I cant access the console. Appears a prompt, and when i type something, nothing happens.

---

### Post by warp99 on 2008-04-30
> **quincasmetall said:**
> When the DVD was booting I've tried to do your steps. But I cant access the console. Appears a prompt, and when i type something, nothing happens.

I know you want to save the DVD backup so here's how you can do this. You most likely have an ISO before you burned the DVD so you have a working copy to make the changes. You can mount the ISO just like a DVD then you can change root into the ISO just as if you booted into the DVD. Example:

Make a mount point for the ISO:
```
sudo mkdir /media/ISO
```
Mount the ISO as a regular drive:
```
sudo mount -t iso9660 -o loop file.iso /media/ISO
```
change root into the ISO:
```
sudo chroot /media/ISO
```
now you have the root directory inside of the ISO so all you need to do is run 'sudo update-rc.d -f hal remove' to turn off the service at boot. 

You can also do this as a virtual image if you have VMware player or server installed. Just change the /dev/<dvd> device to the file.iso location in the *.vmx file you generate using on online service like this:

[http://www.easyvmx.com/](http://www.easyvmx.com/)

or use VMware server, then you can repair the ISO within the virtual image. You could also use a combination of both if needed, change root into the ISO to turn off the hal services, then use VMware to troubleshoot the problem. Once you figured it out you can burn it back to a DVD.

---

### Post by quincasmetall on 2008-05-01
Dude, I've made all of your steps listed. But when i type this in terminal:

```
sudo chroot /media/ISO
```

I receive this in prompt: ```
chroot: cannot run command `/bin/bash': No such file or directory
```

---

### Post by chrisccoulson on 2008-05-01
Does /bin/bash actually exist on the ISO? (/media/ISO/bin/bash)

---

### Post by warp99 on 2008-05-01
> **chrisccoulson said:**
> Does /bin/bash actually exist on the ISO? (/media/ISO/bin/bash)
That's correct. If /bin/bash does not exist on the ISO you won't be able to run the commands. I did some checking on the Remastersys scripts from Linux Mint and the file system is compressed, so you won't be able to change root into the ISO. Your best chance of trying to repair the ISO is using VMware player or server.

---

### Post by quincasmetall on 2008-05-01
Thanks for your support, but the version that appears in my repositories doesn't work in my processor architecture. Its an i388.

---

### Post by Fate Reconciled on 2008-05-01
Wait, so you're using 64-bit version for an x86 processor?

---

### Post by quincasmetall on 2008-05-01
For which program u refers? The VMware version located in my available program list is the version of 64bits processors.

---

### Post by quincasmetall on 2008-05-11
I've actually give up about this "problem". I've looking for some solutions of this in a bunch of forums, including in my country (Brazil).

Thanks for all of your support and wasted time. 

Hugs.

---

