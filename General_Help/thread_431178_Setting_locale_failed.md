---
title: "Setting locale failed"
date: 2007-05-02
forum: General Help
---

### Post by brim4brim on 2007-05-02
For most of the packages I install using apt-get/synaptic I get the following error:
> 
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB.UTF-8",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory


Can someone tell me how to fix this issue

---

### Post by dcstar on 2007-05-02
> **brim4brim said:**
> For most of the packages I install using apt-get/synaptic I get the following error:


Can someone tell me how to fix this issue

Do you have the "**locales**" package installed?, either install or re-install it and see if things change.

---

### Post by brim4brim on 2007-05-02
No still getting the error in first post after reinstall locales package.  I think its something to do with perl as these errors are occuring when installing perl packages/programs I think.

> 
Gtk-WARNING **: Unable to locate theme engine in module path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 67 <> line 1


as I just installed 3Ddesktop package and got this error.

When trying to use Man right now I also got this error:
> 
man: can't set the locale; make sure $LC_* and $LANG are correct


---

### Post by dcstar on 2007-05-02
> **brim4brim said:**
> No still getting the error in first post after reinstall locales package.  I think its something to do with perl as these errors are occuring when installing perl packages/programs I think.



as I just installed 3Ddesktop package and got this error.

When trying to use Man right now I also got this error:

Do you also have the various "GB" English packages installed? (and not just the US ones)

---

### Post by brim4brim on 2007-05-02
I switched back to system default there and when I type man, I still get the" man: can't set the locale; make sure $LC_* and $LANG are correct" error.

---

### Post by evaristegalois on 2007-05-25
I am having the same problem. A lot of programs depend on this, so I get a lot of error messages when running things from the command line, like this:

> cannot set lc_all to default locale: no such file or directory

> perl: warning: setting locale failed

et cetera. There is the suggestion to run

> export LC_ALL="en_US"

on the command line on [http://www.linuxquestions.org/questions/showthread.php?t=218622]("http://www.linuxquestions.org/questions/showthread.php?t=218622"). But it didn't help in my case. Here is the output of the command locale:

> LANG=en_CA.UTF-8
LANGUAGE=en_CA:en
LC_CTYPE="en_CA.UTF-8"
LC_NUMERIC="en_CA.UTF-8"
LC_TIME="en_CA.UTF-8"
LC_COLLATE="en_CA.UTF-8"
LC_MONETARY="en_CA.UTF-8"
LC_MESSAGES="en_CA.UTF-8"
LC_PAPER="en_CA.UTF-8"
LC_NAME="en_CA.UTF-8"
LC_ADDRESS="en_CA.UTF-8"
LC_TELEPHONE="en_CA.UTF-8"
LC_MEASUREMENT="en_CA.UTF-8"
LC_IDENTIFICATION="en_CA.UTF-8"
LC_ALL=


(CA stands for Canada as opposed to US, but that's not the problem. I already checked into that, plus everything worked just fine for years until just a couple of days ago when I installed gocr -- I don't know if that caused the problem). Here is /etc/environment:

> PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_CA.UTF-8"
LANGUAGE="en_CA:en"


Your help would be appreciated by a lot of people, I guess, because there are a lot of entries on quite a few forums, and nowhere is this problem satisfactorily settled for anyone.

--evaristegalois

---

### Post by brim4brim on 2007-05-25
Sorry, I can't help, I just did a clean install to get rid of it.

---

### Post by NT4usB on 2007-05-26
I got it too...```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```I'm pretty sure it has to do with my install of MythTV 0.20 on Dapper using some packages from Edgy.

---

### Post by brim4brim on 2007-05-26
My issue was caused because I was installing Network Manager but didn't have a network connection up to then so I was downloading the packages required from [http://packages.ubuntu.com](http://packages.ubuntu.com) and installing them in Ubuntu from there.

Something got broken along the way.  Maybe seeing what packages these two programs have in common, might help you.  I was installing Network Manager from Edgy packages on Dapper.

---

### Post by NT4usB on 2007-05-26
Here's the steps I took to install 0.20 and break locales.
[http://ubuntuforums.org/showpost.php?p=1586072&postcount=310](http://ubuntuforums.org/showpost.php?p=1586072&postcount=310)

---

### Post by evaristegalois on 2007-05-26
It seems this problem occurs not infrequently when packages are installed offline. In any case, your link points out how to install mythtv under edgy but it doesn't at all address the issue of how to fix the locale problem. Everytime I enter a command or run a program on the command line I get these error messages. Other programs who somehow depend on stable locales have quit working (e.g. dvd::rip). 

So it would still be great if someone who knows how to fix locales when they break in this way could help. Otherwise I'll have to do a reinstall as well -- how dreadful!

--evaristegalois

---

### Post by NT4usB on 2007-05-26
> **evaristegalois said:**
> It seems this problem occurs not infrequently when packages are installed offline. In any case, your link points out how to install mythtv under edgy but it doesn't at all address the issue of how to fix the locale problem.
Read it again. I said:
*Here's the steps I took to install 0.20 and **_*break locales.**_
Translation: This is what I did and the result was broken locales.
(all conducted online, btw...)
Maybe someone can look at these steps and see which one might have broken it.

 > **evaristegalois said:**
> Everytime I enter a command or run a program on the command line I get these error messages. Other programs who somehow depend on stable locales have quit working (e.g. dvd::rip). 
I get the error message too.
I haven't found anything that doesn't work because of locales. Since it is only a PVR, I don't do much else on it. I do rip and burn DVD's though, and they work fine.

> **evaristegalois said:**
> So it would still be great if someone who knows how to fix locales when they break in this way could help. Otherwise I'll have to do a reinstall as well -- how dreadful!

--evaristegalois

Fact is, if we could learn what's broke, we could fix it without reinstalling. Unlike Windows, there's very little that can't be fixed in Linux without resorting to reinstalling. The challenge is figuring out what to fix.

---

