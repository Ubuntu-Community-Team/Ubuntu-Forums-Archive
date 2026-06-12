---
title: "firefox dump core"
date: 2008-03-19
forum: General Help
---

### Post by hbbk on 2008-03-19
hi

Brand new pb...:(

```
hbbk:~$ /usr/bin/firefox
Segmentation fault (core dumped)
hbbk:~$ /usr/bin/firefox -safe
Segmentation fault (core dumped)
hbbk:~$ mv .mozilla .mozilla.backup
hbbk:~$ /usr/bin/firefox
Segmentation fault (core dumped)
hbbk:~$ cat /etc/firefox/firefoxrc
# which /dev/dsp wrapper to use
FIREFOX_DSP="none"
```

I even did an aptitude remove then install and have no "exotic" stuff in my sources.list 

I installed "by hand" firefox from the mozilla.org tar.gz package and it works perfectly with my regular profile, so the pb do not come from my profile but from the ubuntu installation.
 
any help welcome please

---

### Post by Oreo on 2008-03-23
There are many posts about this, and none of the proposed solutions worked for me.

All of the above didn't work for me.

I found a temporary work-around at this post: [http://ubuntuforums.org/showthread.php?t=610488&highlight=firefox+segmentation](http://ubuntuforums.org/showthread.php?t=610488&highlight=firefox+segmentation)
The post is by Ellioo.

[INDENT]To accomplish the same in firefox on any ubuntu-family installation (for the record, I am currently on xubuntu-gutsy)

01. Launch Firefox.
02. Go to the Edit menu and select Preferences.
03. Select the Content tab.
04. In the "Fonts & colors" section, click on the Advanced button.
05. Specify the fonts you would like to use as the defaults, as well as their size.
06. Uncheck the checkbox "Allow pages to use their own fonts, instead of my selections above."
07. Restart Firefox

You should be free of the ubuntu.com/ubuntuforums.org crashes, however you won't be seeing any of the cool fonts the web designers used.[/INDENT]

My problem occurred after upgrading from Feisty to Gutsy. I have tried reinstalling Firefox, deleting my old profile, reinstalling mscorefonts, checking the chmod of the corefonts, etc. So far the above is the only thing I have found that allows me to use Firefox. I sure hope someone comes up with something that allows me to use the designer's fonts.

Oreo

---

