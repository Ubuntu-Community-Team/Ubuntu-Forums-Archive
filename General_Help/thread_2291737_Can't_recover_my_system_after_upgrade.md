---
title: "Can't recover my system after upgrade"
date: 2015-08-22
forum: General Help
---

### Post by Przemysaw_aba on 2015-08-22
Good evening,

I do not know how much of that will be useful to describe my problem, but I feel I have to describe step by step. 
  I have used Ubuntu 14.04 LTS. Yesterday, I wanted to watch a film  using VLC Media Player. The trouble was, my version of VLC did not open  files with hevc/h265 codec, so I wanted to upgrade this to version 2.2  or higher. Unlucky, it was impossible both via terminal and Software  Center. There was trouble with some dependencies. So I removed VLC  completely and I wanted to reinstall, but it proved impossible to do,  from the same reason. 
  I decided to upgrade my Ubuntu to version 14.10. I did it via Update  Manager. There were more problems. Updating process didn't go correctly.  Some errors were shown, something wasn't installed etc. But upgrading  was finished and only thing left was to reboot computer. So I did. Then  occur the real trouble. 
  After rebooting it was impossible to log in. There was a communicate,  that only possible is working in low graphic mode. The only thing I  could do was log in via terminal and typing commands. So I decided to  looking for some solutions in Internet using LiveCD Ubuntu 10.04 LTS  (the only version I've got). I've got two ideas what to do next - fix  booting options or upgrade to Ubuntu 15.04. 

```

sudo apt-get install --reinstall ubuntu-desktop
```

This command did not help at all. When I typed others, like

```

sudo apt-get update
sudo apt-get dist-upgrade
sudo do-release-upgrade
```

it was too helpful also. The light of hope was when I use those commands:

```

sudo aptitude remove fglrx
sudo aptitude install fglrx
```


But it was deceptive. I still can no longer log into my system, but  at least there was initial checking disks for errors (like sometimes  before log in). But it let me type in terminal commands to upgrade  Ubuntu so I did it. 
  I'm afraid it was definitely end. Though the downloading of necessary  files went so good, there were still problem with installation. The  communicate said something, that it was impossible to upgrade because of  **too many errors**. When I reboot computer, I can not  even get to terminal mode in low graphic mode. It shows only this window  with inscription "Ubuntu" and those little white points below  (normally, while loading, they turn red). 
  All right, it was long introduction. 
  Using LiveCD i peeked, that in partition, the version of Ubuntu  installed in partition is updated to 15.04. So I downloaded ISO file  with 15.04 version and tried to reinstall system. I know there is such  possibility - in [this link]("http://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/")  someone shows screen which proves that I can reinstall existing version  of Ununtu on my computer without losing data nor programs. But when I  try to do it, the only options I've got are:
  
[LIST]
[*]Install Ubuntu alongside them 
[*]Erase disc and install Ubuntu 
[*]Something else 
[/LIST]
  Not a slide of possibility of reinstall. 
  

  Please advise me what should I do next. The best option is to recover my previous system without losing any data. 

=============================================================================

PS1: I make a little partition, where I installed ubuntu 15.04 from Live CD. I can see my files from previous installation are OK, but of course it does not satisfy me. I want get access to my old distribution. Furthermore, to be able to use this today installed OS I had to reinstall grub, otherwise it wasn't detected.
PS2: In grub there are advanced options for ubuntu, like recovery mode etc. Yes, it partially worked after upgrade to 14.10, but nevermore since 15.04. 

==============================================================================

I count on your help and I believe it is possible to fix that mess.

---

### Post by ian-weisser on 2015-08-22
You have two options: Repair (which maybe rather lengthy) or reinstall (faster, but more intrusive). Tell us which option you want.
Neither should usually delete your data, but the unexpected sometimes occurs - I suggest backing up your data onto a different device first.

If you can boot that other partition or LiveCD and 'see' your data, then  what prevents you from simply copying all your data onto a backup  device?

This sort of thing happens to users who install some software from non-Ubuntu sources. It's usually pretty easy to repair once you understand how the package manager works.

---

### Post by monkeybrain20122 on 2015-08-22
Your system is broken. Back up your data and do a clean install of 15.04 or reinstall 14.04.** 14.10 is no longer supported and you can't do anything in it** (better to keep a separate / and /home partitions for the future which make clean install of new release a lot simpler)

For your vlc problem you could have upgraded it with a ppa without upgrading 14.04 .[https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)


P.S. upgrading with update-manager takes a long time and it will mess up your system if it is not in pristine state (e.g with fglrx driver as in your case) You could have restored your system to its pristine state (removing third party software, proprietary drivers, ppas etc) before upgrade but I would have finished with a clean install and reinstall all my applications already even before you you are 1/2 way through upgrade-manager and I would not mess up my system.

---

### Post by Przemysaw_aba on 2015-08-23
> **ian-weisser said:**
> You have two options: Repair (which maybe rather lengthy) or reinstall (faster, but more intrusive). Tell us which option you want.
Neither should usually delete your data, but the unexpected sometimes occurs - I suggest backing up your data onto a different device first.

Well, the time has no meaning for me, so maybe repair sounds better if I can get access to my old system (and all settings, programs, plugins, bookmarks etc.).

> If you can boot that other partition or LiveCD and 'see' your data, then  what prevents you from simply copying all your data onto a backup  device?

To be honest, I've tried to do it using LiveCD (both 10.04 and 15.04), but then I could copy only part of my files - the rest make error that I can't copy them because of something (authorisation or access fail). 
Now it seems possible to copy everything, maybe I should try once more time. 


> P.S. upgrading with update-manager takes a long time and it will mess up  your system if it is not in pristine state (e.g with fglrx driver as in  your case) You could have restored your system to its pristine state  (removing third party software, proprietary drivers, ppas etc) before  upgrade but I would have finished with a clean install and reinstall all  my applications already even before you you are 1/2 way through  upgrade-manager and I would not mess up my system.

Maybe You're right, but I had upgraded my Ubuntu that way at least three times and it always went OK. Of course, I copied some of my files (which I considered most important), but I wasn't ready fopr such mess.

---

### Post by ian-weisser on 2015-08-23
monkeybrain20122's advice is excellent.
Repairing an EOL system is possible, but rather a waste of time.

Back up your data.
Then do a clean install.
Going forward, uninstall all non-Ubuntu software before upgrading to the next release of Ubuntu.

That final step has meant 10 years of smooth upgrades for me.

---

