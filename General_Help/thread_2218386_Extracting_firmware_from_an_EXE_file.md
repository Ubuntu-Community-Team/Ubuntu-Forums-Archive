---
title: "Extracting firmware from an EXE file"
date: 2014-04-20
forum: General Help
---

### Post by Keith_Beef on 2014-04-20
I have a Samsung UA32C5000 and would like to update the firmware. Sadly, Samsung is one of those companies who supplies the firmware upgrade as a self-extracting EXE file that, for no good reason, must first of all be unpacked on a Windows computer to a flash drive, then the flash drive is plugged into the TV.

So, I believe that if I could unpack the firmware I should be able to install it to the TV.

A little while ago, I upgraded the firware on my mainboard, and this firmware was also supplied as a self-extracting EXE file. I used archive Manager to unpack the image, then used flashrom to do the upgrade.

So by the same logic, I think that Archive Manager should be able to extract the image for the Samsung TV… but I obviously don't want to end up with a 32-inch brick sitting in my TV room.

The EXE file contains a directory "T-TDT5DEUC" which itself contains a directory "image" which contains these files.
```
total 28704
drwx------ 2 xxxxxxxx xxxxxxxx    32768 Jun 24  2011 .
drwx------ 3 xxxxxxxx xxxxxxxx    32768 Apr 20 19:07 ..
-rw-r--r-- 1 xxxxxxxx xxxxxxxx  2658596 Mar 31  2011 appdata.img.sec
-rw-r--r-- 1 xxxxxxxx xxxxxxxx       20 Mar 31  2011 appdata.img.sec.cmac
-rw-r--r-- 1 xxxxxxxx xxxxxxxx        0 Mar 31  2011 appdata.img.sec.cs
-rw-r--r-- 1 xxxxxxxx xxxxxxxx        0 Mar 31  2011 appdata.img.sec.vs
-rw-r--r-- 1 xxxxxxxx xxxxxxxx 26394916 Mar 31  2011 exe.img.sec
-rw-r--r-- 1 xxxxxxxx xxxxxxxx       20 Mar 31  2011 exe.img.sec.cmac
-rw-r--r-- 1 xxxxxxxx xxxxxxxx        0 Mar 31  2011 exe.img.sec.cs
-rw-r--r-- 1 xxxxxxxx xxxxxxxx        0 Mar 31  2011 exe.img.sec.vs
-rw-r--r-- 1 xxxxxxxx xxxxxxxx       18 Mar 31  2011 info.txt
-rw-r--r-- 1 xxxxxxxx xxxxxxxx        7 Mar 31  2011 major_version
-rw-r--r-- 1 xxxxxxxx xxxxxxxx        6 Mar 31  2011 minor_version
-rw-r--r-- 1 xxxxxxxx xxxxxxxx        0 Mar 31  2011 rocommon.img
-rw-r--r-- 1 xxxxxxxx xxxxxxxx       47 Mar 31  2011 validinfo.txt
-rw-r--r-- 1 xxxxxxxx xxxxxxxx       44 Mar 31  2011 version_info.txt
```

Has anybody here done a firmware upgrade on a Samsung TV?

---

### Post by hamishmb on 2014-04-20
If you have WINE, you can probably extract the firmware on that as if you were using windows, with a little luck :)

Hamish

---

### Post by Keith_Beef on 2014-04-21
> **hamishmb said:**
> If you have WINE, you can probably extract the firmware on that as if you were using windows, with a little luck :)

Hamish

Thanks for the idea.

I used WINE and got almost the same result, but not quite. Here's the list of the archive unpacked using WINE.

```

total 48960
drwx------ 2 xxxxxxxx xxxxxxxx    32768 Jun 24  2011 .
drwx------ 3 xxxxxxxx xxxxxxxx    32768 Jun 24  2011 ..
-rw-r--r-- 1 xxxxxxxx xxxxxxxx  2658596 Mar 31  2011 appdata.img.sec
-rw-r--r-- 1 xxxxxxxx xxxxxxxx       20 Mar 31  2011 appdata.img.sec.cmac
-rw-r--r-- 1 xxxxxxxx xxxxxxxx      256 Mar 31  2011 appdata.img.sec.cs
-rw-r--r-- 1 xxxxxxxx xxxxxxxx      256 Mar 31  2011 appdata.img.sec.vs
-rw-r--r-- 1 xxxxxxxx xxxxxxxx 26394916 Mar 31  2011 exe.img.sec
-rw-r--r-- 1 xxxxxxxx xxxxxxxx       20 Mar 31  2011 exe.img.sec.cmac
-rw-r--r-- 1 xxxxxxxx xxxxxxxx      256 Mar 31  2011 exe.img.sec.cs
-rw-r--r-- 1 xxxxxxxx xxxxxxxx      256 Mar 31  2011 exe.img.sec.vs
-rw-r--r-- 1 xxxxxxxx xxxxxxxx       18 Mar 31  2011 info.txt
-rw-r--r-- 1 xxxxxxxx xxxxxxxx        7 Mar 31  2011 major_version
-rw-r--r-- 1 xxxxxxxx xxxxxxxx        6 Mar 31  2011 minor_version
-rw-r--r-- 1 xxxxxxxx xxxxxxxx 20611072 Mar 31  2011 rocommon.img
-rw-r--r-- 1 xxxxxxxx xxxxxxxx       47 Mar 31  2011 validinfo.txt
-rw-r--r-- 1 xxxxxxxx xxxxxxxx       44 Mar 31  2011 version_info.txt

```

There are a few small, but possibly important differences in some file sizes.

The following files have a size of zero when extracted using Archive Manager, while they have a size of 256 when extracted using WINE:
```
-rw-r--r-- 1 xxxxxxxx xxxxxxxx        0 Mar 31  2011 appdata.img.sec.cs
-rw-r--r-- 1 xxxxxxxx xxxxxxxx        0 Mar 31  2011 appdata.img.sec.vs

-rw-r--r-- 1 xxxxxxxx xxxxxxxx        0 Mar 31  2011 exe.img.sec.cs
-rw-r--r-- 1 xxxxxxxx xxxxxxxx        0 Mar 31  2011 exe.img.sec.vs
```

But most importantly, one file has a size of zero when extracted using Archive Manager, but a size of **20611072** when extracted using WINE:

```
-rw-r--r-- 1 xxxxxxxx xxxxxxxx        0 Mar 31  2011 rocommon.img
```

---

### Post by sdowney717 on 2014-04-21
If your real concerned, use a windows PC to unpack.
Public library, work, home of friend should have one.

---

### Post by Keith_Beef on 2014-04-21
> **sdowney717 said:**
> If your real concerned, use a windows PC to unpack.
Public library, work, home of friend should have one.

:rolleyes:

I'll call a few friends, then, and tell them that according to some random guy on a forum they should all have computer'se capable of unpacking my Samsung firmware, eh?

---

### Post by Mark Phelps on 2014-04-21
> hey should all have computer'se capable of unpacking my Samsung firmware, eh? 

Being sarcastic doesn't help!

What you're asking your friend to do is run a self-extracting archive -- since such a file can't run in Linux and may not run reliably in Wine.  The fact that it includes Samsung firmware is irrelevant!

---

### Post by Keith_Beef on 2014-04-21
> **Mark Phelps said:**
> Being sarcastic doesn't help!

What you're asking your friend to do is run a self-extracting archive -- since such a file can't run in Linux and may not run reliably in Wine.  The fact that it includes Samsung firmware is irrelevant!

OK, I agree that the fact that it is Samsung firmware is not relevent. What **is** relevent is that this is a self-extracting archive for DOS or Windows.

Neither you nor "sdowney717" seem to have understood that the basic question of "how can I unpack this on a Linux computer" goes back to what many people consider as being at the very root of **why we run Linux**: **to have a computing environment that sets us free of reliance on proprietary operating systems and applications**.

If every time you run into a problem you just run to a friend and say "please run this Windows program for me", well you may as well just pack in the whole Linux thing and go back to Windows for you home set-up.

I didn't intend for this thread to turn into a discussion of the basic philosophy of the difference between free and open software on the one hand and proprietary software on the other hand. I went through all those arguments almost fifteen years ago. This is neither the time nor the place for it, so let's please **stay on topic**.

---

### Post by steeldriver on 2014-04-21
The **non-free** version of unrar (package unrar-nonfree - from multiverse) will unpack SFX Windows self-extracting archives, and appears to give the 'correct' file sizes:

```

$ unrar x ~/Downloads/T-TDT5DEUC.exe 

UNRAR 4.00 beta 3 freeware      Copyright (c) 1993-2010 Alexander Roshal


Extracting from /home/xxxxxxx/Downloads/T-TDT5DEUC.exe

;The comment below contains SFX script commands

Title=How to prepare the USB memory Drive
Text
{
<HTML>
    <HEAD>
        <TITLE>Samsung Enterprise Portal mySingle</TITLE>
.
.
.
</HTML>

}


Creating    T-TDT5DEUC                                                OK
Creating    T-TDT5DEUC/image                                          OK
Extracting  T-TDT5DEUC/image/appdata.img.sec                          OK 
Extracting  T-TDT5DEUC/image/appdata.img.sec.cmac                     OK 
Extracting  T-TDT5DEUC/image/appdata.img.sec.cs                       OK 
Extracting  T-TDT5DEUC/image/appdata.img.sec.vs                       OK 
Extracting  T-TDT5DEUC/image/exe.img.sec                              OK 
Extracting  T-TDT5DEUC/image/exe.img.sec.cmac                         OK 
Extracting  T-TDT5DEUC/image/exe.img.sec.cs                           OK 
Extracting  T-TDT5DEUC/image/exe.img.sec.vs                           OK 
Extracting  T-TDT5DEUC/image/info.txt                                 OK 
Extracting  T-TDT5DEUC/image/major_version                            OK 
Extracting  T-TDT5DEUC/image/minor_version                            OK 
Extracting  T-TDT5DEUC/image/rocommon.img                             OK 
Extracting  T-TDT5DEUC/image/validinfo.txt                            OK 
Extracting  T-TDT5DEUC/image/version_info.txt                         OK 
All OK

```

```

$ ls -l T-TDT5DEUC/image/
total 48552
-rw-rw-r-- 1 xxxxxxx xxxxxxx  2658596 Mar 31  2011 appdata.img.sec
-rw-rw-r-- 1 xxxxxxx xxxxxxx       20 Mar 31  2011 appdata.img.sec.cmac
-rw-rw-r-- 1 xxxxxxx xxxxxxx      256 Mar 31  2011 appdata.img.sec.cs
-rw-rw-r-- 1 xxxxxxx xxxxxxx      256 Mar 31  2011 appdata.img.sec.vs
-rw-rw-r-- 1 xxxxxxx xxxxxxx 26394916 Mar 31  2011 exe.img.sec
-rw-rw-r-- 1 xxxxxxx xxxxxxx       20 Mar 31  2011 exe.img.sec.cmac
-rw-rw-r-- 1 xxxxxxx xxxxxxx      256 Mar 31  2011 exe.img.sec.cs
-rw-rw-r-- 1 xxxxxxx xxxxxxx      256 Mar 31  2011 exe.img.sec.vs
-rw-rw-r-- 1 xxxxxxx xxxxxxx       18 Mar 31  2011 info.txt
-rw-rw-r-- 1 xxxxxxx xxxxxxx        7 Mar 31  2011 major_version
-rw-rw-r-- 1 xxxxxxx xxxxxxx        6 Mar 31  2011 minor_version
-rw-rw-r-- 1 xxxxxxx xxxxxxx 20611072 Mar 31  2011 rocommon.img
-rw-rw-r-- 1 xxxxxxx xxxxxxx       47 Mar 31  2011 validinfo.txt
-rw-rw-r-- 1 xxxxxxx xxxxxxx       44 Mar 31  2011 version_info.txt

```

HOWEVER afaik the exe.img.sec file is still encrypted - so unless you have the key it probably isn't going to help you much

---

### Post by Keith_Beef on 2014-04-21
> **steeldriver said:**
> The **non-free** version of unrar (package unrar-nonfree - from multiverse) will unpack SFX Windows self-extracting archives, and appears to give the 'correct' file sizes:

HOWEVER afaik the exe.img.sec file is still encrypted - so unless you have the key it probably isn't going to help you much

Thanks for that.

The file sizes look like those that I got from WINE. If the image file is encrypted by some key, maybe the key is in the TV; then the TV can use the key to decrypt the image before flashing it to its EEPROM. 

I've got a ticket open with Samsung about this question, too.

---

