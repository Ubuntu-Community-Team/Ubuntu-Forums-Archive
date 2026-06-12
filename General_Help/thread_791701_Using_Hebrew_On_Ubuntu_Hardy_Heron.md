---
title: "Using Hebrew On Ubuntu Hardy Heron"
date: 2008-05-12
forum: General Help
---

### Post by OrcaWave on 2008-05-12
Could you perhaps tell me just how to install and use Hebrew on Hardy Heron?

I'm going to buy a Hebrew/English keyboard, do you think that it will be a problem installing a bi-lingual keyboard on Hardy Heron OS?

I want to use English as the *main* language, and then at times switch to Hebrew, so I can share in a couple of e-list's that use Hebrew, as well as English.

Will this be a problem, do you think?

Thanks a lot for your help.

---

### Post by YigalB on 2008-08-16
I have same problem: I just can't make Hebrew work.
try adding the following: it didn't work for me, maybe it will work for you.
Maybe someone will come with an answer for both of us:
sudo aptitude install language-pack-he && language-pack-he-base

In my case, the packages were already installed, but I still can't get the Hebrew to show up.

Good luck

---

### Post by Mgiacchetti on 2008-08-16
> **YigalB said:**
> I have same problem: I just can't make Hebrew work.
try adding the following: it didn't work for me, maybe it will work for you.
Maybe someone will come with an answer for both of us:
sudo aptitude install language-pack-he && language-pack-he-base

In my case, the packages were already installed, but I still can't get the Hebrew to show up.

Good luck

you should try

```
 sudo apt-get install language-pack-he language-pack-he-base language-support-he

```

```


michael@AMD-64:~$ sudo apt-get install language-pack-he language-pack-he-baseReading package lists... Done
Building dependency tree       
Reading state information... Done
[B]Recommended packages:
  language-support-he[/B]
The following NEW packages will be installed:
  language-pack-he language-pack-he-base
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 804kB of archives.
After this operation, 2445kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy-updates/main language-pack-he-base 1:8.04+20080527 [462kB]
Get:2 http://us.archive.ubuntu.com hardy-proposed/main language-pack-he 1:8.04+20080805 [342kB]
Fetched 804kB in 3s (208kB/s)                 
Selecting previously deselected package language-pack-he-base.
(Reading database ... 153663 files and directories currently installed.)
Unpacking language-pack-he-base (from .../language-pack-he-base_1%3a8.04+20080527_all.deb) ...
Selecting previously deselected package language-pack-he.
Unpacking language-pack-he (from .../language-pack-he_1%3a8.04+20080805_all.deb) ...
Replacing files in old package language-pack-he-base ...
Setting up language-pack-he (1:8.04+20080805) ...
Setting up language-pack-he-base (1:8.04+20080527) ...
Generating locales...
  he_IL.UTF-8... done
Generation complete.
 * Reloading GNOME Display Manager configuration...                              *** Changes will take effect when all current X sessions have ended.**
                                                                         [ OK ]



michael@AMD-64:~$ sudo apt-get install language-support-he
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]The following extra packages will be installed:
  aspell-he hspell language-support-fonts-he language-support-translations-he
  language-support-writing-he myspell-he openoffice.org-l10n-he ttf-sil-ezra[/B]
[B]Suggested packages:
  language-support-extra-he hunspell-dictionary-he myspell-dictionary-he
  openoffice.org-ctl-he openoffice.org-help-he openoffice.org-hyphenation-he
  openoffice.org2-thesaurus-he[/B]
The following NEW packages will be installed:
  aspell-he hspell language-support-fonts-he language-support-he
  language-support-translations-he language-support-writing-he myspell-he
  openoffice.org-l10n-he ttf-sil-ezra
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 2172kB of archives.
After this operation, 10.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hardy/main language-support-translations-he 1:8.04+20080407 [2102B]
Get:2 http://us.archive.ubuntu.com hardy-updates/main openoffice.org-l10n-he 1:2.4.1-1ubuntu2 [388kB]
Get:3 http://us.archive.ubuntu.com hardy/main aspell-he 1.0-0-1 [190kB]
Get:4 http://us.archive.ubuntu.com hardy/main ttf-sil-ezra 2.51-2 [200kB]
Get:5 http://us.archive.ubuntu.com hardy/main language-support-fonts-he 8.04+20080229 [1808B]
Get:6 http://us.archive.ubuntu.com hardy/main hspell 1.0-3 [568kB]
Get:7 http://us.archive.ubuntu.com hardy/main myspell-he 1.0-3 [818kB]
Get:8 http://us.archive.ubuntu.com hardy/main language-support-writing-he 8.04+20080214 [1980B]
Get:9 http://us.archive.ubuntu.com hardy/main language-support-he 1:8.04+20080229 [1956B]
Fetched 2172kB in 5s (413kB/s)                    
Selecting previously deselected package language-support-translations-he.
(Reading database ... 153759 files and directories currently installed.)
Unpacking language-support-translations-he (from .../language-support-translations-he_1%3a8.04+20080407_all.deb) ...
Selecting previously deselected package openoffice.org-l10n-he.
Unpacking openoffice.org-l10n-he (from .../openoffice.org-l10n-he_1%3a2.4.1-1ubuntu2_all.deb) ...
Selecting previously deselected package aspell-he.
Unpacking aspell-he (from .../aspell-he_1.0-0-1_all.deb) ...
Selecting previously deselected package ttf-sil-ezra.
Unpacking ttf-sil-ezra (from .../ttf-sil-ezra_2.51-2_all.deb) ...
Selecting previously deselected package language-support-fonts-he.
Unpacking language-support-fonts-he (from .../language-support-fonts-he_8.04+20080229_all.deb) ...
Selecting previously deselected package hspell.
Unpacking hspell (from .../archives/hspell_1.0-3_i386.deb) ...
Selecting previously deselected package myspell-he.
Unpacking myspell-he (from .../myspell-he_1.0-3_all.deb) ...
Selecting previously deselected package language-support-writing-he.
Unpacking language-support-writing-he (from .../language-support-writing-he_8.04+20080214_all.deb) ...
Selecting previously deselected package language-support-he.
Unpacking language-support-he (from .../language-support-he_1%3a8.04+20080229_all.deb) ...
Setting up openoffice.org-l10n-he (1:2.4.1-1ubuntu2) ...

Setting up language-support-translations-he (1:8.04+20080407) ...
Generating locales...
  he_IL.UTF-8... up-to-date
Generation complete.
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]

Setting up aspell-he (1.0-0-1) ...
aspell-autobuildhash: processing: he [he]

Setting up ttf-sil-ezra (2.51-2) ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-sil-ezra
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.

Setting up language-support-fonts-he (8.04+20080229) ...
Setting up hspell (1.0-3) ...
Setting up myspell-he (1.0-3) ...
Updating OpenOffice.org's dictionary list... done.

Setting up language-support-writing-he (8.04+20080214) ...
Generating locales...
  he_IL.UTF-8... up-to-date
Generation complete.
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]

Setting up language-support-he (1:8.04+20080229) ...

```

---

### Post by YigalB on 2008-08-16
Thanks - they were already installed.
Yet I tried it and there was nothing to update.


> **Mgiacchetti said:**
> you should try

```
 sudo apt-get install language-pack-he language-pack-he-base language-support-he

```


---

### Post by sam-c on 2008-08-16
> **YigalB said:**
> Thanks - they were already installed.
Yet I tried it and there was nothing to update.
Shmuel from Yaffo has found that Installing Ubuntu from Scratch with Hebrew
makes everything work with hebrew. &#1513;&#1489;&#1493;&#1506; &#1496;&#1493;&#1489;

---

### Post by YigalB on 2008-08-17
I can tell you the steps required, but they are not working for me, and I am frustrated. Maybe they will work for you though. I also use English as main language, and Hebrew as secondary:
1- Go to System->Administration->Language Support and add Hebrew
2- Go to System->Preferences->Keyboard
3- Press the "Layouts" tab
4- Press "Add" and add the Hebrew

This should work for you.
Switching - press both ALT keys.

Let me know id it helps.

Good luck


> **OrcaWave said:**
> Could you perhaps tell me just how to install and use Hebrew on Hardy Heron?

I'm going to buy a Hebrew/English keyboard, do you think that it will be a problem installing a bi-lingual keyboard on Hardy Heron OS?

I want to use English as the *main* language, and then at times switch to Hebrew, so I can share in a couple of e-list's that use Hebrew, as well as English.

Will this be a problem, do you think?

Thanks a lot for your help.

---

### Post by thedavidg on 2008-08-18
if u add hebrew to the keyboard
system>preferences>layout and add israel
it wasn't enogh - i had to change the 
layout options>layout switching to alt+shift
and then it works...

---

### Post by YigalB on 2008-08-18
Interesting suggestion.
I tried it and here is what happen:
- The keyboard indication did change between USA/ISR
- When in ISR mode, the cursor moved to the right side. Good start!
- When I pressed the keyboard - nothing was shown on screen :(

I got same behavior is I changed the language with my mouse via the GUI.

So I am still stuck.


> **thedavidg said:**
> if u add hebrew to the keyboard
system>preferences>layout and add israel
it wasn't enogh - i had to change the 
layout options>layout switching to alt+shift
and then it works...

---

### Post by Oriolo on 2008-10-14
One suggestion for you is that you go to System>Administration>Synaptic package manager, search for "hebrew" and "bidi" and install everything that seems relevant.
Good day.
Ariel

---

### Post by YigalB on 2008-10-14
Hi 

I did search and found almost 40 packages that sum up at 187MB.
Doesn't make sense to me.

Also, shouldn't it be more a systematic approach?
One I chose Hebrew, the OS should do the hard work for me, and not the other way around.

Thanks

---

### Post by YigalB on 2008-10-21
I would like to add that I did 2 trials to add Hebrew:
- in a computer that was installed with hebrew as main language from the beginning. At first at first i couldn't type Hebrew, until I changed the "both alts" into "alt+shift" - then it started working.
- in the other computer, where English was the main language, all methods failed.

My conclusion is that Hebrew is not well supported from versions 7.10 and above. Unfortunately, because the hebrew support can work on on certain installation process, and can NOT be added later on, we can't say that Ubuntu can be alternative for XP.

---

