---
title: "Rosetta Stone will not recognize mounted iso"
date: 2008-04-06
forum: General Help
---

### Post by tefflox on 2008-04-06
According to the appsdb at [winehq.com]("http://winehq.com"), the working version I've installed of Rosetta Stone should work to flying colors.  The app starts and works just fine, but I am at a loss to secure the language pack.  In [acetoneISO]("http://www.acetoneiso.netsons.org/"), the disc reads mounted.  I've set the winecfg drive listing to ~/virtual-drives/1/ (and 2 and 3) as to where acetone mounts the cdrom.  Also troubling, mounting the cd twice, and again, results in losing control of the first and second virtual drives.  I am unable to delete the folders / files from the virtual-drives directories.

Here is the runtime for the standard output, as the RS software loads and terminates properly ---

```
jess@home:~/.wine/drive_c/Program Files/The Rosetta Stone/The Rosetta Stone$ wine TheRosettaStone.exe 
fixme:spoolsv:serv_main (0 (nil))
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a
fixme:font:CreateScalableFontResourceW (0,L"c:\\windows\\system32\\tmpFD600.FOT",L"C:\\windows\\temp\\AAX6d9.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"c:\\windows\\system32\\tmp4E600.FOT",L"C:\\windows\\temp\\AAX6e1.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"c:\\windows\\system32\\tmpEE600.FOT",L"C:\\windows\\temp\\AAX6e6.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"c:\\windows\\system32\\tmp8F600.FOT",L"C:\\windows\\temp\\AAX6f1.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"c:\\windows\\system32\\tmp40700.FOT",L"C:\\windows\\temp\\AAX6fd.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"c:\\windows\\system32\\tmpB0700.FOT",L"C:\\windows\\temp\\AAX707.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"c:\\windows\\system32\\tmp41700.FOT",L"C:\\windows\\temp\\AAX70d.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"c:\\windows\\system32\\tmpA1700.FOT",L"C:\\windows\\temp\\AAX717.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"c:\\windows\\system32\\tmp52700.FOT",L"C:\\windows\\temp\\AAX71d.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"c:\\windows\\system32\\tmpA2700.FOT",L"C:\\windows\\temp\\AAX728.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"c:\\windows\\system32\\tmp43700.FOT",L"C:\\windows\\temp\\AAX72c.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"c:\\windows\\system32\\tmpE7700.FOT",L"C:\\windows\\temp\\AAX775.tmp",(null)): stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:shell:DllCanUnloadNow stub
```

---

### Post by bulletxt on 2008-04-06
you can't delete files from a folder wich contains a mounted image. it is read only. if it can help, run "winecfg" and set $HOME/virtual-drives1 as a cdrom device and try again.

---

### Post by tefflox on 2008-04-07
Neither virtual drive 1 or 2 are mounted.
> you can't delete files from a folder wich contains a mounted image. [INDENT][[IMG]http://gravityway.com/media/rosettastone_wine_ubuntu-gutsy_sm.jpg[/IMG]]("http://gravityway.com/media/rosettastone_wine_ubuntu-gutsy.jpg")
[/INDENT]

---

### Post by Matthewslf on 2008-04-07
try this in terminal:

cd ~/.wine/dosdevices
rm d:
ln -s ~/virtual-drives/[drive number] d:

and once you are done with a disk, run the same code for another one.

You could always burn a real cd.

---

### Post by tefflox on 2008-04-07
Before I try your solution, it helps to note that I have burned a disc --- nor does RS recognize it...

UPDATE:[B]  [COLOR=DarkRed]Solution fails[COLOR=Black].
[/COLOR][/COLOR][/B]>  cd ~/.wine/dosdevices
rm d:
ln -s ~/virtual-drives/[drive number] d:

and once you are done with a disk, run the same code for another one.

---

### Post by tefflox on 2008-04-11
I still need help here.  I'm trying gmountiso, acetoneiso, and the kernel modprobe loop --- nothing works, not even the cdrom in the physical drive.

---

### Post by tefflox on 2008-04-14
Problem solved: I gave up and installed the whole language pack (26 languages).  It works fine with AcetoneISO2.  My advice, stay away from [FONT=Arial]**h33t**[/FONT]'s iso's at the moment.

---

