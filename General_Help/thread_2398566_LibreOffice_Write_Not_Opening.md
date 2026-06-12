---
title: "LibreOffice Write Not Opening"
date: 2018-08-14
forum: General Help
---

### Post by electrosteam on 2018-08-14
Fresh install of Lubuntu 18.04.1 and LibreOffice 6.0.3.2 on an old Dell laptop with 2GB of RAM.


All the components of LO other than Write open correctly.
Write displays an opening window, then quits.


Did some searching and found one thread that fixed the problem by disabling Java and/or renaming the folder ~/.config/libreoffice as a backup.
Cannot track down that link now.


Just enquiring if anyone can confirm these solutions, or offer alternatives.


John

---

### Post by kc1di on 2018-08-14
what happens when  you issue this command in a terminal?```
libreoffice --writer
``` post any error messages you get.

---

### Post by electrosteam on 2018-08-14
Dave, thanks for the interest and suggestion
```

john@Bluebox:~$ libreoffice --writer


(soffice:1393): dbind-WARNING **: 07:22:38.280: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
john@Bluebox:~$ 

```

Got an opening window of LibreWriter, which cleared instantly and a dialogue box offering to recover a crashed file - which I declined this time.

Lubuntu was installed over the previous version with option selected to clear the hard drive, then backups installed and AbiWord used to access a document on the new install.
Subsequently LibreOffice was installed.

Perhaps AbiWord left a file as crashed.
There is a history of freezes on this machine, and it did so soon after the fresh install, a document may have been open at the time.

A couple of re-runs of the command differed in the (soffice:nnnn) number only, but the dialogue box did not appear.

John

---

### Post by ajgreeny on 2018-08-14
It does sound as if your configuration folder contains some corrupt files so I suggest you try the renaming of your current configuration folder as you mention in your original post.
You can do that with command ```
mv .config/libreoffice .config/libreoffice-backup
``` then restart LO-Writer.
A new config folder will be created and may allow you to get the writer program to work.

I have had problems in the past with LO or OOo created files opened with Abiword being corrupt when nest opening in LO bit it was a very long time ago and I've not seen that for several years.
Can you still open the corrupt file you mention using Abiword?  If so try saving that as a .doc file then see if you can open the new .doc file in LO and resave it as an .odt, then try opening this new .odt again in both LO and Abiword.

---

### Post by electrosteam on 2018-08-14
Al, tried that without success (using mv instead of mov).
```

john@Bluebox:~$ mv .config/libreoffice .config/libreoffice-backup
john@Bluebox:~$

```

After attempted Writer opening:
```

john@Bluebox:~$ ls .config/libreoffice-backup
4
john@Bluebox:~$ ls .config/libreoffice
4

```

You have prompted me into delving into the system operation, a good thing.
John

---

### Post by ajgreeny on 2018-08-15
Mea culpa!!

Whoops, sorry about that typo; I've no idea how that mistake got through as I've been using **mv** for 13 years.

---

