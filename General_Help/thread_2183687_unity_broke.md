---
title: "unity broke"
date: 2013-10-25
forum: General Help
---

### Post by guine on 2013-10-25
So I just got a new computer with 13.04 running and it was working for a couple of days until I launched a full screen game and the game locked up and left me stuck with a black screen and a cursor but nothing would respond so I rebooted my computer.  When it booted back up and I logged in my wallpaper was the only thing to come up, launchpad and the bar across the top never appeared.  I tried to do this solution but it had no effect - [http://askubuntu.com/questions/214529/unity-launcher-has-disappeared](http://askubuntu.com/questions/214529/unity-launcher-has-disappeared)
After that failed I decided to try upgrading to 13.10 and the upgrade seemed to go smoothly until the end when it wanted to reboot and instead it did nothing so I rebooted it on my own and when I logged in this time my wall paper didn't even load and all I got was a black screen with a cursor.  I also have xfce installed and that still appears to be working properly.  Anyone have any ideas how to fix unity?  Thanks

---

### Post by vanadium on 2013-10-26
Try resetting Unity: [http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/](http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/)

---

### Post by guine on 2013-10-26
It still boots to a black screen with a cursor that I can move around but I can't launch anything with the mouse or a keyboard shortcut.

---

### Post by vanadium on 2013-10-26
Try creating a new user account. If you succeed loging in into the new user account, then you know it is a problem in the user configuration. Else it is a system wide problem.

---

### Post by guine on 2013-10-26
Same problem with a different account.

---

### Post by guine on 2013-10-26
Can add this to things that haven't had an effect
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:unity-team/staging
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity
```
And when I try this
```
unity --reset
sudo service lightdm restart
```
I get an error after I enter the first command - ERROR:  the reset option is now deprecated

---

### Post by vanadium on 2013-10-27
Problem difficult to identify, as you see yourself. I would reinstall. If the problem remains, or comes back, then there definitely must be some uncompatibility between Unity and your hardware. Anyway, as you did an upgrade rather than a clean reinstall, there may currently be quircks in your system which definitely won't be there after a clean install (= wiping the current OS before installing the new one). I much expect the problem be gone after a fresh install in this case.

---

