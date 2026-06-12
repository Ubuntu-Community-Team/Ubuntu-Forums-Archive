---
title: "Wubi doesn't use an ISO and keeps downloading"
date: 2008-05-14
forum: General Help
---

### Post by kman16 on 2008-05-14
I'm trying to use wubi on XP. Download speeds are ridiculesly slow (few day long...), so I downloaded an desktop ISO file and putted it in the same directory with wubi.

when I launch wubi it keeps trying to download and wont use the ISO, even if there is no internet connection.

What should I do to make it work???

---

### Post by terryeden on 2008-05-14
I'm having the same problem.

I've created a directory D:\wubi\

The only two files in it are
Wubi-8.04.exe and hardy-desktop-i386.iso

I double-click Wubi, enter my details and it goes off and tries to download the ISO.

Are there any command line parameters I can use to force it to use the ISO?

---

### Post by ago on 2008-05-14
If you look into the wubi log (which is in your user temp folder) there should be an explanation.

---

### Post by kman16 on 2008-05-14
can't find any wubi log.
Where is it supposed to be? or what is that log exact filename.

---

### Post by ago on 2008-05-14
Type %temp% in explorer URL bar

---

### Post by kman16 on 2008-05-14
found it, thanks.

heres the relevant part (I think), it is written twice.
```
DetectIso
      IsValidIso ispoath=C:\wubi\hardy-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\Nir\LOCALS~1\Temp\nse4B.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\Nir\LOCALS~1\Temp C:\wubi\hardy-desktop-i386.iso
      IsValid 
no cdinfo
CDInfo cleared
```

---

### Post by terryeden on 2008-05-14
The section I've found says
```
D:\wubi\hardy-desktop-i386.iso
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release i386 (20080509)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080509 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
different version 8.04 != 8.04.1
```

Which at first I thought was caused by it thinking that I have and AMD64 processor (I have an Intel U7600).  So, I downloaded the AMD64 ISO, but I get this

```
DetectIso
      IsValidIso ispoath=D:\wubi\hardy-desktop-amd64.iso
      ExtractIsoInfo
      d:\Profiles\edend\LOCALS~1\Temp\nsb133.tmp\7z.exe e -y -i!.disk\info -od:\Profiles\edend\LOCALS~1\Temp D:\wubi\hardy-desktop-amd64.iso
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080509)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080509 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
different version 8.04 != 8.04.1
```

So, is it choking because I'm using 8.04.1?

Is there any way to pass Wubi my proxy settings?

---

### Post by ago on 2008-05-14
yes there is a mismatch. You have to use wubi rev 501 with 8.04 (final one) iso and wubi rev 505+ with 8.04.1 (daily builds) isos.

---

### Post by kman16 on 2008-05-14
well,  I don't have that mismatch...
isn't there a command line parameter to force installing from the iso?

---

### Post by ago on 2008-05-14
It seems C:\wubi\hardy-desktop-i386.iso that is not a correct ISO.

If it is valid it should contain a file called .disk/info.

Also the ISO should be called ubuntu-8.04-desktop-i386 (the name "hardy-desktop-i386.iso" is used for daily builds). Here is the correct URL:

[http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.iso](http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.iso)

---

### Post by kman16 on 2008-05-14
Thats the file I got, I've changed its name just to see if it will make any difference (which it didn't). originaly it was called "ubuntu-8.04-desktop-i386".

.disk/info is in the BTW.

---

### Post by ago on 2008-05-14
Doublecheck the md5 of the ISO, from the log it does not seem like it is possible to extract such file from the ISO the command that fails is

7z.exe e -y -i!.disk\info -oC:\Temp C:\wubi\hardy-desktop-i386.iso

(you may need to get 7z separately).

---

### Post by terryeden on 2008-05-15
> **ago said:**
> yes there is a mismatch. You have to use wubi rev 501 with 8.04 (final one) iso and wubi rev 505+ with 8.04.1 (daily builds) isos.

For those looking, the latest version is at [http://wubi-installer.org/devel/minefield/](http://wubi-installer.org/devel/minefield/)

The Wubi team either need to point to the correct ISO or place this in the FAQ.

T

---

### Post by ago on 2008-05-15
The new minefields are not yet ready, please use the main download for the time being. I will announce when they are ready.

---

### Post by terryeden on 2008-05-15
> **ago said:**
> The new minefields are not yet ready, please use the main download for the time being. I will announce when they are ready.

Ah, just used 507 - hope it doesn't bork anything :-)

Can you change [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php) so that "Can I use an existing ISO/CD instead of letting Wubi download a new one?" points to ISOs which are usable by the current version of Wubi?  I'm sure I'm not the only one caught out by that.

T

---

### Post by ago on 2008-05-15
will do

---

### Post by bamsan on 2008-05-15
> **terryeden said:**
> I'm having the same problem.

I've created a directory D:\wubi\

The only two files in it are
Wubi-8.04.exe and hardy-desktop-i386.iso

I double-click Wubi, enter my details and it goes off and tries to download the ISO.

Are there any command line parameters I can use to force it to use the ISO?

I believe that the .iso should be inside D:\wubi\install\
While the wubi installer could be anywhere

---

### Post by ago on 2008-05-15
You have to put ISO and wubi.exe in the same folder. It does not matter how the folder is called. If you have several ISOs spread out, make sure to remove into a different folder first. In particular wubi will look into folders called \ubuntu* as well as your desktop.

---

### Post by bamsan on 2008-05-15
Yup, ago is right. Wubi installer and ubuntu-8.04-desktop-i386.iso sould be in the same place. wubi will copy the .iso to the apropriate place ie, destination_drive:\ubuntu\install\

however, u can give wubi a little hand by copying the iso into destination_drive:\ubuntu\install\
this way, wubi will skip copying iso during instalation

---

### Post by kman16 on 2008-05-15
my ISO was missing few MB...

replaced it with a new one and now I get an "error 15: file not found" massege. after its trying to run "find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst"

then grub4DOS gives me few places to look for the file or commandline, reboot or halt options to choose.

I found two "menu.lst" file using XP in:
c:\ubuntu\winboot
c:\ubuntu\install\boot\grub

don't know what to think...

---

### Post by ago on 2008-05-15
Uninstall, run chkdsk /r on your disk, and then try to install again. Let wubi download the iso for you.

---

### Post by kman16 on 2008-05-15
I'm running chkdsk right now, but I'm afraid letting wubi to do the download isn't an option. It take about four days(!) from some reason...

---

### Post by ago on 2008-05-15
> **kman16 said:**
> I'm running chkdsk right now, but I'm afraid letting wubi to do the download isn't an option. It take about four days(!) from some reason...

It selects randomly one of the country mirrors, might be that it got a particularly slow one. If you stop restart will likely get a different one.

---

### Post by kman16 on 2008-05-15
did the chkdsk thingy and tryed with the same 
ISO. I get the same error...

I'm in Israel and maybe it can't find any mirror here. downloading ISO from a mirror I choose in Israel is quite fast.
I'll try to varify the MD5SUM (ot what ever that thing is called.

I hope its just another bad ISO other wise I think I'll just stay with XP.

---

### Post by ago on 2008-05-15
Make sure you use wubi rev 501 with [http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.iso](http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.iso)

If it keeps downloading post the wubi log (is in your windows user temp folder)

---

### Post by Midwest-Linux on 2008-05-15
Can Wubi be used for other distros? 

 If someone names a ISO file as Ubuntu and puts it in the Wubi folder. Would Wubi be able install it? 

 For instance If I took Knoppix 5.3 and changed the file name from Knoppix to Ubuntu 8.04 would Wubi install it thinking it was Ubuntu but install it anyway as Knoppix??

Or

If I took Linux Mint 4.0 and renamed it as Ubuntu 8.04 as placed it in the same file as Wubu 8.04, could I install Linux Mint 4.0 that way?

---

### Post by kman16 on 2008-05-16
ago>> the wubi and ubuntu version match, the downloading problem was solved after replacing the first ISO file. the installation went on fine (using the new ISO) but after rebooting i got [COLOR="DarkRed"]error 15[/COLOR] from the GRUB. (grub(?) can't find menu.lst) :confused:

Midwest-Linux>> I really don't know much about linux, but in that case my guess is that you'll have to work harder then just change the filename. the wubi looks into the iso for: .disks/info and read that file with the distro information.

---

### Post by ago on 2008-05-16
> **Midwest-Linux said:**
> Can Wubi be used for other distros?
Not without being recompiled. See the customization section in the wubi guide

> If someone names a ISO file as Ubuntu and puts it in the Wubi folder. Would Wubi be able install it? 
It will not work

---

### Post by ago on 2008-05-16
> **kman16 said:**
> ago>> the wubi and ubuntu version match, the downloading problem was solved after replacing the first ISO file. the installation went on fine (using the new ISO) but after rebooting i got [COLOR="DarkRed"]error 15[/COLOR] from the GRUB. (grub(?) can't find menu.lst) :confused:

[https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742](https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742)

the section on error 21 might also be relevant

---

### Post by kman16 on 2008-05-16
according to the link, if its really an error 15 problem I can't think of any thing more to do. 
(No RAID as far as I know.
 Its an IBM laptop, I don't believe its HD is encrypted.
 The ISO and wubi match.
 Already ran chkdsk.
 No other partition exist.
)

do you think changing menu.lst file like suggested in the part about error21 can solve my problem?

I think I had enough linux for a while... (and that supused to be the easier way to install it). thank you very much for the effort, maybe I better stay with XP for now.

---

### Post by Veacheslav on 2009-11-13
Main system WinXP Sp3 32bit.
Cannot install ubuntu 8.04.3.
I have placed wubi.exe and ubuntu iso in the same dir, but it tries to connect to internet to download some additonal files.

here are some lines from Wubi-8.04.3-rev510.log file
> DetectIso
      IsValidIso ispoath=D:\Install\ISO\Ubuntu\ubuntu-8.04.3-desktop-i386.iso
      ExtractIsoInfo
      C:\WINDOWS\Temp\nso40.tmp\7z.exe e -y -i!.disk\info -oC:\WINDOWS\Temp D:\Install\ISO\Ubuntu\ubuntu-8.04.3-desktop-i386.iso
C:\WINDOWS\Temp\nso40.tmp\7z error: error
      IsValid 
no cdinfo
CDInfo cleared 

there is a way to fix 7zip error?

---

