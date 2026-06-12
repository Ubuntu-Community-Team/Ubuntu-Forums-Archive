---
title: "script to detect &amp; format usb drive"
date: 2015-10-07
forum: General Help
---

### Post by jimmyh1972 on 2015-10-07
Hi

how do I write a bash script that will automatically detect & format a usb drive that I plug in?
I wrote it interactively with fdsik (the user still has to wirte some inputs in the termianl)
 but Im looking for a way to do the whole process automatically
I mean when some user plugs in a usb and run the script it will auto detect it and auto format it

Thank's Jimmi

---

### Post by sudodus on 2015-10-07
I made [mkusb](https://help.ubuntu.com/community/mkusb/gui), and it can do what you intend to do. It is a bash shell-script using standard programs and shell functions. You can use it or read the shell-script and pick the pieces you like for your own shell-script. I suggest that you install the bleeding edge version from phillw.net or from the unstable ppa.

Ask me, if you need help to explain something.

---

### Post by jimmyh1972 on 2015-10-07
Its A good one i need only the bash script no gui

---

### Post by sudodus on 2015-10-07
Tell me with more details what you need :-)

---

### Post by jimmyh1972 on 2015-10-08
I need a bash script to detect a removable usb & a bash script that will automatically format in after detection
I know that usually detection is done with sed but I dont know exactly how to write it
tha main gaol is that both scripts will be non interactive
the user just has to plug in the usb and the machin will do the wrest

---

### Post by sudodus on 2015-10-08
***It is risky to have something like this fully automatic alias non interactive, because it may format a drive by mistake, and destroy valuable data.***

You can do things two ways:

1. Detect the USB drive, when it is plugged in. This means that the script must be running in the background and look for USB drives at regular intervals.

2. Plug in the USB drive and after that start the script. I would suggest this method.

Even if the script is mainly non interactive, I think you should have a '**final checkpoint**', where you 'see' the target device, the USB drive, and can confirm that you want to format it.

**Detection:**

I use the method to identify drives, and in particular, USB drives, that is programmed in the **function list_drives**, that you find in mkusb, if you look at it with a text editor or text viewer.

I have a stand-alone version of it in the attached script file **list-drives.gz**

**Formatting:**

There are many ways to format a [USB] drive. The standard way is an MSDOS partition table and one partition with the FAT32 file system, but there are several alternatives, depending on how you intend to use the drive. Some of these alternatives are implemented in mkusb's wipe menu.

[LIST]Standard: create MSDOS partition table with FAT32 partition
[*]Big drive: create GUID partition table with NTFS partition
[*]General: use 'gparted' to make partition table and partition(s)
[*]Advanced: create GUID partition table (skeleton for installing OS)
[*][COLOR="#696969"](wipe the First megabyte (mibibyte))[/COLOR]
[*][COLOR="#696969"](wipe the Whole device - consider other options except for special cases)[/COLOR]
[/LIST]

See the following functions in the mkusb script

[LIST]
[*]function mk_msdos
[*]function mk_gpt_ntfs
[*]function mk_gpart
[*]function mk_gpt_skel
[/LIST]

---

### Post by jimmyh1972 on 2015-10-08
Thank you so much for this one! I really appreciate it!
one more question - how do I create LVM from several hard drives?

---

### Post by sudodus on 2015-10-09
I am no expert on LVM. I can use the automatic options in the Ubuntu installer (ubiquity). I can find and read tutorials and manual pages, but I have never used LVM manually, and I'm afraid that those who know will not find this post (because the title of the thread is about another problem).

Are you sure that you want LVM and not RAID? Maybe you want both? (Sorry, but it is the same problem with RAID, I don't know much about it.)

So I suggest that you ***start another thread*** about LVM with a good title describing your problem/question and as much details as possible in the opening post.

---

### Post by jimmyh1972 on 2015-10-09
Thank's for helping in the 2 other cases its been a pleasure!
all the best

---

### Post by sudodus on 2015-10-09
You are welcome, and good luck with your project :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

