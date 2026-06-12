---
title: "Package management errors"
date: 2015-10-12
forum: General Help
---

### Post by maxime-jak on 2015-10-12
Hello,

STORY: skype wasn't working properly, so i removed it to install it again.


    sudo apt-get remove skype
    sudo apt-get autoremove


PROBLEM: when i

    sudo apt-get install skype

it gives an broken packages error. I want to fix it with synaptics package manager but when i click: fix broken packages, it returns an error.


QUESTION: what do I do now? I desperately need skype.




WHAT I TRIED SO FAR: 


    sudo apt-get purge skype
    sudo apt-get autoclean
    sudo apt-get clean
    sudo apt-get autoremove


I have also tried downloading from the website, it gives an error while installing: cannot install libqt4-dbus:i386


When I try to install it from the commandline, it says: missing dependencies: skype-bin


when I try 


    sudo apt-get install skype-bin


it says missing dependencies: libqt4-dbus:i386 and a whole lot of other packages. When I try to install one of those packages it misses some other packages. What do i have to do?
Thanks in advance,

---

### Post by ian-weisser on 2015-10-12
Please open a terminal.
Run the following commands, and post the entire output here. Use [code tags]("http://ubuntuforums.org/showthread.php?t=1189729") to contain the output.
```
sudo apt-get update
sudo apt-get upgrade
apt-cache policy skype
```
We want to see *all* the output, including errors in the order they occur.


'apt-get purge' didn't work because 'purge' doesn't mean what you perhaps think it means.
    'apt-get autoclean' and 'apt-get clean' do very different things (don't use them together). Neither has anything to do with installing or uninstalling or reinstalling.
    'apt-get autoremove' was a good try, but won't fix a version conflict (which is what you seem to have).

I recommend against trying random apt commands. You may chance upon one that really damages your system, and makes the problem much worse.

I strongly recommend against downloading random deb packages off the dirty, dirty internet. Even if it's not poisoned, you have no way to know it's dependencies until you look in the control file. The wrong dependencies will really screw up your system. Rather like putting diesel in a petrol car - they are both fuels, sold at the same place, and works in other cars with the right parts for it...but not yours.

---

