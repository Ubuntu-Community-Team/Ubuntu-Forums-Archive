---
title: "Full screen Terminal when booting (help!)"
date: 2024-07-30
forum: General Help
---

### Post by rbscairns on 2024-07-30
My laptop is dual boot, Windows 10 and Ubuntu 22.04. Today in Ubuntu I was playing around deleting some files. When I rebooted there was no GUI. A full-screen Terminal was displayed asking for my user name and then my password. This I entered but the screen remained in Terminal - no GUI. My thoughts are that I probably deleted something that I shouldn't have.

In Ubuntu I use Duplicity to backup daily and the latest backup was performed about 10 hours before I lost access to Ubuntu's GUI. Is there any way to restore my Ubuntu GUI? I would rather not have to reinstall Ubuntu and set it all up again with all my wants/needs.

---

### Post by ajgreeny on 2024-07-30
"Deleting some files" as you put it is no help to us.
What were those files and where were they?

If they were in your home folder there is more chance we can get you back to a full GUI; if they were in your root filesystem things may be more difficult but what we need is more detailed information.

---

### Post by currentshaft on 2024-07-30
> **rbscairns said:**
> My laptop is dual boot, Windows 10 and Ubuntu 22.04. Today in Ubuntu I was playing around deleting some files. When I rebooted there was no GUI. A full-screen Terminal was displayed asking for my user name and then my password. This I entered but the screen remained in Terminal - no GUI. My thoughts are that I probably deleted something that I shouldn't have.

In Ubuntu I use Duplicity to backup daily and the latest backup was performed about 10 hours before I lost access to Ubuntu's GUI. Is there any way to restore my Ubuntu GUI? I would rather not have to reinstall Ubuntu and set it all up again with all my wants/needs.

Run "startx" and see what happens.

---

### Post by rbscairns on 2024-07-30
All file deletions wewre performed within Synaptic Package Manage, thinking this would be pretty safe. I was trying to delete all packages associated with OpenShot and Firefox.

---

### Post by rbscairns on 2024-07-30
> **currentshaft said:**
> Run "startx" and see what happens.

I did as you suggested and got
[CENTER][IMG]https://i.imgur.com/HYxczNH.jpg[/IMG][/CENTER]

Then pressing enter, this was displayed
[CENTER][IMG]https://i.imgur.com/enmwSJl.jpg[/IMG][/CENTER]

---

### Post by currentshaft on 2024-07-30
> **rbscairns said:**
> I did as you suggested and got
[CENTER][IMG]https://i.imgur.com/HYxczNH.jpg[/IMG][/CENTER]

Then pressing enter, this was displayed
[CENTER][IMG]https://i.imgur.com/enmwSJl.jpg[/IMG][/CENTER]

Try "sudo startx" and if that fails, check /var/log/Xorg.0.log for errors.

---

### Post by rbscairns on 2024-07-30
> **currentshaft said:**
> Try "sudo startx" and if that fails, check /var/log/Xorg.0.log for errors.

I tried sudo startx and got a similar result:
[CENTER][IMG]https://i.imgur.com/Jrowmm3.jpg[/IMG][/CENTER]

Unfortunately I do not know how to view the /var/log/Xorg.0.log file without access to the GUI.

---

### Post by currentshaft on 2024-07-31
less /var/log/Xorg.0.log

page up/down and arrow keys to navigate, q to quit

Also try "sudo apt install --reinstall xorg"

---

### Post by rbscairns on 2024-07-31
> **currentshaft said:**
> less /var/log/Xorg.0.log

page up/down and arrow keys to navigate, q to quit

Also try "sudo apt install --reinstall xorg"

```
less /var/log/Xorg.0.log
``` worked. The following line markings were listed:

[INDENT](--) probed = 2 listings
(**) from config file = 71 listings approx.
(==) default setting = 26 listings
(++) from command line = 0 listings
(!!) notice = 0 listings
(II) informational = balance of listings
(WW) warning = 5 listings
(EE) error = 0 listings
(NI) not implemented = 0 listings
(??) unknown = 0 listings[/INDENT]

What information should I be providing from the Xorg.0.log file?

---

### Post by ajgreeny on 2024-07-31
Have a look at all the lines marked WW, ie, the warnings.
You have no errors listed so there is nothing obvious so far.

---

### Post by rbscairns on 2024-07-31
> **ajgreeny said:**
> Have a look at all the lines marked WW, ie, the warnings.
You have no errors listed so there is nothing obvious so far.

The five (WW) warnings are shown in this screen photo:
[CENTER][IMG]https://i.imgur.com/YG8ha03.jpg[/IMG][/CENTER]

They all relate to /usr/share/fonts/X11/

I hope this helps. I really appreciate the help that I am getting here.

---

### Post by currentshaft on 2024-07-31
sudo apt install --reinstall fontconfig fontconfig-config xorg

---

### Post by rbscairns on 2024-07-31
> **currentshaft said:**
> sudo apt install --reinstall fontconfig fontconfig-config xorg

I performed the ```
sudo install --reinstall fontconfig fontconfig-config xorg
``` and all appeared to work. I then examined the Xorg.0.log again and the (WW) warnings were still displayed.

I need to prepare for work now and will return in about 8 hours.

---

### Post by rbscairns on 2024-08-01
Anyone?

---

### Post by ajgreeny on 2024-08-01
I have just noticed that you used synaptic to "remove the files" as you called them, though they were packages, not just files.

From your full screen terminal run command ```
sudo apt install ubuntu-desktop
``` and you may find you get back to a GUI.

Apt, dpkg and synaptic keep a record of all packages added or removed so you should be able to find the list of packages you removed from the log files.
See what output you get from command ```
grep -i " remove " /var/log/dpkg.log.1 /var/log/dpkg.log
```
It should show a list of dates and packages removed which may give you some clue of what needs to be reinstalled, all of which you can do from the full screen terminal using command ```
sudo apt install packagename1 packagename2 etc etc
```
Just list the packagenames with no punctuation marks and you may be able to get back to a full GUI

---

### Post by rbscairns on 2024-08-02
> **ajgreeny said:**
> I have just noticed that you used synaptic to "remove the files" as you called them, though they were packages, not just files.

From your full screen terminal run command ```
sudo apt install ubuntu-desktop
``` and you may find you get back to a GUI.

Apt, dpkg and synaptic keep a record of all packages added or removed so you should be able to find the list of packages you removed from the log files.
See what output you get from command ```
grep -i " remove " /var/log/dpkg.log.1 /var/log/dpkg.log
```
It should show a list of dates and packages removed which may give you some clue of what needs to be reinstalled, all of which you can do from the full screen terminal using command ```
sudo apt install packagename1 packagename2 etc etc
```
Just list the packagenames with no punctuation marks and you may be able to get back to a full GUI

@ajgreeny you arev a lifesaver! Installing then ubuntu-desktop brought my GUI back. I cannot thank you enough for your guidance.

I will now look into the log file.

---

