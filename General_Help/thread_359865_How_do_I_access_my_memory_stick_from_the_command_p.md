---
title: "How do I access my memory stick from the command prompt?"
date: 2007-02-12
forum: General Help
---

### Post by mrmonday on 2007-02-12
Hi Everyone,

:confused:I am currently having problems with my PC (see [here]("http://ubuntuforums.org/showthread.php?t=359702")) and I need access to my memory stick under a command prompt. Can anyone help? 

Thanks in advance.

---

### Post by newlinux on 2007-02-12
Assuming it automounted and you haven't setup a specific mount point for it, you can probably get to it from /media.

```
cd /media
ls
```


it' probably usbdisk or usbdisk2 or something like that. That's where mine automount to.

---

### Post by zvezdogled on 2007-02-12
you mean terminal.
the usb memory drives are usualy automaticly mounted in /media/ folder
so if you want to find it via terminal use comand
> 
cd /media/

and than 
> ls

---

### Post by MasterOfMuppets on 2007-02-12
First of all try making auto-mount:
udo mkdir /media/memory-stick
sudo mount *I don't know, I'm a newb*

To unmount:

sudo umount *The folder into which you mounted*.

---

### Post by newlinux on 2007-02-12
If it is not automounted there I can probably give you some more detailed instructions on explicitely mounting it.

---

### Post by mrmonday on 2007-02-12
Thanks everyone.

My memory stick doesn't appear to have auto-mounted. Could someone please give some detailed instructions for how to do this.

Thanks again.

---

### Post by Ramses de Norre on 2007-02-12
Take out the stick, run
```
sudo nohup gnome-volume-manager &
```
Plug the stick back in.

Hopefully it gets auto-mounted now.

PS: you can print all mounted filesystems with their mountpoints and such by simply invoking **mount**.

---

### Post by highneko on 2007-02-12
Can you paste the output of the following command? How much memory should it have?
cat /proc/partitions; df -h; ls /media/

---

### Post by newlinux on 2007-02-12
Assuming your memory stick is fat32 or NTFS

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)

You can list your partition table by doing:

```
fdisk -l
```

that should tell you what to replace /dev/hda1 with in the instructions.

---

### Post by mrmonday on 2007-02-12
> Take out the stick, run
Code:

sudo nohup gnome-volume-manager &

Plug the stick back in.

Hopefully it gets auto-mounted now.

PS: you can print all mounted filesystems with their mountpoints and such by simply invoking mount.

Unfortuently this didn't work:(
> Can you paste the output of the following command? How much memory should it have?
cat /proc/partitions; df -h; ls /media/
Will this give a long output, because I will have to write it down then type it.
> Assuming your memory stick is fat32 or NTFS

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)

You can list your partition table by doing:

Code:

fdisk -l

that should tell you what to replace /dev/hda1 with in the instructions.
It's a very old memory stick... it uses a FAT partitiona and has 64mb of memory... are there seperate commands for this?

---

### Post by highneko on 2007-02-12
Try and type the commands. Look for what you think the name should be.

---

### Post by newlinux on 2007-02-12
> **mrmonday said:**
> ...

It's a very old memory stick... it uses a FAT partitiona and has 64mb of memory... are there seperate commands for this?

the commands in the ubuntuguide should work, provided you properly identify your USB drive with fdisk -l, and follow the FAT instructions, not  the NTFS. I should have said as long as it is FAT,  not FAT32.

---

### Post by mrmonday on 2007-02-12
> Try and type the commands. Look for what you think the name should be.

This has quite a long output, what should I be looking for?

> the commands in the ubuntuguide should work, provided you properly identify your USB drive with fdisk -l, and follow the FAT instructions, not the NTFS. I should have said as long as it is FAT, not FAT32.

Again, what should I be looking for? This has a huge output, which flies off the screen.

---

### Post by newlinux on 2007-02-12
fdisk -l has a huge output? that doesn't seem right. how many partitions do you have? You should just be looking for something that is 64MB with device boot of /dev/something where something will be something like sdb1, sdc1, hda1, or something along those lines. But it is really hard for us to troubleshoot without seeing the output - if things are working right your drive should automount which means there are some problems...

Can you ssh into you machine from whatever machine you are using to send messages on this forum and then copy and paste the outputs?

---

### Post by mrmonday on 2007-02-12
I have my main windows partition, and the two linux made, swap and ext3?

I am using windows on the same PC as linux... however I could take photos of the screenand upload them if that helps...

I can't do this now though, because it is late however I will do it in the morning.

Thanks for your help.

---

### Post by mrmonday on 2007-02-13
OK.

When I plug my memory stick in, I get:
```
[17179628.000000] sdb: assuming drive cache: write through [17179628.016000] sdb: assuming drive cache: write through
``` 
Which leaves a blank line after, upon hitting enter you get back to the prompt.

when I run cat /proc/partitions; df -h; ls /media/ i get:
```

major    minor   #blocks          name

    8         0     80043264      sda
    8         1     31872928      sda1
    8         2     46178842      sda2
    8         3                1      sda3
    8         5      1983996       sda5
    8        16         64000      sdb
Filesystem                          Size   Used  Avail  Use%  Mounted on
/dev/sda2                           44G    1.9G  40G     5%   /
varrun                               506M    80K  506M   1%   /var/run
varlock                              506M       0  506M   0%   /var/lock
procbususb                          10M   120K  9.9M   2%   /proc/bus/usb
udev                                   10M   120K  9.9M   2%  /dev
devshm                              506M      0   506M   0%  /dev/shm
lrm                                    506M    18M  489M  4%  /lib/modules/2.6.17-10-generic/volatile
[COLOR="PaleGreen"]cdrom[/COLOR]  [COLOR="DeepSkyBlue"]cdrom0[/COLOR]  [COLOR="PaleGreen"]floppy[/COLOR]  [COLOR="DeepSkyBlue"]floppy0[/COLOR]

```

I am a slow typist, so I will not type the huge output(which I don't have all of, just the end).There is a picture here. If you can't see it go to: [http://lh4.google.com/image/robert.clipsham/RdH-mRG9OEI/AAAAAAAAABA/O3fV5jCms3k/fdisk-l.jpg?imgmax=512]("http://lh4.google.com/image/robert.clipsham/RdH-mRG9OEI/AAAAAAAAABA/O3fV5jCms3k/fdisk-l.jpg?imgmax=512")
[IMG]http://lh4.google.com/image/robert.clipsham/RdH-mRG9OEI/AAAAAAAAABA/O3fV5jCms3k/fdisk-l.jpg?imgmax=512[/IMG]

Thanks for your help.

---

### Post by charl.ie on 2007-02-13
what about:

  sudo mkdir /media/sdb1
  sudo mount /dev/sdb1 /media/sdb1

your memory stick should be mounted in /media/sdb1

---

### Post by public_void on 2007-02-13
> what about:

sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1

your memory stick should be mounted in /media/sdb1
Note: mount tries to auto detect the filesystem, if it fails (unlikely) then use the -t with the filesystem type ("man mount" has more information) e.g.
```
sudo mount -t vfat /dev/sdb1 /media/sdb1
```

---

### Post by mrmonday on 2007-02-13
Thanks everyone, I have managed to mount it using:
```
sudo mkdir /media/sdb1
sudo mount /dev/sdb /media/sdb1
```

However now I have another problem... If you read the thread I linked to at the very start of this one, you know about my problems. I need to know how to install programs from the terminal I tried:
```
sudo apt-get install envy_0.8.1-0ubuntu6_all.deb
```
Which gave an error stating something like it can't find the package, however using the ls command the file is there... can any of you help?

---

### Post by charl.ie on 2007-02-13
I don't think apt-get works if you put the .deb extension. Try:

sudo apt-get install envy_0.8.1-0ubuntu6_all

---

### Post by mrmonday on 2007-02-13
Nope... this doesn't work either... but heres the error message:

E: Couldn't find package envy_0.8.1-0ubuntu6_all

This time I couldn't use the ls command to view the files, to check I had it right.

Oops, I just realised I forgot to mount it... I'll try again.

---

### Post by mrmonday on 2007-02-13
Nope, didn't work... any other ideas? thanks.

---

### Post by newlinux on 2007-02-13
If you are installing a local .deb you should use dpkg

```
sudo dpkg -i envy_0.8.1-0ubuntu6_all.deb
```

this code assumes you working directory contains that .deb file.

---

### Post by charl.ie on 2007-02-13
i think apt-get is trying to get the package from the internet, so if it's on your memory stick then it won't find it :(

try dpkg -i package envy_0.8.1-0ubuntu6_all.deb

---

### Post by mrmonday on 2007-02-13
OK.

Now I am truely stuck. I ran envy, which couldn't get the nvidia drivers from the internet. So I ran the nvidia drivers, using the instructions on the site, now I get an error message when I boot, and no terminal prompt, I can get one starting in recovery mode... Any ideas?

Thanks.

---

