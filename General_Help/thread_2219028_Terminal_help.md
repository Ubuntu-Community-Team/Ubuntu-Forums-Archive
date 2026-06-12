---
title: "Terminal help"
date: 2014-04-22
forum: General Help
---

### Post by tkillby on 2014-04-22
Sorry for the silly question, fairly new to this. I regularly sudo apt-get update and upgrade, but lately I get this message. 

W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

Of course when I apt-get update it doesn't solve these problems. Thanks for any help, everything is running fine though.

---

### Post by papibe on 2014-04-22
Hi tkillby.

Could you open a terminal, run this command, and post back the results (you can copy/paste the text)?
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Regards.

---

### Post by tkillby on 2014-04-22
Thanks for the quick response:

```
/etc/apt/sources.list.d/google.list

     1    deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

/etc/apt/sources.list.d/google-chrome.list

     1    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2    # You may comment out this entry, but any other modifications may be lost.
     3    deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

/etc/apt/sources.list

     1    # deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Daily i386 (20140405)]/ trusty main restricted
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty main restricted
     6    deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    11    deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty universe
    17    deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty universe
    18    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates universe
    19    deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty multiverse
    27    deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty multiverse
    28    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    29    deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    37    deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    38    
    39    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    40    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    41    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    42    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    43    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    44    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    51    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    56    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
```

---

### Post by anaconda on 2014-04-22
It seems you have the same line:
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

in 2 files:
/etc/apt/sources.list.d/google.list
/etc/apt/sources.list.d/google-chrome.list

and those files do not have anything else in them.

So it is safe to delete one of those files:

sudo rm /etc/apt/sources.list.d/google.list

and then run the
sudo apt-get update

PS. papibe. great work. hope I didn't step on your toes by coming in middle of your excellent help.

---

### Post by tkjeeper on 2014-04-22
Sorry for the confusion, just had my screen name changed, it looks like hyroglyphics to me! Any idea what to look for in /etc/apt/sources.list to delete from what I've posted?

---

### Post by Habitual on 2014-04-22
> **anaconda said:**
> 

sudo rm /etc/apt/sources.list.d/google.list

and then run the
sudo apt-get update

 much wiser man than I said. :)

---

### Post by tkjeeper on 2014-04-22
awesome! worked like a charm, thanks to both of you for the quick help!

If  theres any way I could impose a little further, I'm not getting any  response on this. I recently tried the old sudo install xubuntu-desktop,  didn't like it so I got everything removed, only thing I'm missing  badly is the nice newer 14.04 lockscreen, I have a white box in the  middle of the screen to choose a user an log in, not near as nice,  everything works, but I miss the new one. PS I can get to the nice  lockscreen by Ctrl+Alt+L, but it's only for me, not the general login  screen for all users. Once again, Thanks so much. 
PS. papibe. great work. hope I didn't step on your toes by coming in middle of your excellent help.[/QUOTE]





[QUOTE=anaconda;12998352]It seems you have the same line:
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

in 2 files:
/etc/apt/sources.list.d/google.list
/etc/apt/sources.list.d/google-chrome.list

and those files do not have anything else in them.

So it is safe to delete one of those files:

sudo rm /etc/apt/sources.list.d/google.list

and then run the
sudo apt-get update

---

### Post by nothingspecial on 2014-04-22
Much better to put that question in a new thread so someone else has a chance of finding the answer when they do a search. I would call it, "How to get my lockscreen back after installing and removing xubuntu-desktop"

---

### Post by tkjeeper on 2014-04-22
thanks

---

