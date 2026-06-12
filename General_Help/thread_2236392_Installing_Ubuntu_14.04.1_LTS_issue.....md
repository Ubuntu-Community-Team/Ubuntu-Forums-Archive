---
title: "Installing Ubuntu 14.04.1 LTS issue...."
date: 2014-07-26
forum: General Help
---

### Post by mark155 on 2014-07-26
I downloaded the 14.04.1 version of Ubuntu yesterday and burned it to a disk. Then I rebooted my machine to the DVD drive. Then a screen popped up giving me several options, and I chose Install Ubuntu. However, after I highlighted Install and pressed enter, all I get is a blank screen. After that, I transferred the Ubuntu file to a flash drive using the [ Pen Drive Linux's USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") and still got a blank screen after rebooting to the Flash Drive and hitting Install. My machine is a Asus P8Z77-V(Intel 4000hd graphics), no graphics card, and I'm running Windows 7 Professional 64 bit. Any ideas on what the problem is would be appreciated.

---

### Post by sudodus on 2014-07-26
Maybe there are problems with the driver for graphics or wifi, but Intel graphics is often working with the Ubuntu flavours. I suggest that you [try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389") and that you try several boot options according to this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by mark155 on 2014-07-26
Thanks for the reply. I had already tried most those suggestions, and they didn't work. Anyone have other suggestions. Thanks

---

### Post by sudodus on 2014-07-26
- Have you checked the iso file with md5sum?

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

- Have you checked if the computer runs UEFI or BIOS? You need to run/install Ubuntu in the same mode as Windows is installed.

- Sometimes it helps to run Intel graphics with UXA acceleration according to the following link (Yes I know, it is mainly for old hardware, but I have seen cases where it has also helped with newer graphics chips).

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics)

---

### Post by mark155 on 2014-07-26
I did a MD5 checksum and the values weren't even close.  This is what the MD5 hash should have been:[TABLE]
[TR]
[TD][FONT=inherit]dccff28314d9ae4ed262cfc6f35e5153[/FONT]
[/TD]
[TD][FONT=inherit]ubuntu-14.04-desktop-amd64.iso[/FONT]
[/TD]
[/TR]
[/TABLE]
and this is what was calculated:
119cb63b48c9a18f31f417f09655efbd

Here's the download link. I've downloaded the 64 bit desktop version 14.04 3 different times with no luck. I guess they were all corrupted.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

 My computer runs [COLOR=#000000] UEFI .[/COLOR]

---

### Post by sudodus on 2014-07-26
1. Try to download from a ***mirror*** or even better via ***torrent***, because then the md5sum is checked as part of the process. 


2. Read  carefully the following threads about UEFI
[URL="http://ubuntuforums.org/showthread.php?t=2147295"]
UEFI Installing - Tips[/URL]

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Jesse_Campton on 2014-07-26
Did you boot into Ubuntu live and try installing from there? I have had issues in the past from trying to install from the bootup installer vs the installer from the desktop.

---

### Post by mark155 on 2014-07-26
> **Jesse_Campton said:**
> Did you boot into Ubuntu live and try installing from there? I have had issues in the past from trying to install from the bootup installer vs the installer from the desktop.

I'm not sure what your talking about as this is my first time to use Ubuntu. However, I did download the file from a torrent and got the same MD5 hash output as from the file I downloaded from the Ubuntu website:
[COLOR=#000000]119cb63b48c9a18f31f417f09655efbd. I also made the BIOS changes as suggested in the link above, and it still doesn't work.[/COLOR]

---

### Post by mark155 on 2014-07-26
Finally got it working. Thanks for the replies and help!

---

### Post by sudodus on 2014-07-27
Congratulations :KS

Please share with the Ubuntu Forums ***how*** you solved your problem!

Finally, if things are working now, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

---

### Post by craig10x on 2014-07-27
By the way, what Jessie_Campton meant was that when you run the iso disc of ubuntu, it is best to hit the button that says "try ubuntu" first...when you click that on, it boots into a live session that one can "play with" before actually installing...In that "live session" there is an icon on the desktop that says "install ubuntu 14.04" for example...and when you double click it brings up the installer...
For some reason, installs often go smoother when you do it that way...as opposed to just hitting that "install ubuntu" button you saw initially...

Just something to keep in mind for the future ;)

---

### Post by Jesse_Campton on 2014-07-28
Thank you for updating that for me craig10x, got all caught up with family that arrived this weekend and wasnt able to get back to the computer... Glad you were able to get Ubuntu installed, can you share with us, how you went about fixing the problem and mark this thread closed. thanks

---

### Post by mark155 on 2014-07-28
> **Jesse_Campton said:**
> Thank you for updating that for me craig10x, got all caught up with family that arrived this weekend and wasnt able to get back to the computer... Glad you were able to get Ubuntu installed, can you share with us, how you went about fixing the problem and mark this thread closed. thanks

I'm with you. If someone could post how they fixed the problem on a similar type of machine([COLOR=#000000]Asus P8Z77-V motherboard, Intel 4000hd graphics, no graphics card,  Windows 7 Professional 64 bit)[/COLOR] that would help a lot. I went and tried to install Debian and ran into the same issues. There are a lot of issues installing Linux on machines that use UEFI, instead of BIOS. If someone has successfully installed Ubuntu on a machine similar to mine, I would like to know how you did it step by step, as I have pretty much tried everything suggested so far. My purpose is to run GNS3 in a Linux environment as it is more stable than Windows. I can download and run Ubuntu in virtual box, but that would bring up other issues trying to integrate it with GNS3 as I am already running a GNS3 IOU server VM in virtual box with GNS3. The developers of GNS3 said the addition of Ubuntu into virtual box would add too many layers to the GNS3 interface.

---

### Post by Jesse_Campton on 2014-07-29
I am not sure if this will help, but here is what I have found:  [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by Topsiho on 2014-07-29
The correct md5sums are:

```

dccff28314d9ae4ed262cfc6f35e5153 *ubuntu-14.04-desktop-amd64.iso
c4d4d037d7d0a05e8f526d18aa25fb5e *ubuntu-14.04-desktop-i386.iso
01545fa976c8367b4f0d59169ac4866c *ubuntu-14.04-server-amd64.iso
08d25bf879e353686a974b7b14ae7d81 *ubuntu-14.04-server-i386.iso
119cb63b48c9a18f31f417f09655efbd *ubuntu-14.04.1-desktop-amd64.iso
a4fc15313ef2a516bfbf83ce44281535 *ubuntu-14.04.1-desktop-i386.iso
ca2531b8cd79ea5b778ede3a524779b9 *ubuntu-14.04.1-server-amd64.iso
3aa14ca13d52df070870d39306f4a4eb *ubuntu-14.04.1-server-i386.iso
b31731ea6cdbebe1d02f8193db420886 *wubi.exe

```

So the correct md5sum for 04.1 is 119 etc, the other "correct" md5sum is for the original 0.4

Sudodus is right asking you to describe how you solved this problem, which is only possible because your .iso file was correct after all :)

Topsiho

---

