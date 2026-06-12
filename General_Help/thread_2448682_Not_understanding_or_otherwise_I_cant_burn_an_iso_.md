---
title: "Not understanding or otherwise: I cant burn an iso file (19.11)"
date: 2020-08-11
forum: General Help
---

### Post by fprnar on 2020-08-11
I have saved in my "downloads" file a Fedora install. It's an iso file and I simply want to burn it onto a usb sick  such that I can boot from it and install this Fedora.
Though when I use Startup Disk  it will simply not let me open the iso. It detects my 8GB usb no issues (shows at the bottom of the window that it opens with).

I cant find 3rd party software that will let me burn onto the usb since all i get is deamon and rufus and all the other windows programs for this. 

Thanks for your time

---

### Post by jp734 on 2020-08-11
I'd recommend just using the 'dd' command. 

- open terminal
- sudo blkid = check the device id for your usb stick
- type command: dd if=/path/to/iso/file of=/dev/sd? (replace the '?' with the letter for your usb stick)

---

### Post by kneutron on 2020-08-11
--Try **unetbootin**, and make sure the permissions on your ISO file are correct for your userid.

[https://unetbootin.github.io/](https://unetbootin.github.io/)


--Permissions should be at least: rwx------ yourid whatevergroup

...and you also need at least r-x permissions for the directory containing the ISO, or have appropriate Group permissions to be able to "find" it

---

### Post by fprnar on 2020-08-11
re: to jp734 

thanks ! I had seen this before but my luck with cmd is a very sad story to tell. 
Though , providing I got the right "usb stick letter") It says "dd: failed to open /dev/sdb: permission denied"

---

### Post by fprnar on 2020-08-11
> **kneutron said:**
> --Try **unetbootin**, and make sure the permissions on your ISO file are correct for your userid.

[https://unetbootin.github.io/](https://unetbootin.github.io/)


--Permissions should be at least: rwx------ yourid whatevergroup

...and you also need at least r-x permissions for the directory containing the ISO, or have appropriate Group permissions to be able to "find" it

I got lost :( mainly from my own incomptance but also my ubuntu has been dying so its really hard to do the simple tasks without crumbling under failure.

---

### Post by jp734 on 2020-08-11
then type "sudo dd ........"

Once you understand how this work, I'm sure you will like it. And it doesn't matter what linux you're using.

If you need further assistance. you can take a screenshot and post. I'll be glad to assist.

---

### Post by QIII on 2020-08-11
Be careful.  DD's original meaning was "Data Definition".  Its nickname nowadays is Disk Destroyer.

---

### Post by CelticWarrior on 2020-08-12
A safe and very easy to use tool is [Balena Etcher]("https://www.balena.io/etcher/"). It works exactly as the main page's animation suggests.

---

### Post by jp734 on 2020-08-12
> **QIII said:**
> Be careful.  DD's original meaning was "Data Definition".  Its nickname nowadays is Disk Destroyer.

Oh, that's not good :(   - What kind of problems is it causing now a days. I've always use it and still using and never have an issue but will start a research. Though I agree, a simple one character mistake can wipe out a drive that's why I check multiple times before hitting the return key.

---

### Post by CelticWarrior on 2020-08-12
> [COLOR=#000000]I've always use it and still using and never have an issue but will start a research. [/COLOR]

Good for you. That means that you never inadvertently select the wrong destination and run DD. It won't ask questions nor show warnings, it jus does what it was (wrongly) told to do, hence the nickname.

---

### Post by HermanAB on 2020-08-12
Note that an ISO file is a complete file system.  So you just copy it to a USB stick, byte for byte.  

The important thing is to copy it to the correct device and not overwrite your system disk in the process.

***Your system disk is likely sda, so never, never write to sda.***

The way I do this:
Run dmesg to see what is going on:
$ dmesg

Insert the USB stick and run dmesg again:
$ dmesg

It should show a new disk was identified for example /dev/sdc1 or some such (anything except sda).

Now copy the ISO file:
$ sudo cat /wherever/whatever.iso > /dev/sdc
...Long wait...
$ sudo sync
$

La voila.

---

### Post by rbmorse on 2020-08-12
I'm surprised no one has mentioned mkusb:

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

I'be been using it for several years to create install media for various distributions
and it has never failed. 

 The latest version will even handle Windows 10 ver 1901 and
2004 .isos that require a dual FAT 32 partition arrangement because one of the install files is
larger than 4Gb (go Microsoft!). 

 Very user friendly, too.

---

### Post by fprnar on 2020-08-12
> **jp734 said:**
> then type "sudo dd ........"

Once you understand how this work, I'm sure you will like it. And it doesn't matter what linux you're using.

If you need further assistance. you can take a screenshot and post. I'll be glad to assist.


Thanks! I didint get an error message and if i try to close the terminal it says its doing a thing. Ill just leave it be and hope my usb is being burnt or what ever.
You would be surprised I can even open an app without being confused.

---

### Post by fprnar on 2020-08-12
> **rbmorse said:**
> I'm surprised no one has mentioned mkusb:

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

I'be been using it for several years to create install media for various distributions
and it has never failed. 

 The latest version will even handle Windows 10 ver 1901 and
2004 .isos that require a dual FAT 32 partition arrangement because one of the install files is
larger than 4Gb (go Microsoft!). 

 Very user friendly, too.


Ah thanks. Ill have a look at this. Though as many pages with similar tools seem to do, it contains  only about 50% of words that I actually understand. The other 50% are akin to tach-savey peoples slang. hehe

---

### Post by fprnar on 2020-08-12
> **HermanAB said:**
> Note that an ISO file is a complete file system.  So you just copy it to a USB stick, byte for byte.  

The important thing is to copy it to the correct device and not overwrite your system disk in the process.

***Your system disk is likely sda, so never, never write to sda.***

The way I do this:
Run dmesg to see what is going on:
$ dmesg

Insert the USB stick and run dmesg again:
$ dmesg

It should show a new disk was identified for example /dev/sdc1 or some such (anything except sda).

Now copy the ISO file:
$ sudo cat /wherever/whatever.iso > /dev/sdc
...Long wait...
$ sudo sync
$

La voila.


:o that looks simple and I can understand it. providing my DiskDestroyer does that needs done, ill try this out for fun later.
I do have many questions about the terminal but ill make another post about it I am sure. once again, thanks - cos this is cool

---

### Post by QIII on 2020-08-12
:)

I just said to be careful of DD.  I use it all the time.  But as mentioned above, using the wrong destination can wipe a drive in the blink of an eye.

---

### Post by T6&amp;sfpER35% on 2020-08-12
i've done a couple of different linux distros installs , yet could never get it right with a usb.
i just use a dvd and Xfburn, works every time with no hassle.

---

