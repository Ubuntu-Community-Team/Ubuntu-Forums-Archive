---
title: "[SOLVED] GRUB thinks I have 2 ubuntus+A secret within my computer?"
date: 2008-05-29
forum: General Help
---

### Post by nerd0795 on 2008-05-29
I recently updated ubuntu (The one with the little light bulb up on the top right)  then after it finished it asked me to restart.  Then it logged me off and it wanted me to log in.  Then all of a sudden it restarted.  Then I noticed GRUB  added 2 more to the list of os.  

Now I have ubuntu kernal generic (whatever version
ubuntu kernal generic (safe mode I think?) (whatever version)
Ubuntu Kernal generic (whatever version but I number less then the first)
Ubuntu Kernal generic (safe mode I think it's called)
Memtest or whatever it's called
Other Operating systems:
Windows 98/2000/Me/XP <--- I don't have any of them....
Windows Longhorn/Vista loader

There are 2 questions what is a way to get rid of the old version of ubuntu off the OS list in Grub (the 3rd and 4th in the list)

Also why do u think it says it thinks I have 98/2000/Me/XP

I know I have 3 partitions for Vista (I think)

I have 2 hard drives

Here is what my partitions look like

[8GB NTFS Partion][70GB NTFS Partion][40GB Ubuntu Partion (extended][117GB NTFS Partion]

What do u think this means?

P.S I do have Windows vista on my machine.

---

### Post by drs305 on 2008-05-29
> **nerd0795 said:**
> 

There are 2 questions what is a way to get rid of the old version of ubuntu off the OS list in Grub (the 3rd and 4th in the list)


You can uninstall the old kernel via synaptic. Removing an old kernel will remove the item in menu.lst

You can edit /boot/grub/menu.lst and change "howmany=all" to "howmany=1" or two. You can also do this if you install startupmanager and go to System, Administration, StartUp-Manager, Advanced, number of kernels to keep.

You can comment out the lines in menu.lst

You can remove the lines in menu.lst

If you need more info on any of these options, ask or search the forum.

---

### Post by nerd0795 on 2008-05-29
Thank you

---

### Post by meierfra. on 2008-05-29
I wouldn't use "howmany=1". Once in a while it  can happen that a new kernel is incompatible with you hardware. For this case you really want to have your old kernel on the Grub menu to  be able to boot into Ubuntu.

---

### Post by lengo on 2008-08-30
> **nerd0795 said:**
> I recently updated ubuntu (The one with the little light bulb up on the top right)  then after it finished it asked me to restart.  Then it logged me off and it wanted me to log in.  Then all of a sudden it restarted.  Then I noticed GRUB  added 2 more to the list of os.  

Now I have ubuntu kernal generic (whatever version
ubuntu kernal generic (safe mode I think?) (whatever version)
Ubuntu Kernal generic (whatever version but I number less then the first)
Ubuntu Kernal generic (safe mode I think it's called)
Memtest or whatever it's called
Other Operating systems:
Windows 98/2000/Me/XP <--- I don't have any of them....
Windows Longhorn/Vista loader

Same story here: a recent update and new stuff in GRUB, namely another kernel (.15 in addition to .14, regular and safe mode) and Memtest. Where'd this stuff come from?! And why is Memtest now the default?! This is cruel and unusual punishment for new users!!! Can anyone help me restore my GRUB? I.e., one kernel (with regular and safe mode), no Memtest, and XP as my default (as anathema as that may be :-) )?

---

### Post by drs305 on 2008-08-30
> **lengo said:**
> Same story here: a recent update and new stuff in GRUB, namely another kernel (.15 in addition to .14, regular and safe mode) and Memtest. Where'd this stuff come from?! And why is Memtest now the default?! This is cruel and unusual punishment for new users!!! Can anyone help me restore my GRUB? I.e., one kernel (with regular and safe mode), no Memtest, and XP as my default (as anathema as that may be :-) )?

You can get the answers by reading the link in my signature line about StartUp-Manager. It pretty much explains what's going on and how to fix it. These are all easy fixes - StartUp-Manager just uses a gui app to make editing the menu.lst worry-free.

---

### Post by Garratt on 2008-08-30
> **meierfra. said:**
> I wouldn't use "howmany=1". Once in a while it  can happen that a new kernel is incompatible with you hardware. For this case you really want to have your old kernel on the Grub menu to  be able to boot into Ubuntu.

yea i was going to say the same thing...! just keep it there and edit out the me/xp/2000 from the menu.lst

you can check one of my old posts called "omg please help error17!"
to work out how to do this...

theres a few ways, one basic command you should get yourself aquainted with is: 
```
sudo nautilus
```
this opens up file browser in *root*

the menu.lst is in:   /boot/grub/menu.lst

or i think to directly open the file its:
```
gksudo gedit /boot/grub/menu.lst
```

you menu/lst should look similar to this at the bottom (obviously not exact as you have different hdd config etc. but i also run vista/ubuntu.

```
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f47a88a8-6205-4a90-afb7-dc6c6c9548a7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f47a88a8-6205-4a90-afb7-dc6c6c9548a7 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
chainloader	+1

```

If you are unsure of what you are doing you can comment lines out, meaning they become "comments" rather than "code" in the file, you can comment by placing # at the start of the lines you wish to comment.

Don't worry about stuffing it up too much, if you do anything like acedently comment out your vista and ubuntu hdd's so neither will load you can use the Live CD -> Try ubuntu without any change to the computer -> then edit it again, (would need to mount the ubuntu drive in this case before editing)

---

### Post by lengo on 2008-08-30
Thanks drs305 and Garratt--both responses very helpful. One more question: Do I assume that I use the highest number kernel (in my case n.nn.15) to boot rather than the lower one (n.nn.14)? And further, is the higher number kernel the result of my recent update? Thanks!

---

### Post by drs305 on 2008-08-30
> **lengo said:**
> Thanks drs305 and Garratt--both responses very helpful. One more question: Do I assume that I use the highest number kernel (in my case n.nn.15) to boot rather than the lower one (n.nn.14)? And further, is the higher number kernel the result of my recent update? Thanks!

Yes, the higher number is the more recent kernel and probably the one you just upgraded to. You should keep the older kernel on your menu at least for a while should you need to revert to it for some reason.

Your grub settings may need to be changed to automatically use the new kernel. The tutorial on grub's menu.lst, linked below, can give you instructions on how to make a specific kernel the default. You can also just check which kernel you are using with "uname -r", which will tell you the running kernel. If you are happy with the result you don't have to change the grub menu...

---

