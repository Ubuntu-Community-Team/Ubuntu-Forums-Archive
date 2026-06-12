---
title: "[SOLVED] MozBackup"
date: 2008-06-04
forum: General Help
---

### Post by ekmon1582 on 2008-06-04
How do I install this program? I've already downloaded the install file off the website.

---

### Post by geo909 on 2008-06-04
Did you try to find it on synaptic?

Sorry for not really answering your question, but if MozBackup is for backing up your firefox or thunderbird settings, that can be easily done by backing up (= copying somewhere) your /home/<yourusername>/.mozilla folder.

---

### Post by rraj.be on 2008-06-04
Just could you tell me the contents of the file.

I sthere any .deb file or something like .sh  

for example installer.sh

---

### Post by ekmon1582 on 2008-06-04
> **geo909 said:**
> Did you try to find it on synaptic?

Sorry for not really answering your question, but if MozBackup is for backing up your firefox or thunderbird settings, that can be easily done by backing up (= copying somewhere) your /home/<yourusername>/.mozilla folder.

Done it, I tried to copy my profile folders for Firefox and Thunderbird and paste them, but it doesn't work. For some reason, the system acts like the file was pasted there, but I see nothing.


> **rraj.be said:**
> Just could you tell me the contents of the file.

I sthere any .deb file or something like .sh  

for example installer.sh

The name of the install file is "MozBackup-1.4.8EN.exe" (w/out quotations).

---

### Post by leito666 on 2008-06-04
The version its only for linux,

From the web
"This program is freeware and works on Windows 98/ME/NT/2000/XP/2003/Vista"

---

### Post by rraj.be on 2008-06-04
Ubuntu doesnt know a valid formate as .exe.

its a windows installation file.

The best way for you is to go with synaptic package manager.

```
you cant install any exe files in ubuntu.

You should use some emulator like Wine to install exe files in ubuntu
```

see here for more details[www.winehq.org/]("www.winehq.org/")

---

### Post by ekmon1582 on 2008-06-04
> **leito666 said:**
> The version its only for linux,

From the web
"This program is freeware and works on Windows 98/ME/NT/2000/XP/2003/Vista"

Didn't notice that :oops:.

---

### Post by rraj.be on 2008-06-04
```
Note:

Not [COLOR="Red"]all[/COLOR] windows softwares can be emulated using wine.
```

To install wine 

open terminal

```
Applications-->administration-->terminal
```

It will ask for your password.
 Enter it.

Now type


```
sudo apt-get install wine
```

in terminal

---

### Post by geo909 on 2008-06-04
> **ekmon1582 said:**
> Done it, I tried to copy my profile folders for Firefox and Thunderbird and paste them, but it doesn't work. For some reason, the system acts like the file was pasted there, but I see nothing.


Didn't understand what you mean, sorry for my english..

MAYBE it's because it's a "hidden" file. Open nautilus in your /home/yourusername/ folder, press Ctrl+H and you'll see it.

Actually that's the way I keep backups of my settings and emails from firefox and thunderbird and it works fine.
I find it simpler than messing with wine.
 Just
```
cp -a /home/yourusername/.mozilla /home/yourusername/mozilla_BACKUP
```

---

### Post by ekmon1582 on 2008-06-04
I'll try that later, I seem to have lost my Thunderbird profile, so I'll hold off till I get it back. Thanks everyone for the help.

---

### Post by davegoodman on 2012-11-30
> **rraj.be said:**
> Ubuntu doesnt know a valid formate as .exe.

its a windows installation file.

The best way for you is to go with synaptic package manager.

```
you cant install any exe files in ubuntu.

You should use some emulator like Wine to install exe files in ubuntu
```

see here for more details[www.winehq.org/]("www.winehq.org/")
Sorry i know this is an old post just wanted too point out ... doesnt WINE stand for WINE is not an emulator ?? :biggrin:

---

