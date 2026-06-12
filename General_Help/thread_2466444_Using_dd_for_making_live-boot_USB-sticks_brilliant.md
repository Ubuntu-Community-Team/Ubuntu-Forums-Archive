---
title: "Using dd for making live-boot USB-sticks: brilliant, but a few issues remain"
date: 2021-08-27
forum: General Help
---

### Post by GhX6GZMB on 2021-08-27
Making bootable USB-sticks seems to be an eternal issue.
I've found a way using dd. It's very reliable (every USB-stick created the is way has booted every time), but there are a couple of issues. The command is:
```
sudo dd bs=4M if=$HOME/Downloads/lubuntu-20.04-desktop-amd64.iso of=/dev/sdg conv=fdatasync status=progress

```
where:
```
$HOME/Downloads/lubuntu-20.04-desktop-amd64.iso

```
is the downloaded .ISO image and
```
/dev/sdg
```
is the USB-stick.

I've tested this using USB-stick formated as ext4 and as FAT32. Both work (the sticks were empty, whether this works with files stored on the stick is open).

BUT: if no USB-stick is connected, the dd command runs without errors, and just creates a /dev/sdg file instead.

Is there any way to force the dd command to issue an error in this situation? The man page for dd is not very good..

Thanks.

---

### Post by mikewhatever on 2021-08-27
You could add a little if statement:
```

[ -e /dev/sdg ] && sudo dd bs=4M if=$HOME/Downloads/lubuntu-20.04-desktop-amd64.iso of=/dev/sdg conv=fdatasync status=progress>.

```
That said, it is a good idea to verify the correct device is used for output, which makes the above redundant.

---

### Post by monkeybrain20122 on 2021-08-27
Apart from not having any feedback and reporting the correct output device, it is also requires a bit of work to recover the usb drive if you want to use it for other purposes later. I ran into [this issue ]("https://bbs.archlinux.org/viewtopic.php?id=204366")when I was quite new to Linux (I made a liveusb for Fedora, I think) I thought the drive was lost after trying the usual methods to reformat it (like with gparted) and failed.

I am never a big fan of dd, there are tons of more user friendly and less risky ways to create live usb (why is that an 'eternal issue'? It is pretty much a non  issue) I think for most new users the purpose of creating a bootable usb is to get a system up and running as fast and problem free as possible rather than dealing with the intricacies of dd and the like, the set up process (which includes creating a bootable usb) should be as simple as possible. The learning can come later (there are distos who make a point about difficult to set up, supposedly for experts, such as arch, gentoo, LFS and the likes but those belongs to a different category)

---

### Post by HermanAB on 2021-08-28
Note that there is nothing special about dd - except for its special syntax.  All it does is copy a file.  I prefer to use cat, but one could also use head, tail, netcat, or many other little programs that can send one file to another file handle. The only exception seems to be cp, which is trying to be too smart about it!

---

### Post by ajgreeny on 2021-08-28
The problem of reusing a USB which has been used for this purpose with dd is exactly the same as if one uses mkusb from the PPA. I simply create a new partition table with gparted then make a new partition, or even simpler use the Restore function of mkusb; both do the job admirably.

---

### Post by sudodus on 2021-08-28
As you noted in the opening post, **[FONT=Courier New]dd[/FONT]** does a good job cloning. Other copying tools are also good (at cloning). But many of these simple command line tools do what you tell them to do without any question. And many people, even experienced Linux gurus have overwritten valuable data because of a typing error or not remembering that another drive was given the device ID for example [FONT=Courier New]**/dev/sdc**[/FONT], that the user thought 'was' the USB pendrive.

For this reason I made [mkusb](https://help.ubuntu.com/community/mkusb) in order to 'wrap a safety belt around **[FONT=Courier New]dd[/FONT]**'. It helps you identify the drives and provides a final checkpoint, where you can double-check, that you are writing to the correct drive.

---

### Post by VMC on 2021-08-28
I have an alias that id's all drives
```
[FONT=monospace][COLOR=#000000]alias hyb='echo "sudo dd if= of=/dev/sdc bs=8M"&&lsblk'[/COLOR][/FONT]
```
Then I just copy paste what iso i want.

---

