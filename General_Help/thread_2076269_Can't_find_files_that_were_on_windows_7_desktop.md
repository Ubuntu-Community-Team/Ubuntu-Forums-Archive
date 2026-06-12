---
title: "Can't find files that were on windows 7 desktop"
date: 2012-10-25
forum: General Help
---

### Post by emerill on 2012-10-25
I was running windows 7 and the system stopped loading up.  I am now able to run Ubuntu and want to transfer files off before I replace the hard drive.  Anyway, I found some of the files and transferred them off. There were a bunch of files on my windows desktop that are nowhere to be found.  I tried using the terminal window to copy the data to a new directory, but got mount denied because the volume is exclusively opened. 

Any help is greatly appreciated!

emeril l

theirartworkendures.wordpress.com

---

### Post by Bashing-om on 2012-10-25
emerill; Hi ! Welcome to the forum.

Maybe the windows partition containing the files you seek is not mounted, thus ubuntu can not see them...
However as the drive "might" be in a damaged state ...
I suggest access from the live cd...see if the file manager in the live cd environment can access the windows partition and see the wanted files ? (*file manager will mount the partitions if possible)
[INDENT]try'n to help <==BDQ

[/INDENT]

---

### Post by emerill on 2012-10-25
Hi,
I can't find my files!  It's crazy, I see the hard drive in the devices section.  I click users folder, but it is empty.

I thought this link would help me but it doesn't find /host (or perhaps I'm not searching for it correctly).  [http://ubuntuforums.org/showthread.php?t=914358](http://ubuntuforums.org/showthread.php?t=914358)

Anyway, I had some files on the windows 7 desktop and can't locate them now.

Any help is super appreciated!

emeril

---

### Post by emerill on 2012-10-25
I don't really know what you are referring to.  Total newbie over here.

---

### Post by CCgirl6690 on 2012-10-25
afaik . you must have root access to be able to see windows files  unless they are on another drive .

---

### Post by Frogs Hair on 2012-10-25
I think it is File System > Host > Users > Your User Folder > Desktop.

---

### Post by emerill on 2012-10-25
Hi,
there is no folder called host in the file system menu.  :confused:

---

### Post by Bashing-om on 2012-10-25
ok ..small steps ... my reference is an install cd
1. set bios to boot cd as 1st boot priority.
 2. boot up the install cd
 3. when booted to the install menu ...choose "try ubuntu"
4. boots (finally) to the desk top ->left side of screen is the launcher (column of icons) -> second from top is a folder icon
5. click on the folder icon -> nautilus file manager ...left pane list all the partitions the file manager recognizes
6. click on any ...see if you can find your files.
[INDENT]try'n to help <== BDQ
 
[/INDENT]

---

### Post by emerill on 2012-10-25
1. Thanks for you help!
2. Got into Nautilus, can see my hard drive.  lots of other files are there, but not things that were stored on the windows desktop.

---

### Post by emerill on 2012-10-25
> **CCgirl6690 said:**
> afaik . you must have root access to be able to see windows files  unless they are on another drive .

Can see some files, though not the ones that were loaded on the desktop.  
Easy way to get root access?

---

### Post by Frogs Hair on 2012-10-25
> **emerill said:**
> Hi,
there is no folder called host in the file system menu.  :confused:

If you are using Wubi there should be  .  As suggested there may be a permission problem.  ```
gksudo nautilus
```


The thread you linked is for a Wubi installation so if you are not using it the method won't apply.

---

### Post by Bashing-om on 2012-10-25
It has been many years since "windows" for me ...I no longer have the knowledge to navigate through the paths to "desktop files" in windows. 

Perhaps others will be able to come to your aid.

[INDENT]kind regards <==BDQ

[/INDENT]

---

### Post by emerill on 2012-10-25
> **Frogs Hair said:**
> If you are using Wubi there should be  .  As suggested there may be a permission problem.  ```
gksudo nautilus
```
The thread you linked is for a Wubi installation so if you are not using it the method won't apply.

Did the gksu nautilus.  Saw the root menu appear.  Not sure what to do from there.  

I am booting from a usb under "try ubuntu"

---

### Post by uzumakifahim on 2012-10-26
"Got into Nautilus, can see my hard drive.  lots of other files are there"

That means you can access your windows partition right now. Is that right? If you can access then rest of the things are piece of cake !!!

---

### Post by NikTh on 2012-10-26
Hi ,

if you want to give it a try from the terminal , then boot from Ubuntu CD , click "Try Ubuntu" , open a terminal (CTRL+ALT+T) and give the results of bellow commands 

```
sudo fdisk -l 
sudo lshw -businfo | grep scsi
```

Thanks

---

### Post by mcduck on 2012-10-26
> **emerill said:**
> 1. Thanks for you help!
2. Got into Nautilus, can see my hard drive.  lots of other files are there, but not things that were stored on the windows desktop.

The Desktop folders for Windows 7 are located in Users/*username*/Desktop so assuming the drive you mounted is the drive that was used as C:/ in Windows, that's where you should find your files...

---

### Post by Frogs Hair on 2012-10-26
If you are booting from a live USB  no Host file will appear in the file system. As I wrote that will only work if Ubuntu has been installed via the Windows Installer/Wubi.

I have not attempted to access my Windows partition from a live DVD or USB so I cant help with that.

---

### Post by emerill on 2012-10-26
> **mcduck said:**
> The Desktop folders for Windows 7 are located in Users/*username*/Desktop so assuming the drive you mounted is the drive that was used as C:/ in Windows, that's where you should find your files...


The Users file was empty, but just tried it again and this is what popped up:
all users
default
default user
public
desktop.ini

Clicked through these and still didn't find the files.

---

### Post by emerill on 2012-10-26
> **NikTh said:**
> Hi ,

if you want to give it a try from the terminal , then boot from Ubuntu CD , click "Try Ubuntu" , open a terminal (CTRL+ALT+T) and give the results of bellow commands 

```
sudo fdisk -l 
sudo lshw -businfo | grep scsi
```Thanks


this is a lot of code. how can I get it here without retyping it all?

---

### Post by NikTh on 2012-10-27
> **emerill said:**
> this is a lot of code. how can I get it here without retyping it all?

You can copy from terminal and paste it here by click on "New Reply".
Put the results between the brackets **[noparse]```
the results here
```[/noparse]** so can be easy to read. 

Thanks

---

### Post by newb85 on 2012-10-27
> **emerill said:**
> this is a lot of code. how can I get it here without retyping it all?

In the terminal, the keyboard shortcut for copy is Ctrl+Shift+C, and paste is Ctrl+Shift+V.

---

### Post by varunendra on 2012-10-28
> **emerill said:**
> The Users [COLOR=Red]**file was empty**[/COLOR], but just tried it again and this is what popped up:
all users
default
default user
public
desktop.ini

Clicked through these and still didn't find the files.Ouch!
First thing first- **DON't do anything that can WRITE on that partition !!**
If that 'folder' really appeared as a file initially, then even when it opened, had your user folder (with the same name as your login id in windows) missing, I doubt it has been corrupt and 'lost'. May be that's the reason why your windows installation failed in the first place.

Unless you or some tweaking tool moved it, it must have been there.

Accordingly, I'd suggest to use a data recovery tool to see if it can find your missing files. If you can afford a commercial software, I'd suggest GetDataBack for NTFS. You can use its trial version for free to see if it can find the lost folder (your user folder in /Users/<user-id>/Desktop) and its contents. If it can, you'll have to buy it to actually recover the found data. Alternatively, you can try PhotoRec which is a part of testdisk package. It is free and is available in software center. [PhotoRec step-by-step]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step") example with screenshots (I have personally seen testdisk / photorec succeed where even top grade commercial software fail sometimes).

---

### Post by howefield on 2012-10-28
Threads merged.

---

