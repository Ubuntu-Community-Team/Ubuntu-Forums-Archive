---
title: "Install Power ISO in Ubuntu"
date: 2024-05-15
forum: General Help
---

### Post by wollyvio on 2024-05-15
Hi I want to install Power ISO in Ubuntu and I  don't know how to start.Can someone help me?I need this to download an  iso file game.

---

### Post by coffeecat on 2024-05-15
Support, not chat. *Thread moved to **General Help**.*

---

### Post by grahammechanical on 2024-05-15
This is what the original poster is talking about.

[https://www.poweriso.com/download-poweriso-for-linux.htm](https://www.poweriso.com/download-poweriso-for-linux.htm)

Ubuntu comes with a utility to burn ISO images to USB memory sticks. It is called Startup Disk Creator. Or you can download and install mkusb which I have found very useful.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

It might be helpful if we knew what game you want to run. The instructions of the game's developer might be informative.

Regards

---

### Post by wollyvio on 2024-05-16
[[FONT=inherit]https://imgur.com/a/JszUHKB[/FONT]]("https://imgur.com/a/JszUHKB")
This is how I typed in the terminal and I can't get the software to work.How do I fix this issue?

---

### Post by Holger_Gehrke on 2024-05-16
Never knew that there is a Linux version of Power Iso. I've been using gcdemu for a long time for the purpose of mounting CD/DVD images and I'm quite happy with it. There's also Acetone Iso. gcdemu can be found at [https://cdemu.sourceforge.io/](https://cdemu.sourceforge.io/) and they have a PPA for Ubuntu. Acetone Iso is in the repositories.

Holger

---

### Post by yancek on 2024-05-16
The message in the image you posted indicates that a plugin could not be found and suggests reinstalling the application which I take to mean the poweriso application.  Have you tried that?

---

### Post by wollyvio on 2024-05-16
> **yancek said:**
> The message in the image you posted indicates that a plugin could not be found and suggests reinstalling the application which I take to mean the poweriso application.  Have you tried that?

How do I install this plugin?Can someone help?

---

### Post by Holger_Gehrke on 2024-05-16
It's actually not the xcb plugin itself, it's the whole thing which is incompatible. If you run it with
```

QT_DEBUG_PLUGINS=1 ./poweriso.sh

```
you get (a lot) more detailed information. The program tries to bring all the libraries it needs along, but some are missing and are used from the system. Those aren't compatible with the ones the program brings along (specifically libqxcb needs libfontconfig, libfreetype, libbrotlidec, and libbrotlicommon which aren't included and those on your system need a newer version of libc than the one which is included; and of course the included libraries and the program need that old version of libc). It's a classical case of dependency hell. This program was compiled on February 10th in 2019 and the world has moved on since then.

Holger

---

### Post by him610 on 2024-05-16
Seems like you need to use a different utility, or a different OS.
> Supported operating systems:
Windows 11, Windows 10, Windows 8 / 8.1, Windows 7, Windows Vista, Windows 2008, Windows 2003, Windows XP, Windows 2000, Windows Me, Windows 98

---

### Post by wollyvio on 2024-06-05
> **grahammechanical said:**
> This is what the original poster is talking about.

[https://www.poweriso.com/download-poweriso-for-linux.htm](https://www.poweriso.com/download-poweriso-for-linux.htm)

Ubuntu comes with a utility to burn ISO images to USB memory sticks. It is called Startup Disk Creator. Or you can download and install mkusb which I have found very useful.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

It might be helpful if we knew what game you want to run. The instructions of the game's developer might be informative.

Regards
I just want to extract the ISO file.
I replaced the commands powersh file and now I get this error
export LD_LIBRARY_PATH=1.
export QT_QPA_PLATFORM_PLUGIN_PATH=1.
./poweriso
export QT_DEBUG_PLUGINS=1
unset LD_LIBRARY_PATH




./poweriso: ./libc.so.6: version `GLIBC_2.38' not found (required by /lib/x86_64-linux-gnu/libGLX.so.0)
./poweriso: ./libc.so.6: version `GLIBC_2.34' not found (required by /lib/x86_64-linux-gnu/libGLX.so.0)
./poweriso: ./libc.so.6: version `GLIBC_2.38' not found (required by /lib/x86_64-linux-gnu/libGLdispatch.so.0)
./poweriso: ./libc.so.6: version `GLIBC_2.34' not found (required by /lib/x86_64-linux-gnu/libGLdispatch.so.0)
./poweriso: ./libc.so.6: version `GLIBC_2.33' not found (required by /lib/x86_64-linux-gnu/libX11.so.6)
./poweriso: ./libc.so.6: version `GLIBC_2.34' not found (required by /lib/x86_64-linux-gnu/libX11.so.6)
./poweriso: ./libc.so.6: version `GLIBC_2.38' not found (required by /lib/x86_64-linux-gnu/libX11.so.6)
./poweriso: ./libc.so.6: version `GLIBC_2.38' not found (required by /lib/x86_64-linux-gnu/libxcb.so.1)
./poweriso: ./libc.so.6: version `GLIBC_2.33' not found (required by /lib/x86_64-linux-gnu/libXau.so.6)
./poweriso: ./libc.so.6: version `GLIBC_2.33' not found (required by /lib/x86_64-linux-gnu/libbsd.so.0)
./poweriso: ./libc.so.6: version `GLIBC_2.38' not found (required by /lib/x86_64-linux-gnu/libbsd.so.0)
./poweriso: ./libc.so.6: version `GLIBC_2.33' not found (required by /lib/x86_64-linux-gnu/libmd.so.0)

---

### Post by wollyvio on 2024-06-05
> **Holger_Gehrke said:**
> It's actually not the xcb plugin itself, it's the whole thing which is incompatible. If you run it with
```

QT_DEBUG_PLUGINS=1 ./poweriso.sh

```
you get (a lot) more detailed information. The program tries to bring all the libraries it needs along, but some are missing and are used from the system. Those aren't compatible with the ones the program brings along (specifically libqxcb needs libfontconfig, libfreetype, libbrotlidec, and libbrotlicommon which aren't included and those on your system need a newer version of libc than the one which is included; and of course the included libraries and the program need that old version of libc). It's a classical case of dependency hell. This program was compiled on February 10th in 2019 and the world has moved on since then.

Holger
Then how do you fix it? I need POWERISO to extract an ISO file!

---

### Post by dragonfly41 on 2024-06-05
[Alternatives?]("https://alternativeto.net/software/power-iso/?platform=linux&p=2")

---

### Post by Holger_Gehrke on 2024-06-05
> **wollyvio said:**
> Then how do you fix it? I need POWERISO to extract an ISO file!

As I said before there are at least two alternatives for poweriso - acetoneiso and gcdemu. Also, if it's an actual ISO file and not one of the many formats for raw CD dumps, then you don't need any of them. You can just mount the file through a loop device.
```

sudo mount -t iso9660  -o loop file.iso /mnt

```
will make the contents of file.iso accessible in /mnt.

Holger

---

### Post by coffeecat on 2024-06-05
> **wollyvio said:**
> I need POWERISO to extract an ISO file!

No you don't - if you mean to extract a file or files from an ISO. In fact, assuming you are using Ubuntu with gnome, you don't need to install anything at all. Simply right-click on your ISO file in a file manager window and click on the first option, "Open with Disk Image Mounter" and it will be mounted so that you can explore the contents with Files. I don't know whether this is so with the other Ubuntu flavours and desktop environments.

---

