---
title: "Deleting Ubuntu Partitions With Gparted In Ubuntu Live CD"
date: 2017-05-22
forum: General Help
---

### Post by voodoochild16 on 2017-05-22
[CENTER][http://i696.photobucket.com/albums/vv324/voodoochild16/smaller_zpsydirq4lk.jpg](http://i696.photobucket.com/albums/vv324/voodoochild16/smaller_zpsydirq4lk.jpg)


**If i made this any smaller it would be hard to see. It is now only 114kb's. **




[/CENTER]
Hi all, so I am trying to delete a Ubuntu formatted drive by going into Ubuntu with a Live CD and using Gparted. But, for some reason, it won't let me Delete the partitions while inside of Gparted. Is there another way of doing this?. I currently have no way of booting into this installation of Ubuntu, the laptop wont let me. Thanks in advance.

---

### Post by wildmanne39 on 2017-05-22
Please use thumbnails or Url's when posting images because many people have slow internet connections and loading pages with large images is very difficult for them.

---

### Post by voodoochild16 on 2017-05-22
> **wildmanne39 said:**
> Please use thumbnails or Url's when posting images because many people have slow internet connections and loading pages with large images is very difficult for them.

It is now only 114 kb's and if it goes any smaller than that it will be hard to see, thank you and sorry about that.

---

### Post by wildmanne39 on 2017-05-22
> **voodoochild16 said:**
> It is now only 114 kb's and if it goes any smaller than that it will be hard to see, thank you and sorry about that.

Please leave it as an url then, it is a very large image when clicked on.

---

### Post by voodoochild16 on 2017-05-22
[COLOR=#070F14][FONT=Verdana]I just booted into an Ubuntu LiveCD, and I noticed that with the use of the "Disks" program, or even "Gparted", I cannot delete the volume. [/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]I read somewhere on Google that the drive may be an "LVM" formatted drive, and needs to be deactivated using a command line, in order to unlock it and delete the partition. [/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]I still cant find instructions on how to do that yet.[/FONT][/COLOR]

---

### Post by vasa1 on 2017-05-22
> **voodoochild16 said:**
> It is now only 114 kb's and if it goes any smaller than that it will be hard to see, thank you and sorry about that.
You could also trim the extra area off and post just the relevant area.

Keep in mind people access the forum via mobile devices as well and won't want to expend their bandwidth on bloated images.

Use the forum's attachment facility which is accessed by clipping on the paperclip icon above the text box. If you don't see the paperclip icon, click on "Go Advanced" below the text box.

Here's how I trimmed your image:

---

### Post by voodoochild16 on 2017-05-22
> **vasa1 said:**
> You could also trim the extra area off and post just the relevant area.

Keep in mind people access the forum via mobile devices as well and won't want to expend their bandwidth on bloated images.

Use the forum's attachment facility which is accessed by clipping on the paperclip icon above the text box. If you don't see the paperclip icon, click on "Go Advanced" below the text box.

Here's how I trimmed your image:

Perfect, thanks. Now I give up because it's impossible for me to boot from Ubuntu after reinstalling 3 times already. I see a LVM partition, but I can't use the command line to unlock it because you can't become a Root user while running Ubuntu off of the LiveCD. 

I mean this is rediculous, I have a almost perfectly brand new Dell Inspiron that has nothing wrong with it (hardware wise) but this software problem is preventing me from doing anything!!!.

---

### Post by deadflowr on 2017-05-22
> but I can't use the command line to unlock it because you can't become a Root user while running Ubuntu off of the LiveCD. 

I do that all the time.
open a terminal and run
```
sudo <some-command or action-here>
```

live sessions do not require a password to sudo.

---

### Post by oldfred on 2017-05-22
I do not really know LVM, never used it.
But it really is for advanced users, but also is required if you want full drive encryption.

You would have to use LVM tools to mount & delete the LVM. And unencrypt the / partition so it can be seen to delete.
 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM) 

This has details on mounting an encrypted partition in steps 1 thru 4.
[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)
then you can delete
[http://tldp.org/HOWTO/LVM-HOWTO/removevgs.html](http://tldp.org/HOWTO/LVM-HOWTO/removevgs.html)

---

### Post by voodoochild16 on 2017-05-23
> **oldfred said:**
> I do not really know LVM, never used it.
But it really is for advanced users, but also is required if you want full drive encryption.

You would have to use LVM tools to mount & delete the LVM. And unencrypt the / partition so it can be seen to delete.
 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM) 

This has details on mounting an encrypted partition in steps 1 thru 4.
[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)
then you can delete
[http://tldp.org/HOWTO/LVM-HOWTO/removevgs.html](http://tldp.org/HOWTO/LVM-HOWTO/removevgs.html)

No problem, me either, [although I found this link to be useful]("https://askubuntu.com/questions/565101/how-to-format-a-hard-drive-to-ntfs-on-ubuntu-14-04"). 

I was able to unlock the encrypted partition while running off of an Ubuntu Live DVD (most recent version of Ubuntu was used). I just launched terminal and followed the directions. 

As this was a very long and grueling process to bring the Inspiron 11 3162/3164 back to life, [I made my own post on this to document every step of the way of how I got it running on Windows 10 again. ]("http://willthisrestoreitself.blogspot.ca/2017/05/recovering-infamous-inspiron-11.html")

I personally use Ubuntu on an older computer for my home theater, but I really didn't like using it on this machine, it took so long to get it back to the factory settings, it will stay running Windows 10. 

Thanks for the advice, hopefully this helps someone else. 

Cheers.

---

