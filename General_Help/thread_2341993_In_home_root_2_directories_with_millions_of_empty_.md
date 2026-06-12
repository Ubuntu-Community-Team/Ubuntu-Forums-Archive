---
title: "In /home root 2 directories with millions of empty files says clamscan -r /home"
date: 2016-11-02
forum: General Help
---

### Post by xenon3 on 2016-11-02
```


clamscan -r /home

...
/home/kingdom/bt4e2BN7gn/VBTYJS : Empty file
/home/kingdom/bt4e2BN7gn/ABCTYS : Empty file
/home/kingdom/bt4e2BN7gn/XYZVTJ : Empty file
...


```

Goes on without end, directories are visible in file explorer, directories are empty in file explorer or load very slow because it seems to be millions of empty files, directory properties also seems to count without end. I thought maybe CLAMTK and consequently clam (from clamscan from freshclam) are corrupt, so I did clean reinstall

CLAMTK hangs on one file scanned, properties seem to count #files without end, clamscan goes on without end with finding empty files in:

```


 /home/kingdom/bt4e2BN7gn/


```

Is this the newest hack or something, what could be the use for hackers to generate enormous amounts of empty files? To keep CLAMTK busy? So that it does not find the real virus (hack). Kind of protection of the hack or virus?

> **xenon3 said:**
> 

```

  
/home/kingdom/bt4e2BN7gn/


```

/kingdom/ is my login user name so /home/kingdom/ is a user "home directory" right in the /home root



PLEASE HELP! I'm worried that I'm under attack, however could be the OS that is corrupt

IF:
-system acts strange see if reboot helps
-system acts strange see if modem reset helps
-application does weird things see if clean uninstall / reinstall helps
-Bleach bit the whole system (all options as user and again as root), thoroughly virus scan whole computer with CLAMTK from GUI and CLAMSCAN from terminal, see if that helps
-otherwise rebuild whole computer (OS and applications) see if that helps
-otherwise buy new computer en start from scrap again

Finally ended (normally it takes only a couple of minutes)

```


----------- SCAN SUMMARY -----------
Known viruses: 5028026
Engine version: 0.99.2
Scanned directories: 6633
Scanned files: 3208010
Infected files: 0
Total errors: 2
Data scanned: 53260.07 MB
Data read: 35988.81 MB (ratio 1.48:1)
Time: 12169.679 sec (202 m 49 s)
kingdom@king-MS-7728:~$ 


```

---

### Post by Bucky Ball on 2016-11-06
Did you actually create the folder at /home/kingdom or has that magically appeared? *What were you doing immediately before this issue occurred?* Which release and flavour of Ubuntu? Ubuntu 16.04 or something else?

Guess this is telling us something.

```
Infected files: 0
```

Tried deleting everything in the folder 'kingdom/bt4e2BN7gn/' (or even the complete /bt4e2BN7gn/ folder) and rebooting? Do they reappear?

---

### Post by xenon3 on 2016-11-08
> **Bucky Ball said:**
> Did you actually create the folder at /home/kingdom or has that magically appeared? *What were you doing immediately before this issue occurred?* Which release and flavour of Ubuntu? Ubuntu 16.04 or something else?

Guess this is telling us something.

```
Infected files: 0
```

Tried deleting everything in the folder 'kingdom/bt4e2BN7gn/' (or even the complete /bt4e2BN7gn/ folder) and rebooting? Do they reappear?

I did NOT create the folder! OK than It appeared magically.

Last thing I did to the system was to install and run BleachBit (as user and as root), but I'm not sure if this was BEFORE, I do remember that for maybe a couple of weeks or a month CLAMTK got slower and slower and always hanged on a number scanned files for a long time 

```


kingdom@king-MS-7728:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty
kingdom@king-MS-7728:~$ 


```

I will try later to delete the folders and files. OK? Now I still have some kind of proof on my computer. I will wait your response and decide

BleachBit: [https://www.bleachbit.org/](https://www.bleachbit.org/) installation was with an installation UBUNTU ERROR but it was installed and seem to work, however now in SEARCH APPS somtimes 2 BleachBit icons and one "BleachBit as Root" icon. One of the plain BleachBit icons does not do anything.

Could be the whole BleachBit installation is corrupt = not properly installed?

---

### Post by xenon3 on 2016-11-09
> **Bucky Ball said:**
> 

Tried deleting everything in the folder 'kingdom/bt4e2BN7gn/' (or even the complete /bt4e2BN7gn/ folder) and rebooting? Do they reappear?



The in /home/kingdom millions of empty files containing directories can be deleted permanently, do not reappear after reboot. Can be removed from the Trash

There were also 2 of such directories (same name format) in /home/kingdom/.local/share/trash/files/ they immediately come back after delete with .2 attached, are in Trash bin but cannot be removed from Trash bin.

example:

./9tn1w97iXcl/

becomes ./9tn1w97iXcl.2/ after delete when they come back

once again ./9tn1w97iXcl.2.2/

etc.

TO YOU READERS: Just tell me if you think its corrupt  / damaged software or a new hackers tric.

I'm afraid someone is in my system [IMG]https://ubuntuforums.org/images/smilies/icon_sad.gif[/IMG] would be very strange that corrupt software is all of the sudden making millions of empty files

---

### Post by Habitual on 2016-11-10
You use(d) bleachbit?

---

### Post by xenon3 on 2016-11-10
> **Habitual said:**
> You use(d) bleachbit?

Yes

---

