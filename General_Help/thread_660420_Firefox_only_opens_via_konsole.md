---
title: "Firefox only opens via konsole"
date: 2008-01-06
forum: General Help
---

### Post by Scooter7 on 2008-01-06
Hi,

I'm using Kubuntu 7.10.   I installed Firefox via Adept.   However, it doesn't run unless I run this command in the konsole:

```
sudo firefox
```

I've tried modifying the menu entry to be sudo firefox, sudo firefox %u, and firefox, but none of these work, not even the default (firefox %u).

Any suggestions?

---

### Post by earobinson on 2008-01-06
well the weird thing is that only root is alound to run firfox, can you paste the output of ```
lrwxrwxrwx 1 root root 22 2007-12-05 09:44 /usr/bin/firefox -> ../lib/firefox/firefox
```

---

### Post by Scooter7 on 2008-01-06
> bash: ../lib/firefox/firefox: No such file or directory

...is the output.

---

### Post by p_quarles on 2008-01-06
Guessing he meant the output of:
```
ls -l /usr/bin/firefox
```
That said, the output should like like what earobinson posted.

---

### Post by Scooter7 on 2008-01-06
Yes, that is the output.   So I don't /think/ it's a path problem.

---

### Post by p_quarles on 2008-01-06
Can you post the output you got, just so we can doublecheck the exact settings?

Anyway, one thing you might try is running this:
```
sudo dpkg-reconfigure firefox
```
Also, it's potentially hazardous to use "sudo" for running graphical applications. The better practice is to use "gksudo" (Gnome and Xfce) or in this case "kdesu" (for KDE).

---

### Post by Scooter7 on 2008-01-06
Running it with kdesu works fine, but I don't want to have to enter my password every time I start my browser, as I open it quite often.

Here is the output of 'ls -l /usr/bin/firefox':

```
lrwxrwxrwx 1 root root 22 2008-01-06 04:58 /usr/bin/firefox -> ../lib/firefox/firefox
```

---

### Post by p_quarles on 2008-01-06
> **Scooter7 said:**
> Running it with kdesu works fine, but I don't want to have to enter my password every time I start my browser, as I open it quite often.

Here is the output of 'ls -l /usr/bin/firefox':

```
lrwxrwxrwx 1 root root 22 2008-01-06 04:58 /usr/bin/firefox -> ../lib/firefox/firefox
```
I understand, and actually you *shouldn't *run the web browser as root. That's a pretty big security risk. 

Did the dpkg-reconfigure command I gave change anything?

---

### Post by Scooter7 on 2008-01-06
No, it didn't, at least not as far as I can tell.   I did, however, get this when I ran the command:

> Please restart any running Firefoxes, or you will experience problems.
Warning: something created compreg.dat!
Your system was affected by this bug: [https://launchpad.net/bugs/30791](https://launchpad.net/bugs/30791)
compreg.dat has now been removed again, which should fix the symptoms.

---

### Post by p_quarles on 2008-01-06
That's a pretty old bug, and I don't see anything there to indicate it affects Firefox 2. 

I have no idea what's going on here. The best I can tell you is to give [Swiftweasel]("http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717") a try. It's a recompiled version of Firefox that's been optimized for Debian Linux-based systems (including Ubuntu). If you need any help choosing the correct package for your CPU, just ask.

---

### Post by Scooter7 on 2008-01-06
Thanks, I think I will try Swiftweasel.   And yeah, help with that would be appreciated.   My processor is a Intel Centrino Duo, 32-bit (i386?).

---

### Post by p_quarles on 2008-01-06
Centrino isn't the actual name of the processor, but just a marketing name for a combination of Intel products. To get the exact type of the processor, post the results of this command:
```
sudo lshw | grep CPU
```
I'm guessing it's a Core 2 Duo, in which case you'd want this Swiftweasel package:
[http://downloads.sourceforge.net/swiftweasel/swiftweasel-2.0.0.11_prescott_ubuntu-i386.deb?modtime=1196597863&big_mirror=0](http://downloads.sourceforge.net/swiftweasel/swiftweasel-2.0.0.11_prescott_ubuntu-i386.deb?modtime=1196597863&big_mirror=0)
If you get a different result, though, let me know and I'll look up the optimized package.

---

### Post by Scooter7 on 2008-01-06
This the output of the command:

> description: CPU
          product: Genuine Intel(R) CPU           T2300  @ 1.66GHz
             description: Logical CPU
             description: Logical CPU

I think I do indeed have a Core 2 Duo, though.   I would check Toshiba's website (the manufacturer), but they no longer list my model.   Seems like it's been replaced by the P200 (I have a Toshiba Satellite Pro P100).

---

### Post by p_quarles on 2008-01-06
Yeah, the T2300 is definitely a Core 2 Duo. Go for the Prescott version of Swiftweasel.

---

### Post by Scooter7 on 2008-01-07
The Swiftweasel installation seemed to go okay, but running it has the same results as with Firefox.   Running swiftweasel %u in the konsole outputs:

> esd: no process killed
cd: 71: can't cd to /home/vertimyst/.mozilla
cp: cannot stat `firefox': No such file or directory
mv: cannot stat `firefox': No such file or directory
mv: cannot stat `swiftweasel': No such file or directory
cd: 71: can't cd to /home/vertimyst/.mozilla/swiftweasel
awk: cannot open profiles.ini (No such file or directory)
mv: missing destination file operand after `tmp1'
Try `mv --help' for more information.
mkdir: cannot create directory `tmp2': File exists
cp: cannot stat `./tmp1/extensions': No such file or directory
cp: cannot stat `./tmp1/*': No such file or directory
mv: missing destination file operand after `tmp2'
Try `mv --help' for more information.

---

### Post by p_quarles on 2008-01-07
Hmm. Try backing up and then removing the Firefox config directory:
```
mv -r .mozilla/default firefox-config.bak
```
Then, run firefox or swiftweasel (without the %u, though -- that's not necessary) again. Any difference?

---

### Post by Scooter7 on 2008-01-07
That command gives me an error saying that -r is not a valid option... do you mean: ```
rm -r .mozilla/default firefox-config.bak
```?

---

### Post by p_quarles on 2008-01-07
Oops. Sorry. The "mv" command doesn't need the -r option, and apparently won't work with it. I didn't mean "rm", but you can use that if you make sure to back up the directory prior to doing so. (i.e., you don't want to lose your bookmarks).

---

### Post by Scooter7 on 2008-01-07
I've discovered that the .mozilla directory is locked, only available to the root user.   Changing permissions on the folder fixed my problem for both Firefox and Swiftweasel.  I find it odd that the folder was locked to begin with, though.

Anyway, thanks for your help. ;)

---

### Post by p_quarles on 2008-01-07
Cool. Glad I could help.

The .mozilla folder is *not* supposed to be locked out from the user under normal circumstances. The only thing I can think of here is that using "sudo" to run graphical applications can sometimes mess up permissions settings.

---

