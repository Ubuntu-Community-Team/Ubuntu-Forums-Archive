---
title: "Persistence File Increase Keeps Giving Me syslinux"
date: 2014-04-18
forum: General Help
---

### Post by zane99 on 2014-04-18
I'm about to try:
[http://askubuntu.com/questions/71655/wont-boot-from-usb-stops-at-syslinux-copyright](http://askubuntu.com/questions/71655/wont-boot-from-usb-stops-at-syslinux-copyright)

But my Ubuntu isolinux.cfg file looks nothing even close to the answer he gave so I'm not going to try it until I get a confirmation.
Does anyone have any up to date answers for 13.10?

---

### Post by sudodus on 2014-04-18
With the information we have now, the only responsible answer would be 'no', but please describe what you have and what you want! The more details, the easier it will be to help :-)

---

### Post by zane99 on 2014-04-18
I don't really know what else to say.  I'm in Ubuntu right now and I'm going to ATTEMPT that solution, but whether or not it'll work is the question.
I have nothing on the hard drive at the moment so I guess I don't really care if it messes up or not, I guess this thread was kind of unneeded.

---

### Post by sudodus on 2014-04-18
- Do you have a USB pendrive and intend to install Ubuntu?
- What version of Ubuntu is put into it?
- Which tool did you use to put Ubuntu into the USB pendrive?
- What happens when you try to boot from it?

- Why do you want to try that particular solution, when your Ubuntu isolinux.cfg file looks nothing even close to the answer he gave?

Edit: And please describe the computer:

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by zane99 on 2014-04-18
- Do you have a USB pendrive and intend to install Ubuntu?
I have a USB but I do not intend on installing Ubuntu as Windows 8.1 has more compatibility with other softwares.
- What version of Ubuntu is put into it?
13.10
- Which tool did you use to put Ubuntu into the USB pendrive?
Universal USB Installer
- What happens when you try to boot from it?
I get a syslinux edd error


- Why do you want to try that particular solution, when your Ubuntu isolinux.cfg file looks nothing even close to the answer he gave?
Because I have no idea what I'm doing xD
Edit: And please describe the computer:


- Brand name and model
HP Pavilion G6
- CPU
Intel Core i3
- RAM (size)
4GB
- graphics chip/card
Intel Graphics (3000 I think)
- wifi chip/card
Realtek

---

### Post by sudodus on 2014-04-18
The computer should be able to run any Ubuntu flavour, so standard Ubuntu 13.10 is OK.

You want to run Ubuntu from the USB drive, not install it to the internal drive.

I think there might be several issues to fix for it to work.

1. You may need to change the settings of the UEFI/BIOS settings to succeed. I suppose you don't want to do it every time you switch between Windows and Ubuntu, so you keep UEFI for Windows to work. But you can [try to] unset ***fast boot*** and ***secure boot*** in the UEFI/BIOS menu system.

2. You need the Ubuntu desktop 64-bit iso file. Check it with md5sum that it matches the listed string in [UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes").

Test in another computer, if the pendrive works (if you can boot from it)

3. If still problems, try another tool to flash the iso file into the pendrive. I suggest ***Unetbootin*** according to [Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")

Test in another computer, if the pendrive works (if you can boot from it)

4. If that does not work, clone the image into the pendrive. In Ubuntu you can use [mkusb]("http://Ubuntu Forums tutorial &quot;Howto make USB boot drives&quot;"), but I guess you have to do it from Windows, so try***win32diskimager***

[http://sourceforge.net/projects/win32diskimager/](http://sourceforge.net/projects/win32diskimager/)

Test in another computer, if the pendrive works (if you can boot from it)

5. If still no go, please describe what happens (the detailed output to the screen, if any)

---

### Post by zane99 on 2014-04-21
Attempted everything on there and nothing.
There is no error showing, it's just not increasing the file size.  Here's what my two 'main' things look like:
[IMG]http://i4.minus.com/jlppdBwbWrEeg.png[/IMG]
.[IMG]http://i2.minus.com/jEWKwv198X5ZE.png[/IMG]

---

### Post by sudodus on 2014-04-21
What is the problem?

Your casper rw-partition is 28.77 GiB and is using most of the drive space and you have 29.20 GiB unused, in other words a lot of space for programs and data files.

Please check from within a terminal window with the following command and post the output

```
df -h
```

I think it will show that the casper rw-partition is actually used by the system.

---

