---
title: "[SOLVED] Terminal/Synaptic thinks I still have my new kernel"
date: 2008-07-05
forum: General Help
---

### Post by L337_K3y5 on 2008-07-05
How in the world do I get terminal and synaptic package manager to stop thinking the new kernel I installed (btw didn't work) so I "uninstalled" it, or more like deleted and purged the files, and updated grub and what-not.  Now, whenever I open it in root, it tries to go to the old directory, which is where I went, and it isn't there, like stated. Attached is the pic I have of the terminals insanity.](*,)

---

### Post by drs305 on 2008-07-05
Edit: nevermind, I see you ran the command from the root prompt.

---

### Post by L337_K3y5 on 2008-07-05
It started happening after I install Konqueror through the package manager.  I was doing it to try to see if something worked if I used that browser instead.  I now have more of a reason to hate that browser....EDIT - Also, I may not have removed the sym link from the linux folder...how do I remove a sym link from a new kernel?

---

### Post by L337_K3y5 on 2008-07-05
Also, this stupid bug has caused a butt-load of trouble; I can't add-remove, update, or use the synaptic things.  Uhhh....](*,)

---

### Post by drs305 on 2008-07-05
When my synaptic seems to get messed up, I take a look at /var/lib/dpkg/status and compare the date/time with the status-old file. If they are fairly close and I've just recently messed things up, I'll rename the 'status' file and then change 'status-old' to 'status' to see if that fixes things. 

Note: you can't delete the 'status' file outright or apt complains...

---

### Post by L337_K3y5 on 2008-07-05
Nope, didn't work, but I have a hunch that it has to do with a system link of the new kernel still in the system, when it shouldn't be....can't believe installing one thing made it go crazy, stupid Konqueror .:mad:  EDIT - Found the files that were supposed to be deleted.  How do I remove the kernel now?  Can I just use ```
dpkg -P
``` to remove all the files left by the old kernel?  I have a pic showing them.

---

### Post by unutbu on 2008-07-05
Perhaps download the .deb file for the linux kernel, install it with

```
sudo dpkg -i --force-all [linux-kernel-package].deb
```

Then uninstall it the proper way with

```
sudo apt-get purge [linux-kernel-package]
```

The apt system seems to gag whenever it can't find files that it assumes should be there. If there are just a few files missing, you can just put dummy files there for `apt-get purge` to chew on, but if there are a lot of files missing, I think the easiest way to recover is to use a .deb to repopulate the filesystem for you.

Note that if you manually removed files from more than one package, like linux-image-* and linux-headers-*, then you'll need to install both .debs. In that case, I would download all the required debs, put them in an empty folder, and run

```

sudo dpkg -i *.deb

```

As always, please correct me if I'm wrong, drs305.

---

### Post by L337_K3y5 on 2008-07-05
> **unutbu said:**
> Perhaps download the .deb file for the linux kernel, install it with

```
sudo dpkg -i --force-all [linux-kernel-package].deb
```

Then uninstall it the proper way with

```
sudo apt-get purge [linux-kernel-package]
```

Lol, funny thing is, I can't do that, considering that my problem is still not solved, I still get the error to use the "dpkg --configure -a" to resolve the problem, doesn't work to resolve. EDIT - Wait, hold the phone, let me try yours again.

---

### Post by L337_K3y5 on 2008-07-05
Umm....don't know what the |-|311 I did, but I think I got it working...hmmm...thanks!:)  I think my things that weren't working had an addiction to my packages, and went to long without them, thus causing a withdrawal, and resulting temper-tantrum.

---

### Post by L337_K3y5 on 2008-07-05
Ummm.....sorry to bother again, but when I forgot to uninstall it first, I went to the grub list and made it show all kernels installed, I forgot that I had start-up manager setting it to show only one, then when it restarted, it showed the new kernel that doesn't work.  How can I get it to show all kernels from the Grub, without being able to boot into another?  Can I use the live-cd to fix this at all?

---

### Post by drs305 on 2008-07-05
> **L337_K3y5 said:**
> Ummm.....sorry to bother again, but when I forgot to uninstall it first, I went to the grub list and made it show all kernels installed, I forgot that I had start-up manager setting it to show only one, then when it restarted, it showed the new kernel that doesn't work.  How can I get it to show all kernels from the Grub, without being able to boot into another?  Can I use the live-cd to fix this at all?


I'm not sure I completely understand your situation, but I think you are saying you can't find a bootable kernel in grub. In this case, as grub starts hit the ESC key and it will enter the edit mode. Highlight the kernel, hit E, tab to the kernel again, hit E, and just change the kernel *number* and leave everything else the same. If my instructions don't make sense just read the instructions at the bottom of the screen once you get into the edit mode.

---

### Post by L337_K3y5 on 2008-07-05
K, I get to that part, but I need a how-to or something, I have the one on Ubuntu that is 2.6.24.19 I think, I I don't know which to edit over to do, and I think mine had a dash in it...I'm lost...is there a way throught the command line?

---

### Post by drs305 on 2008-07-05
The previous kernel on my 32-bit machine was 2.6.24-18-generic but your's definitely could have been different.

You can boot to the livecd, _mount your linux partition_, and do a search to find the kernels available (they are in /*mountpoint*/boot and called vmlinuz-xxxxxxxx). You need to know the partition your linux install is on to mount it of course (try sda1 on a non-dual boot machine if you don't have any idea).

```

sudo mkdir /temp
sudo mount /dev/sdXX /temp

```

At this point, you can open nautilus and look inside the 'temp' folder. That is your linux partition. You can see what kernels you have by looking in the temp/boot folder. The available kernel numbers you are familiar with are preceeded by "vmlinuz-".

If you want command line:
```

sudo find /temp/boot -iname vmlinuz*

```

From here, you can see which are installed. You could also open and edit your menu.list (/temp/boot/grub/menu.lst). Remember though that when you install or delete kernels via synaptic, grub's menu.lst is updated so if you removed the kernels the old options are probably not still on the menu.

There is also the 'update-grub' option, which would update your grub with the available kernels. I'd make a backup of your old menu.lst

If you want to try to update grub (explore the differences or pick 'install the package maintainer's version):
```

sudo chroot /temp
sudo update-grub

```


I still don't completely understand where you are regarding installed kernels and your boot menu, but if the above doesn't get you where you need to go just post back.

---

### Post by L337_K3y5 on 2008-07-05
I failed to mention that I could boot into it up to the log-in screen (sorry), so I then went into a fail-safe gnome session, changed it back, and it worked.  Thanks, but now for the uninstalling part.....I removed them using the steps the other guy gave me, and afterwards I thought the other file "linux-2.6.25.9" wasn't used anymore....and thus....I deleted it.  Doesn't seem like a big deal, but now I get this message of it not being able to find its link "linux-2.6.25.9"....I didn't send it to the trash, I wiped it...crap, is there anyway to make the linux folder point back to the 2.6.24.19 kernel instead of the new one, which I have been able to successfully remove, except for screwing up on the last part?  I have the attachment showing a pic. of what error message I get.

---

### Post by unutbu on 2008-07-05
Run 

```
ls -l /usr/src
```

You'll see stuff like
```
total 264712
lrwxrwxrwx  1 root src         21 2008-05-01 19:35 **linux -> /usr/src/linux-2.6.25**
drwxr-xr-x 23 root root      4096 2008-05-02 11:04 **linux-2.6.25**
-rw-r--r--  1 root src   48601689 2008-05-01 19:33 linux-2.6.25.tar.bz2
drwxr-xr-x 19 root root      4096 2008-02-21 15:33 linux-headers-2.6.22-14
drwxr-xr-x  5 root root      4096 2008-02-21 15:33 linux-headers-2.6.22-14-generic
drwxr-xr-x 20 root root      4096 2008-05-01 21:27 linux-headers-2.6.25
-rw-r--r--  1 root src    9185500 2008-05-01 21:02 linux-headers-2.6.25_20080501_i386.deb
-rw-r--r--  1 root src  195213224 2008-05-01 20:57 linux-image-2.6.25_20080501_i386.deb
-rw-r--r--  1 root src   17636559 2008-05-01 21:36 NVIDIA-Linux-x86-169.12-pkg1.run
-rw-r--r--  1 root src     110535 2008-05-01 21:36 nvidia-xconfig-1.0.tar.gz
```

To create the link from linux to /usr/src/linux-2.6.25, type
```

sudo ln -sf /usr/src/linux-2.6.25 /usr/src/linux
```
(Change linux-2.6.25 to your actual directory.)

---

### Post by drs305 on 2008-07-05
So you get to the grub menu and then it boots and during boot you get this message? Or are you able to get fully into ubuntu but you just want to clear this error message? I don't have any such link in my src folder but I've never used an advanced kernel before.

---

### Post by L337_K3y5 on 2008-07-05
I just want to clear this error message...cause it wasn't there before, and I hate not fixing things I've messed up.  I don't know what the linux folder within ```
cd /usr/src
```does, but it is kinda worrrying to not know what it is, then having it broken...:confused:

---

### Post by drs305 on 2008-07-05
> **L337_K3y5 said:**
> I just want to clear this error message...cause it wasn't there before, and I hate not fixing things I've messed up.  I don't know what the linux folder within ```
cd /usr/src
```does, but it is kinda worrrying to not know what it is, then having it broken...:confused:

I was editing my last post when you responded. The system is telling you that there is a broken link, you know you have already deleted the target, you plan on using kernel 19, and ubuntu is smart enough not to commit suicide. 

I understand you want to get everything tidy but the loss of that shortcut isn't going to be missed. If you are really worried about it, rename it rather than delete it. Remember, the link is doing absolutely nothing at the momemt, so if your system is running ok it is doing so without this link.

---

### Post by L337_K3y5 on 2008-07-05
> **drs305 said:**
> I understand you want to get everything tidy but the loss of that shortcut isn't going to be missed. If you are really worried about it, rename it rather than delete it. Remember, the link is doing absolutely nothing at the momemt, so if your system is running ok it is doing so without this link.Thanks, thats a load off of me \\:D/.  Also, I've learned a couple of lessons today about this incident...don't mess with kernels unless you understand wth you're doing. :lolflag:

---

