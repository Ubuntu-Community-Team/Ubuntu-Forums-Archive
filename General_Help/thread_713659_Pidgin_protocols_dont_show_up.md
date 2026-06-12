---
title: "Pidgin protocols dont show up"
date: 2008-03-03
forum: General Help
---

### Post by xitdedragon on 2008-03-03
So I was trying to upgrade my Pidgin to the latest version and things got really messed up. I did this with a few versions from source. Finally I deleted all those and the Ubuntu one, and tried to download and install the new one from GetDeb. This seemed to work fine until I started the program and none of the protocols showed up. All my accounts and settings were there, but none of them had protocols associated with them and when I tried to choose one there were none to choose from. The only thing I could think of was that I deleted a file I wasn't supposed to when I was getting rid of old versions. Those were mostly just old bin files though. Anyway, if anyone could help, I would appreciate it.

---

### Post by KyleMarsh on 2008-05-03
I'm having this problem too...I was running Gutsy with pidgin 2.3.1 installed from source, and when I upgraded to Hardy I saw that 2.4.1 was in the repos, so I uninstalled the copy I had from source with `make uninstall`.  It seems to have killed something that the repo version needs because it's now broken.  Symptoms and attempted repairs below:

Symptoms:
    Pidgin launches fine and the window show up, but the buddy list area remains blank.  Most options in the menus are greyed out.  All the plugins except OTR are greyed out.  In the account manager my accounts are listed, but the only plugin available is bonjour.  I don't have a bonjour account, so I can't check if it works.

Attempts to fix so far:
    `sudo dpkg-reconfigure pidgin`
    `sudo apt-get remove pidgin` followed by `sudo aptitude install pidgin`
    `sudo apt-get purge pidgin` followed by `rm -rf ~/.purple` followed by `sudo aptitude install pidgin` followed by `sudo aptitude reinstall pidgin`

I'm about to try reinstalling the source version I had and see if that replaces whatever got clobbered when I removed it -- the side-by-side installs worked fine, I just wanted to clean up a bit.

~KMarsh

---

### Post by xitdedragon on 2008-05-03
When I upgraded to Hardy it started working again. /*shrugs*/

---

