---
title: "Mounted FAT Partition -  Program Files Directory is owned by Root"
date: 2005-07-21
forum: General Help
---

### Post by carlc on 2005-07-21
My final goal is to get Quicken to run with wine. However, I am having trouble with the program files directory remaining owned by Root.

Here is my Fstab entry:

/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

I am not sure what do from here. I thought about trying to change the folder permissions or ownership or group ownership but was not sure if this was the most efficient way because it seems like this should have been accomplished when it was mounted. 

Any advice would be greatly appreciated!

---

### Post by Omnios on 2005-07-21
I played around with setting up my vfat32 documents drive (primary partition) as my wine directory. It showed up in wine I thing as a cd lol though my wine was totaly dorked but could not install wine fake windows on it. Anyways hers a link of the post dealing with it.

 [http://ubuntuforums.org/showthread.php?t=49830](http://ubuntuforums.org/showthread.php?t=49830)

---

### Post by carlc on 2005-07-22
My problem is that I can not access my Program Files directory from the command prompt and wine does not find it. Here is what happens from the command prompt:

> carlc@blackbox13:~$ cd /media

carlc@blackbox13:/media$ cd windows

carlc@blackbox13:/media/windows$ ls

ALCxxx-06.log           dvd_burn      nvidia                     unrar2
autoexec.bat           hiberfil.sys  pagefile.sys               unrar3
boot.ini                io.sys        Program Files              windows
config.sys              msdos.sys     Recycled
Documents and Settings  ntdetect.com  System Volume Information
download                ntldr         unrar1

carlc@blackbox13:/media/windows$ cd Program Files

bash: cd: Program: No such file or directory

carlc@blackbox13:/media/windows$


So I am not sure if it is a folder permissions problem (if that is the case, I don't know what to do because I can not change permissions or ownership because it will not recognize the file name) or a problem with how the folder is named. I have tried different things like Program_Files but still can not access it from the command prompt.

---

### Post by Omnios on 2005-07-22
[QUOTE=carlc]My problem is that I can not access my Program Files directory from the command prompt and wine does not find it. Here is what happens from the command prompt:



So I am not sure if it is a folder permissions problem (if that is the case, I don't know what to do because I can not change permissions or ownership because it will not recognize the file name) or a problem with how the folder is named. I have tried different things like Program_Files but still can not access it from the command prompt.[/QUOTE]

 I found terminal will not recognise the spece between fienames such as Program Files or other filenames with spaces I got it to do it a very long time ago but could not recreate that trick later on. Think I used ProgramFiles instead but that does not seem to work now.

---

### Post by carlc on 2005-07-23
I got it to work by using quotes.

carlc@blackbox13:/media/windows$ cd "Program Files"

---

### Post by carlc on 2005-07-23
Now, I get this error:

carlc@blackbox13:~$ wine "/media/windows/Program Files/Quicken/qw.exe"

Invoking /usr/lib/wine/wine.bin /media/windows/Program Files/Quicken/qw.exe ...

err:module:import_dll Library MFC71.DLL (which is needed by L"Z:\\media\\windows \\Program Files\\Quicken\\qw.exe") not found

err:module:import_dll Library MSVCR71.dll (which is needed by L"Z:\\media\\windo ws\\Program Files\\Quicken\\qw.exe") not found

err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\windows\\ Program Files\\Quicken\\qw.exe" failed, status c0000135

Wine failed with return code 1
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset

---

