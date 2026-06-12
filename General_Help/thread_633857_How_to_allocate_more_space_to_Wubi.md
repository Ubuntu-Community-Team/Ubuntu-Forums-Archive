---
title: "How to allocate more space to Wubi?"
date: 2007-12-07
forum: General Help
---

### Post by Famicommander on 2007-12-07
When I first installed Feisty with Wubi, I only allocated a small amount of space, thinking I would get bored and go back to Windows.

As it turns out, I haven't booted Windows since I installed. I'm very much enjoying Ubuntu, but it seems that I'm quickly running out of the space I allocated.

Is there any way to allocate more space to Wubi without actually having to uninstall and then reinstall?

And help would be much appreciated.

---

### Post by Planets on 2007-12-07
Use LVPM.

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

### Post by mikedep333 on 2007-12-07
This is much appreciated as the wubi installer does not give you very many options for the size to install to.

---

### Post by TorontoStorm on 2007-12-07
i can get a message in wubi gutsy when i try lvpm. it says it must be a loopmounted partition, and it is cause i'm running it from inside wubi! anyone know a solution?

---

### Post by antimatter15 on 2007-12-09
> **TorontoStorm said:**
> i can get a message in wubi gutsy when i try lvpm. it says it must be a loopmounted partition, and it is cause i'm running it from inside wubi! anyone know a solution?

[https://bugs.launchpad.net/lvpm/+bug/165079](https://bugs.launchpad.net/lvpm/+bug/165079)

Here's an edited version (makes stuff more clear)

cd /host/ubuntu/disks
sudo dd if=/dev/zero of=extra.virtual.disk bs=1000 count=0 seek=$[1000*1000*10]
sudo mkfs.ext3 -F extra.virtual.disk

In this example, the file generated is 10 GB, change the numbers at the end of the command beginning with dd to adjust the sizes.

Now, once you have a virtual disk file, you mount it:

sudo mkdir /media/newhome
sudo mount -o loop extra.virtual.disk /media/newhome

Then you recursively copy the contents of /home to /media/newhome:

sudo rsync -avx /home/ /media/newhome

Now unmount the new virtual disk and remove the mountpoint:

sudo umount /media/newhome
sudo rm -r /media/newhome

Now reboot into Windows and move C:\ubuntui\disks\home.virtual.disk somewhere else and rename extra.virtual.disk to home.virtual.disk, then you should have a new /home with a larger size

---

### Post by mpince on 2007-12-10
> sudo dd if=/dev/zero of=extra.virtual.disk bs=1000 count=0 seek=$[1000*1000*10]

I created a virtual disk by substituting [COLOR="DimGray"]1000*4][/COLOR] for [COLOR="DimGray"]1000*10][/COLOR] in the above code. 

It worked, but the virtual disk only comes out to 3.7 GB

Is there a way to create a solid 4 GB, or better yet, a size that makes full use of an entire DVD-R (for backup)?

---

### Post by ago on 2007-12-11
bs=1GB count=4

---

### Post by TorontoStorm on 2007-12-11
to make a 50GB virtual disk do i do this line:
sudo dd if=/dev/zero of=extra.virtual.disk bs=1000 count=0 seek=$[1000*1000*50]

also, i assume that creates a larger home (/home) virtual drive.
what if i want a larger root drive? 

also, if i look in W:/ubuntu/disks there are three files with the following names: home.disk, root.disk, and swap.disk.
there is no home.virtual.disk

---

### Post by mpince on 2007-12-11
> **ago said:**
> bs=1GB count=4


Thanks ago!

Also, thank you for making wubi-- it has helped me use ubuntu in ways that I never would have with a Live CD. :)

---

### Post by mpince on 2007-12-11
> **TorontoStorm said:**
> 
also, if i look in W:/ubuntu/disks there are three files with the following names: home.disk, root.disk, and swap.disk.
there is no home.virtual.disk

home.disk is the one you want. I think home.virtual.disk is from previous versions. I just renamed mine to-- old.home.disk

---

### Post by TorontoStorm on 2007-12-11
> **mpince said:**
> home.disk is the one you want. I think home.virtual.disk is from previous versions. I just renamed mine to-- old.home.disk

thanks, but do you know how i can get a larger root drive?

---

### Post by ago on 2007-12-12
> **TorontoStorm said:**
> thanks, but do you know how i can get a larger root drive?

Always same process

1) Create a contiguous large file of the appropriate size inside of the windows folder (you can use dd for that) 
2) Format the FILE as ext3 and mount it
3) Copy over the files with rsync
4) replace root.disk with the new file.

---

### Post by mpince on 2007-12-12
> **ago said:**
> Always same process

3) Copy over the files with rsync


How do you prevent the home folder (and files contained in it) from being copied when using rsync? Wouldn't they be copied as well?

---

### Post by TorontoStorm on 2007-12-12
> **ago said:**
> Always same process

1) Create a contiguous large file of the appropriate size inside of the windows folder (you can use dd for that) 
2) Format the FILE as ext3 and mount it
3) Copy over the files with rsync
4) replace root.disk with the new file.

understand everything except step 3.
which files? all the ones in /
would this line work?:
sudo rsync -avx / /media/newhome

---

### Post by ago on 2007-12-13
> **mpince said:**
> How do you prevent the home folder (and files contained in it) from being copied when using rsync? Wouldn't they be copied as well?

```

sudo rsync -avx --exclude=/tmp/* --exclude=/home/* --exclude=/host/* --exclude=/proc/* --exclude=/mnt/*  /  /path/to/new.disk/mountpoint

```

---

### Post by TorontoStorm on 2007-12-17
thanks ago

---

### Post by mpince on 2007-12-17
Is it possible that future versions of wubi might let users choose the size of the home disk independently from the size of the root-- on install? Not that this process hasn't been a good learning experience. In addition to enlarging my home directory, I also created an extra storage disk and got it to mount on my desktop at startup.

---

### Post by ago on 2007-12-17
> **mpince said:**
> Is it possible that future versions of wubi might let users choose the size of the home disk independently from the size of the root-- on install? Not that this process hasn't been a good learning experience. In addition to enlarging my home directory, I also created an extra storage disk and got it to mount on my desktop at startup.

We'll have to decide whether we skip /home completely (unless on fat), so that the size goes against root/swap only and /home is simply a folder inside / as in standard installations .

---

### Post by mpince on 2007-12-18
> **ago said:**
> We'll have to decide whether we skip /home completely (unless on fat), so that the size goes against root/swap only and /home is simply a folder inside / as in standard installations .

If that means that if /home could expand and contract as necessary. That would definitely be the best option.

---

### Post by TorontoStorm on 2007-12-18
ago, definitely make /home a folder in root, make it easier for people to understand as well 'cause there's only 1 thing to resize

---

### Post by gsrkashyap on 2008-01-31
can the same procedure(home.virtual.disk) be done for system.virtual.disk also??

---

### Post by ago on 2008-01-31
yes, when copying the file over you will need to skip /proc /tmp /sys

---

