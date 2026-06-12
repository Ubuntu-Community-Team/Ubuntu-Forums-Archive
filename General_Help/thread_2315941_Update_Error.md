---
title: "Update Error"
date: 2016-03-03
forum: General Help
---

### Post by jooge on 2016-03-03
Hi folks, 

I tried updating via terminal and got this error at the end.

```
W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
```


Now I know that its the Chrome browser update that had the issue, but I was wondering how I can address this and fix it?

Thanks in advance.

---

### Post by QDR06VV9 on 2016-03-03
**EDIT> The last I heard is that google is still changing the source  for Apt with updates so you might want to keep this handy..If it happens  again.**

Linux: How To Fix Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release) (self.chrome)
[B]Credit to: darkfur93
[/B]
If you are using Chrome on Linux you may get a error saying "Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release) Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file) Some index files failed to download. They have been ignored, or old ones used instead." This is because 32-Bit Chrome builds has been discontinued.

If you are on Linux x64 enter this into the command line: **gksudo gedit /etc/apt/sources.list.d/google-chrome.list** place **[arch=amd64] **after deb and before http so the line now looks like this: 
```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```
Or to do it with out opening an text editor..run this in the terminal:
```
sudo sed -i -e 's/deb http/deb [arch=amd64] http/' "/etc/apt/sources.list.d/google-chrome.list"
```

_**If you are on Linux x32 you will need to uninstall chrome due to no more security updates will be offered. **_Your distribution may offer chromium-browser. Chromium will be updated by your linux distribution not by Google.
Source: [https://www.reddit.com/r/chrome/comments/48oje6/linux_how_to_fix_failed_to_fetch/](https://www.reddit.com/r/chrome/comments/48oje6/linux_how_to_fix_failed_to_fetch/)
Hope this helpful...

---

### Post by jooge on 2016-03-03
Awesome, Thanks for all the info. I do have a 64bit. I did your first recommendation. All appears to be good.

Thank you for your help runrickus. Take care bud.

---

### Post by QDR06VV9 on 2016-03-03
Thank You! Very Kind of you.
Glad I could be of assistance..:)
EDIT> The last I heard is that google is still changing the source for Apt with updates so you might want to keep this handy..If it happens again.
Google should be changing that behaviour soon.

---

### Post by jooge on 2016-03-03
Ok, thanks for the heads up on that.

Thanks again dude.

:guitar:

---

### Post by woods-wannamaker on 2016-03-06
Thanks for the solution (it works), but it keeps being reset, then fails again for the next update. How to make it permanent? (Kubuntu 15.10)

---

### Post by Bashing-om on 2016-03-06
woods-wannamaker; Hey ;

On that case take a look at the file " /opt/google/chrome/cron/google-chrome "
the script also generates the .list file
In my install lines 24 and 25 and add the field "[arch=amd64]" there also .

Remember to make a backup of any file one edits prior to that edit .

Been there done that
[INDENT][INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2016-03-06
> **Bashing-om said:**
> woods-wannamaker; Hey ;

On that case take a look at the file " /opt/google/chrome/cron/google-chrome "
the script also generates the .list file
In my install lines 24 and 25 and add the field "[arch=amd64]" there also .

Remember to make a backup of any file one edits prior to that edit .

Been there done that[INDENT][INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]
[/INDENT]

Hey good job Bashing-om...Thanks for your bit..:)
And yes backup files before edits the only way to fly.... 
Regards

---

### Post by psfal on 2016-03-07
Was just coming on here to check on that, happened this past Thurs. Thanks for already having a thread for this issue :D

---

### Post by jooge on 2016-03-12
> **Bashing-om said:**
> woods-wannamaker; Hey ;

On that case take a look at the file " /opt/google/chrome/cron/google-chrome "
the script also generates the .list file
In my install lines 24 and 25 and add the field "[arch=amd64]" there also .

Remember to make a backup of any file one edits prior to that edit .

Been there done that[INDENT][INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]
[/INDENT]



For some odd reason I cannot access  /opt/google/chrome/cron/google-chrome. I have root privileges in Nautilus and I am trying to "Open with Notepad" to do your suggestion but I can't. How can I do this? 
Sorry for the noobish question ;)

Thanks

---

### Post by QDR06VV9 on 2016-03-12
Does this work
```
gksudo gedit  /opt/google/chrome/cron/google-chrome

```

---

### Post by jooge on 2016-03-12
> **runrickus said:**
> Does this work
```
gksudo gedit  /opt/google/chrome/cron/google-chrome

```


Yes that allowed me to edit it, thanks runrickus. I do have a follow-up question though. This is line 24 & 25:

```
REPOCONFIG="deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main"
REPOCONFIGREGEX="deb (\[arch=[^]]*\bamd64\b[^]]*\][[:space:]]*)?https?://dl.google.com/linux/chrome/deb/ stable main"
```


As you can see I added **[arch=amd64]** in the correct place in line 24. Where do I add it in line 25? Do I deleted the "(\[arch=[^]]*\bamd64\b[^]]*\][[:space:]]*)?" and replace it with **[arch=amd64] ? **So that it looks like this[B]:


[/B]
```
REPOCONFIGREGEX="deb [arch=amd64] https?://dl.google.com/linux/chrome/deb/ stable main"
```Thanks again for your help.

---

### Post by deadflowr on 2016-03-13
It's fine as is, I see it myself. I think google put that stuff in there.
Did you run an update with the new entry yet?

---

### Post by jooge on 2016-03-13
> **deadflowr said:**
> It's fine as is, I see it myself. I think google put that stuff in there.
Did you run an update with the new entry yet?


Yes I just made the alteration to line 25 now after you said it looked fine and ran an update and it works :D

Thanks everyone for your help on this issue.

---

### Post by pavel27 on 2016-03-13
Hello everybody!
I've tried to fix this error. I entered these commands
```
sudo sed -i -e 's/deb http/deb [arch=amd64] http/' "/etc/apt/sources.list.d/google-chrome.list"
sudo sed -i -e 's/deb http/deb [arch=amd64] http/' "/opt/google/chrome/cron/google-chrome"
```\
than
```
sudo apt-get update
```
Also I checked google-chrome.list via gedit and saw this
```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```
But I still have the error. What's wrong?
Ubuntu 14.04, MATE 1.8.2

---

### Post by deadflowr on 2016-03-13
> **pavel27 said:**
> Hello everybody!
I've tried to fix this error. I entered these commands
```
sudo sed -i -e 's/deb http/deb [arch=amd64] http/' "/etc/apt/sources.list.d/google-chrome.list"
sudo sed -i -e 's/deb http/deb [arch=amd64] http/' "/opt/google/chrome/cron/google-chrome"
```\
than
```
sudo apt-get update
```
Also I checked google-chrome.list via gedit and saw this
```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```
But I still have the error. What's wrong?
Ubuntu 14.04, MATE 1.8.2

Are you using a 64-bit version of Ubuntu, or 32-bit?

---

### Post by Bashing-om on 2016-03-13
pavel27; Well ..

Possible that there is more than one source ??
Post back :
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
And we will inspect the sources for errors.

Is the error the same ?

show us:
```

sudo apt update
sudo apt upgrade

```

[INDENT][INDENT]getting to the bottom
[INDENT][INDENT][INDENT]not without effort
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by psfal on 2016-03-14
> **jooge said:**
> For some odd reason I cannot access  /opt/google/chrome/cron/google-chrome. I have root privileges in Nautilus and I am trying to "Open with Notepad" to do your suggestion but I can't. How can I do this? 
Sorry for the noobish question ;)

Thanks


Try it from Terminal. I don't use nautilus, but for gedit it's "sudo gedit /opt/google/chrome/cron/google-chrome" so try "sudo notepad /opt/google/chrome/cron/google-chrome".

But this change will not stick for the next update either, we still need a permanent fix for this issue

---

### Post by pavel27 on 2016-03-14
> **deadflowr said:**
> Are you using a 64-bit version of Ubuntu, or 32-bit?
```
pavel@pavel-laptop-PC:~$ uname -a
Linux pavel-laptop-PC 3.16.0-62-generic #83~14.04.1-Ubuntu SMP Fri Feb 26 22:52:39 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```
Here is results
```
pavel@pavel-laptop-PC:~$ cat -n /etc/apt/sources.list
1    # deb cdrom:[Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://ru.archive.ubuntu.com/ubuntu/ trusty main restricted
     6    deb-src http://ru.archive.ubuntu.com/ubuntu/ trusty main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    
    11    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12    ## team. Also, please note that software in universe WILL NOT receive any
    13    ## review or updates from the Ubuntu security team.
    14    deb http://ru.archive.ubuntu.com/ubuntu/ trusty universe
    15    deb-src http://ru.archive.ubuntu.com/ubuntu/ trusty universe
    16    
    17    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    18    ## team, and may not be under a free licence. Please satisfy yourself as to 
    19    ## your rights to use the software. Also, please note that software in 
    20    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    21    ## security team.
    22    deb http://ru.archive.ubuntu.com/ubuntu/ trusty multiverse
    23    deb-src http://ru.archive.ubuntu.com/ubuntu/ trusty multiverse
    24    
    25    ## N.B. software from this repository may not have been tested as
    26    ## extensively as that contained in the main release, although it includes
    27    ## newer versions of some applications which may provide useful features.
    28    ## Also, please note that software in backports WILL NOT receive any review
    29    ## or updates from the Ubuntu security team.
    30    
    31    deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    32    deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
    33    deb http://security.ubuntu.com/ubuntu trusty-security universe
    34    deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    35    deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    36    deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
    37    
    38    ## Uncomment the following two lines to add software from Canonical's
    39    ## 'partner' repository.
    40    ## This software is not part of Ubuntu, but is offered by Canonical and the
    41    ## respective vendors as a service to Ubuntu users.
    42    deb http://archive.canonical.com/ubuntu trusty partner
    43    deb-src http://archive.canonical.com/ubuntu trusty partner
    44    
    45    ## This software is not part of Ubuntu, but is offered by third-party
    46    ## developers who want to ship their latest software.
    47    deb http://extras.ubuntu.com/ubuntu trusty main
    48    deb-src http://extras.ubuntu.com/ubuntu trusty main
    49    deb http://archive.canonical.com/ trusty partner
    50    # deb-src http://archive.canonical.com/ trusty partner


```
and 
```
pavel@pavel-laptop-PC:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/andrew-crew-kuznetsov-xneur-stable-trusty.list <==


==> /etc/apt/sources.list.d/andrew-crew-kuznetsov-xneur-stable-trusty.list.save <==


==> /etc/apt/sources.list.d/andrew-crew-kuznetsov-xneur-unstable-trusty.list <==
deb http://ppa.launchpad.net/andrew-crew-kuznetsov/xneur-unstable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/andrew-crew-kuznetsov/xneur-unstable/ubuntu trusty main


==> /etc/apt/sources.list.d/andrew-crew-kuznetsov-xneur-unstable-trusty.list.save <==
deb http://ppa.launchpad.net/andrew-crew-kuznetsov/xneur-unstable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/andrew-crew-kuznetsov/xneur-unstable/ubuntu trusty main


==> /etc/apt/sources.list.d/atareao-atareao-trusty.list <==
deb http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main


==> /etc/apt/sources.list.d/atareao-atareao-trusty.list.save <==
deb http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main


==> /etc/apt/sources.list.d/diesch-testing-trusty.list <==
deb http://ppa.launchpad.net/diesch/testing/ubuntu trusty main
# deb-src http://ppa.launchpad.net/diesch/testing/ubuntu trusty main


==> /etc/apt/sources.list.d/diesch-testing-trusty.list.save <==
deb http://ppa.launchpad.net/diesch/testing/ubuntu trusty main
# deb-src http://ppa.launchpad.net/diesch/testing/ubuntu trusty main


==> /etc/apt/sources.list.d/forkotov02-ppa-trusty.list <==
deb http://ppa.launchpad.net/forkotov02/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/forkotov02/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/forkotov02-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/forkotov02/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/forkotov02/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google.list <==
deb http://dl.google.com/linux/chrome/deb/ stable main
deb http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google.list.save <==
deb http://dl.google.com/linux/chrome/deb/ stable main
deb http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/gurqn-systray-trusty-trusty.list <==
deb http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main


==> /etc/apt/sources.list.d/gurqn-systray-trusty-trusty.list.save <==
deb http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main


==> /etc/apt/sources.list.d/rebuntu16-other-stuff-trusty.list <==
deb http://ppa.launchpad.net/rebuntu16/other-stuff/ubuntu trusty main
# deb-src http://ppa.launchpad.net/rebuntu16/other-stuff/ubuntu trusty main


==> /etc/apt/sources.list.d/rebuntu16-other-stuff-trusty.list.save <==
deb http://ppa.launchpad.net/rebuntu16/other-stuff/ubuntu trusty main
# deb-src http://ppa.launchpad.net/rebuntu16/other-stuff/ubuntu trusty main


==> /etc/apt/sources.list.d/tualatrix-ppa-trusty.list <==
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/tualatrix-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/ubuntu-mate-dev-ppa-trusty.list <==
deb http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/ubuntu-mate-dev-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/ubuntu-mate-dev-trusty-mate-trusty.list <==
deb http://ppa.launchpad.net/ubuntu-mate-dev/trusty-mate/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-mate-dev/trusty-mate/ubuntu trusty main


==> /etc/apt/sources.list.d/videolan-stable-daily-trusty.list <==
deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu trusty main
# deb-src http://ppa.launchpad.net/videolan/stable-daily/ubuntu trusty main


==> /etc/apt/sources.list.d/videolan-stable-daily-trusty.list.save <==
deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu trusty main
# deb-src http://ppa.launchpad.net/videolan/stable-daily/ubuntu trusty main


==> /etc/apt/sources.list.d/xubuntu-dev-xfce-4_12-trusty.list <==
deb http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu trusty main


==> /etc/apt/sources.list.d/xubuntu-dev-xfce-4_12-trusty.list.save <==
deb http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu trusty main

```And errors after apt upgrade
```
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)

```

---

### Post by QDR06VV9 on 2016-03-14
> **pavel27 said:**
> ```
pavel@pavel-laptop-PC:~$ uname -a
Linux pavel-laptop-PC 3.16.0-62-generic #83~14.04.1-Ubuntu SMP Fri Feb 26 22:52:39 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```
Here is results
```
pavel@pavel-laptop-PC:~$ cat -n /etc/apt/sources.list
1    # deb cdrom:[Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://ru.archive.ubuntu.com/ubuntu/ trusty main restricted
     6    deb-src http://ru.archive.ubuntu.com/ubuntu/ trusty main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    
    11    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12    ## team. Also, please note that software in universe WILL NOT receive any
    13    ## review or updates from the Ubuntu security team.
    14    deb http://ru.archive.ubuntu.com/ubuntu/ trusty universe
    15    deb-src http://ru.archive.ubuntu.com/ubuntu/ trusty universe
    16    
    17    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    18    ## team, and may not be under a free licence. Please satisfy yourself as to 
    19    ## your rights to use the software. Also, please note that software in 
    20    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    21    ## security team.
    22    deb http://ru.archive.ubuntu.com/ubuntu/ trusty multiverse
    23    deb-src http://ru.archive.ubuntu.com/ubuntu/ trusty multiverse
    24    
    25    ## N.B. software from this repository may not have been tested as
    26    ## extensively as that contained in the main release, although it includes
    27    ## newer versions of some applications which may provide useful features.
    28    ## Also, please note that software in backports WILL NOT receive any review
    29    ## or updates from the Ubuntu security team.
    30    
    31    deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    32    deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
    33    deb http://security.ubuntu.com/ubuntu trusty-security universe
    34    deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    35    deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    36    deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
    37    
    38    ## Uncomment the following two lines to add software from Canonical's
    39    ## 'partner' repository.
    40    ## This software is not part of Ubuntu, but is offered by Canonical and the
    41    ## respective vendors as a service to Ubuntu users.
    42    deb http://archive.canonical.com/ubuntu trusty partner
    43    deb-src http://archive.canonical.com/ubuntu trusty partner
    44    
    45    ## This software is not part of Ubuntu, but is offered by third-party
    46    ## developers who want to ship their latest software.
    47    deb http://extras.ubuntu.com/ubuntu trusty main
    48    deb-src http://extras.ubuntu.com/ubuntu trusty main
    49    deb http://archive.canonical.com/ trusty partner
    50    # deb-src http://archive.canonical.com/ trusty partner


```
and 
```
pavel@pavel-laptop-PC:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/andrew-crew-kuznetsov-xneur-stable-trusty.list <==


==> /etc/apt/sources.list.d/andrew-crew-kuznetsov-xneur-stable-trusty.list.save <==


==> /etc/apt/sources.list.d/andrew-crew-kuznetsov-xneur-unstable-trusty.list <==
deb http://ppa.launchpad.net/andrew-crew-kuznetsov/xneur-unstable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/andrew-crew-kuznetsov/xneur-unstable/ubuntu trusty main


==> /etc/apt/sources.list.d/andrew-crew-kuznetsov-xneur-unstable-trusty.list.save <==
deb http://ppa.launchpad.net/andrew-crew-kuznetsov/xneur-unstable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/andrew-crew-kuznetsov/xneur-unstable/ubuntu trusty main


==> /etc/apt/sources.list.d/atareao-atareao-trusty.list <==
deb http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main


==> /etc/apt/sources.list.d/atareao-atareao-trusty.list.save <==
deb http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main


==> /etc/apt/sources.list.d/diesch-testing-trusty.list <==
deb http://ppa.launchpad.net/diesch/testing/ubuntu trusty main
# deb-src http://ppa.launchpad.net/diesch/testing/ubuntu trusty main


==> /etc/apt/sources.list.d/diesch-testing-trusty.list.save <==
deb http://ppa.launchpad.net/diesch/testing/ubuntu trusty main
# deb-src http://ppa.launchpad.net/diesch/testing/ubuntu trusty main


==> /etc/apt/sources.list.d/forkotov02-ppa-trusty.list <==
deb http://ppa.launchpad.net/forkotov02/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/forkotov02/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/forkotov02-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/forkotov02/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/forkotov02/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google.list <==
deb http://dl.google.com/linux/chrome/deb/ stable main
deb http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google.list.save <==
deb http://dl.google.com/linux/chrome/deb/ stable main
deb http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/gurqn-systray-trusty-trusty.list <==
deb http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main


==> /etc/apt/sources.list.d/gurqn-systray-trusty-trusty.list.save <==
deb http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main


==> /etc/apt/sources.list.d/rebuntu16-other-stuff-trusty.list <==
deb http://ppa.launchpad.net/rebuntu16/other-stuff/ubuntu trusty main
# deb-src http://ppa.launchpad.net/rebuntu16/other-stuff/ubuntu trusty main


==> /etc/apt/sources.list.d/rebuntu16-other-stuff-trusty.list.save <==
deb http://ppa.launchpad.net/rebuntu16/other-stuff/ubuntu trusty main
# deb-src http://ppa.launchpad.net/rebuntu16/other-stuff/ubuntu trusty main


==> /etc/apt/sources.list.d/tualatrix-ppa-trusty.list <==
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/tualatrix-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/ubuntu-mate-dev-ppa-trusty.list <==
deb http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/ubuntu-mate-dev-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/ubuntu-mate-dev-trusty-mate-trusty.list <==
deb http://ppa.launchpad.net/ubuntu-mate-dev/trusty-mate/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-mate-dev/trusty-mate/ubuntu trusty main


==> /etc/apt/sources.list.d/videolan-stable-daily-trusty.list <==
deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu trusty main
# deb-src http://ppa.launchpad.net/videolan/stable-daily/ubuntu trusty main


==> /etc/apt/sources.list.d/videolan-stable-daily-trusty.list.save <==
deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu trusty main
# deb-src http://ppa.launchpad.net/videolan/stable-daily/ubuntu trusty main


==> /etc/apt/sources.list.d/xubuntu-dev-xfce-4_12-trusty.list <==
deb http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu trusty main


==> /etc/apt/sources.list.d/xubuntu-dev-xfce-4_12-trusty.list.save <==
deb http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu trusty main

```And errors after apt upgrade
```
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)

```
 Well as bashing-om suggested you have multiple sources for google
You can navigate to "/var/lib/apt/lists/dl.google" as Administrator
and delete the Dups there..I will add a screenshot as to how mine looks and should be the same for you or similar.

---

### Post by Bashing-om on 2016-03-14
pavel27; Hello;


First a warning .. running a graphical application ( gedit or leafpad ) with 'sudo' will have BAD side effects. If one is to activate a GUI app with the elevated authority .. it is "gksudo" or "sudo -H" OR "pkexec" to perform that function. - sudo in the graphical interface will result in 'root' owning files that you should own .. BAD bad bad .

Yep as runrickus advises. Sources are duplicated, and the alternate is not updated... that alternate requires removal from the system.

> 
==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


==> /etc/apt/sources.list.d/google.list <==
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


==> /etc/apt/sources.list.d/google.list.save <==
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


A couple of ways to do the removal . Me, I prefer the terminal .. - more info and direct to the point.

You could do a number like this:
```

sudo rm /etc/apt/sources.list.d/google.list 
sudo rm /etc/apt/sources.list.d/google.list.save

```

Now run in terminal:
```

sudo apt update
sudo apt upgrade

```

I do expect all to be good, and the system to fully update.

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by pavel27 on 2016-03-14
Runrickus, I'm not sure which one should I leave?

---

### Post by QDR06VV9 on 2016-03-14
The one next to the one you have highlighted(with the i386) in your screenshot would be the one you want to delete.
@Bashing-om thanks for the warning I left out..
> First a warning .. running a graphical application ( gedit or leafpad ) with 'sudo' will have BAD side effects.
Kind Regards

---

### Post by pavel27 on 2016-03-14
Runrickus, Bashing-om, thanks, I've just done deleting. There is no errors anymore!!
And thanks for warnings about GUI and sudo. I'll be more careful in future :)

---

### Post by Bashing-om on 2016-03-14
pavel27; Great.

:) Pleased to be of some assistance, runrickus did the heavy lifting .


[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

