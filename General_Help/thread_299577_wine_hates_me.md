---
title: "wine hates me"
date: 2006-11-14
forum: General Help
---

### Post by TheRingmaster on 2006-11-14
I have installed wine from the budget dedicated's repositories (didn't work), I have installed wine from automatix (doesn't work). wine in both cases doesn't automatically create a "C:/" drive, so I have to manually create one through winecfg. still doesn't work. why does wine hate me so much???

these are all the errors it gives me (in terminal)

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/petey', starting in the Windows directory.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\petey\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\petey\\Desktop"'.
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\petey\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\petey\\My Documents"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\petey\\My Pictures"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\petey\\My Music"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\petey\\My Video"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\petey\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\petey\\Desktop"'.
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '../drive_c'

---

### Post by justin whitaker on 2006-11-14
> **TheRingmaster said:**
> I have installed wine from the budget dedicated's repositories (didn't work), I have installed wine from automatix (doesn't work). wine in both cases doesn't automatically create a "C:/" drive, so I have to manually create one through winecfg. still doesn't work. why does wine hate me so much???

I don't know if WINE creates the fake C: drive automatically, since I always run winecfg immediately after installing.

The fake C: drive is hidden. Enable hidden files, and it should be there. 

Crossover Office and Cedega both create fake C: drives automatically.

Edit:

That looks like a permissions issue. Are you installing as user, or root?

---

### Post by TheRingmaster on 2006-11-14
no, the c:/ drive is not there

Yes, I installed as root

---

### Post by nikhilk on 2006-11-14
Most users will be installing a package as root (or sudo), that does not matter as the fake "C:" drive is created per user in his home directory.
Are you sure you have not attempted running winecfg as root previously and now running it as a normal user? In that case maybe it is a permissions problem. Why dont you check the permission of the fake "C:" drive to be sure?

---

### Post by TheRingmaster on 2006-11-14
I have tried installing libjack0.100.0-0, libjack0.100.0-dev, libjackasyn-dev, libjackasyn0 like this guy did [Wine ERRORS - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?t=286646&highlight=wine")

still no luck

Edit: when I do gksu winecfg everything looks perfect. The c:/ drive is showing and a Z:/ drive.

but when I just do winecfg, and click on the drives tab It tells me there is no C:/ drive

*going crazy*

---

### Post by TheRingmaster on 2006-11-14
> **nikhilk said:**
> Most users will be installing a package as root (or sudo), that does not matter as the fake "C:" drive is created per user in his home directory.
Are you sure you have not attempted running winecfg as root previously and now running it as a normal user? In that case maybe it is a permissions problem. Why dont you check the permission of the fake "C:" drive to be sure?
there is no c:/ drive in the /.wine folder (yes I have enabled nautilus to show hidden files)

---

### Post by nikhilk on 2006-11-14
> **TheRingmaster said:**
> 
Edit: when I do gksu winecfg everything looks perfect. The c:/ drive is showing and a Z:/ drive.

but when I just do winecfg, and click on the drives tab It tells me there is no C:/ drive

This is weird. Looks like the root has got wine properly configured for his. Just peek into the root user's ~/.wine directory, all things should be setup properly there.
In that case how about giving this a shot? Copy over the root's .wine directory to your home directory and then doing a
"sudo chown -R <you>:<you> ~/.wine"

---

### Post by TheRingmaster on 2006-11-14
I think I did it.

How do I test wine?

---

### Post by nikhilk on 2006-11-14
> **TheRingmaster said:**
> 
I think I did it.

How, through winecfg?
> **TheRingmaster said:**
> 
How do I test wine?

There are some pretested apps bundled with Wine e.g. "IrfanView". Just see if you can run them.

---

### Post by justin whitaker on 2006-11-14
Wine ships with notepad as well. Wine notepad and see if it runs.

---

### Post by scrooge_74 on 2006-11-14
> **nikhilk said:**
> This is weird. Looks like the root has got wine properly configured for his. Just peek into the root user's ~/.wine directory, all things should be setup properly there.
In that case how about giving this a shot? Copy over the root's .wine directory to your home directory and then doing a
"sudo chown -R <you>:<you> ~/.wine"

Last time I installed wine from repositories (I use WineHQ repository), i just had to go into command line from a normal use and type winecfg. And from there on install and configure things.

it is always at /home/user/.wine

and the fake drive is /home/user/.wine/drive_c/

---

### Post by TheRingmaster on 2006-11-14
> **nikhilk said:**
> This is weird. Looks like the root has got wine properly configured for his. Just peek into the root user's ~/.wine directory, all things should be setup properly there.
In that case how about giving this a shot? Copy over the root's .wine directory to your home directory and then doing a
"sudo chown -R <you>:<you> ~/.wine"
like this

---

### Post by TheRingmaster on 2006-11-14
> ** CD/DVD ~/.wine/dosdevices **

 This is where you go to enable use of your CD/DVD within wine. 
You can try to enable them via winecfg or winetools, but it does not always work. 
Perhaps it is easier to make a symbolic link: 
    [SIZE=-1][COLOR=black][IMG][/IMG]**Code:**[/COLOR][/SIZE]     [FONT=monospace][SIZE=-1]cd ~/.wine/dosdevices
ln -s /media/<CD/DVD mount point> f:[/SIZE][/FONT]
 
  
Use any letter you like, but I suggest you create a new link rather then using D: 
Once wine is configured, you can now install an application from CD: 
    [SIZE=-1][COLOR=black][IMG]http://frodubuntu.free.fr/images/file.png[/IMG]**Code:**[/COLOR][/SIZE]     [FONT=monospace][SIZE=-1]wine f:setup[/SIZE][/FONT]

is there an easier way of doing this?
[FONT=monospace][SIZE=-1][/SIZE][/FONT]

---

### Post by scrooge_74 on 2006-11-14
> **TheRingmaster said:**
> is there an easier way of doing this?
[FONT=monospace][SIZE=-1][/SIZE][/FONT]

in winecfg you can configure  each drive even folders to be drive letters as in DOS.

You should check if wine is giving your CDROM a letter and knows is a drive, it sometimes tells the system is just another hardrive and have to manually tell wine is a CDROM

---

### Post by TheRingmaster on 2006-11-14
> **scrooge_74 said:**
> in winecfg you can configure  each drive even folders to be drive letters as in DOS.

You should check if wine is giving your CDROM a letter and knows is a drive, it sometimes tells the system is just another hardrive and have to manually tell wine is a CDROM
could you tell me how to do this

---

### Post by cotcot on 2006-11-14
Why not using VMWare server instead of wine ?
See : [http://ubuntuforums.org/showthread.php?t=183209]("http://ubuntuforums.org/showthread.php?t=183209")
Works great

---

### Post by scrooge_74 on 2006-11-14
> **TheRingmaster said:**
> could you tell me how to do this

from command line
winecfg

go to the drives tab
pick your CDROM it may say autoselect, if not you can give it the option of CDROM, you are going to see options like network share, etc

if your drives does not appear you can use the option autodetect

---

### Post by scrooge_74 on 2006-11-14
> **cotcot said:**
> Why not using VMWare server instead of wine ?
See : [http://ubuntuforums.org/showthread.php?t=183209]("http://ubuntuforums.org/showthread.php?t=183209")
Works great

But ain't you suppose to have a valid (paid for) copy of XP?

---

