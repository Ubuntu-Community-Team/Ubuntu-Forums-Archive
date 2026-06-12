---
title: "Help me falsh my BIOS"
date: 2008-02-23
forum: General Help
---

### Post by orlox on 2008-02-23
Hi!

I'm trying to update my MOBO's BIOS to see if this helps me get to work my e-geforce 6200, 256 mb video card.

My video card is an ECS elitegrup P4M800PRO-m v1.0a.

I tried to follow this guide;

[HOWRO: Flash BIOS, the Ubuntu way]("http://ubuntuforums.org/showthread.php?t=318789")

But i got up to the point of "unzipping the exe file". The download for the biso come's with a   AFUWIN.EXE file, wich when I try to extract gives me:
```

pablo@ubuntu:/media/KINGSTON/070626S$ unzip AFUWIN.EXE 
Archive:  AFUWIN.EXE
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  AFUWIN.EXE may be a plain executable, not an archive
unzip:  cannot find zipfile directory in one of AFUWIN.EXE or
        AFUWIN.EXE.zip, and cannot find AFUWIN.EXE.ZIP, period.

```

I don't have windows so I can't try to update the bios by that way...

Any help????

---

### Post by wolfen69 on 2008-02-23
to get your BIOS to see your 6200, go into BIOS and go to integrated peripherals (or similar) and disable onboard video.

---

### Post by julian67 on 2008-02-23
> **orlox said:**
> Hi!

I'm trying to update my MOBO's BIOS to see if this helps me get to work my e-geforce 6200, 256 mb video card.

My video card is an ECS elitegrup P4M800PRO-m v1.0a.

I tried to follow this guide;

[HOWRO: Flash BIOS, the Ubuntu way]("http://ubuntuforums.org/showthread.php?t=318789")

But i got up to the point of "unzipping the exe file". The download for the biso come's with a   AFUWIN.EXE file, wich when I try to extract gives me:
```

pablo@ubuntu:/media/KINGSTON/070626S$ unzip AFUWIN.EXE 
Archive:  AFUWIN.EXE
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  AFUWIN.EXE may be a plain executable, not an archive
unzip:  cannot find zipfile directory in one of AFUWIN.EXE or
        AFUWIN.EXE.zip, and cannot find AFUWIN.EXE.ZIP, period.

```

I don't have windows so I can't try to update the bios by that way...

Any help????

**note:  AFUWIN.EXE may be a plain executable, not an archive**

It could be that. Looks to me that you have the bios flash utility from amibios and possibly the new BIOS ROM seperately from your motherboard manufacturer? So if you do already have the ROM then chances are you don't have an exe archive to unpack, but a regular executable so can simply proceed to section 3 point 3 of the howto.

---

### Post by orlox on 2008-02-23
> **julian67 said:**
> 
It could be that. Looks to me that you have the bios flash utility from amibios and possibly the new BIOS ROM seperately from your motherboard manufacturer? So if you do already have the ROM then chances are you don't have an exe archive to unpack, but a regular executable so can simply proceed to section 3 point 3 of the howto.

Yup, thought the same thing. I even have the rom file 070626S.ROM, the problem is I don't know  the instructions I need to do the flashing, wich are supossed to be found In a readme File wich isn't included...

The files I have from the manufacturer are:

```

pablo@ubuntu:/media/KINGSTON/070626S$ ls -l
total 1600
-rwx------ 1 pablo root 524288 2007-07-27 17:52 070626S.ROM
-r-x------ 1 pablo root 114600 2006-04-19 14:39 AFUDOS.EXE
-r-x------ 1 pablo root 389197 2006-04-19 14:41 AFUWIN.EXE
-rwx------ 1 pablo root 344350 2006-08-21 13:30 DOS Flash Utility User Guide.pdf
-r-x------ 1 pablo root 102400 2006-04-12 14:42 Ucoredll.dll
-r-x------ 1 pablo root   8736 2006-04-12 14:33 Ucoresys.sys
-r-x------ 1 pablo root   7840 2006-04-12 14:33 Ucorevxd.vxd
-r-x------ 1 pablo root   7936 2006-04-12 14:33 UCOREW64.SYS

```

---

### Post by Jerry N on 2008-02-23
Be afraid, be very afraid!  If you, or anything else, screws up your BIOS flashing process, your motherboard will become a paperweight.  Most of the time there is no way to recover unless you can find someone that can provide a new BIOS ROM that you can plug in.

Jerry

---

### Post by julian67 on 2008-02-23
> **orlox said:**
> Yup, thought the same thing. I even have the rom file 070626S.ROM, the problem is I don't know  the instructions I need to do the flashing, wich are supossed to be found In a readme File wich isn't included...

The files I have from the manufacturer are:

```

pablo@ubuntu:/media/KINGSTON/070626S$ ls -l
total 1600
-rwx------ 1 pablo root 524288 2007-07-27 17:52 070626S.ROM
-r-x------ 1 pablo root 114600 2006-04-19 14:39 AFUDOS.EXE
-r-x------ 1 pablo root 389197 2006-04-19 14:41 AFUWIN.EXE
-rwx------ 1 pablo root 344350 2006-08-21 13:30 DOS Flash Utility User Guide.pdf
-r-x------ 1 pablo root 102400 2006-04-12 14:42 Ucoredll.dll
-r-x------ 1 pablo root   8736 2006-04-12 14:33 Ucoresys.sys
-r-x------ 1 pablo root   7840 2006-04-12 14:33 Ucorevxd.vxd
-r-x------ 1 pablo root   7936 2006-04-12 14:33 UCOREW64.SYS

```

read the DOS Flash Utility User Guide.pdf you have and if needed try to find out more from [http://www.ami.com/support/bios.cfm]("http://www.ami.com/support/bios.cfm")

also try the support section of your motherboard manufacturer

---

### Post by orlox on 2008-02-23
Already read that, and it says to use windows to create a boot floppy disk, from wich you can  run afudos.exe

I'm trying to create a boot usb disk with freeDOS as said in this link:

[here is the link...]("http://www.tkarena.com/forums/via-epia-mini-itx-nano-itx-pico-itx-arena/35587-flashing-epia-sn.html")

but I can't get freeDOS to work, I only get a black screen that says freeDOS on the upper left corner...

---

### Post by CREEPING DEATH on 2008-02-23
Why are you screwing with the BIOS?  Unless it's defective (there were some GigaByte boards that REQUIRED reflash to keep working) then leave it alone.

CD

---

### Post by orlox on 2008-02-23
Already done... I made a boot CD with NERO including the afudos.exe and the .rom file. I then did thid:
> 
e:          (this was because the data of the cd was here)
afudos.exe the_name_of_the_rom.rom /p /b /n /c /x

And then the system restarted...Everything came back and I was able to get hardware acceleration working for a few minutes (a GREAT improvement though).

The only detail is...NOW I HAVE NO ETHERNET!!!:confused::confused::confused:

Well...guess I'll have to fix that now :P

---

### Post by orlox on 2008-02-23
:confused::confused::confused:

Weird thing...discovered that If i take a jumper of the mobo so the cmos is cleared, I recover my ethernet device. But, If I set the cmos again and restart, I lose it:confused::confused:

---

