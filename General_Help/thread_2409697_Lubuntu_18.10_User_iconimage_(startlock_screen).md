---
title: "Lubuntu 18.10 User icon/image (start/lock screen) ??"
date: 2019-01-05
forum: General Help
---

### Post by zeiken on 2019-01-05
Can anyone please help me change the hideous gray icon/user image in the lock screen/start screen where you type your password to login? I've tried literally every single method suggested through google searches and none have worked. I am on Lubuntu 18.10 and can't change my user image icon to save my life.

---

### Post by Dennis N on 2019-01-05
You need to install a different theme for the login screen. It's explained in this thread:
[https://ubuntuforums.org/showthread.php?t=2407308](https://ubuntuforums.org/showthread.php?t=2407308)

---

### Post by zeiken on 2019-01-05
I've tried saving a picture to home directory, it does not let me paste anything in home directory. Many searches say rename a .png picture to .face and place in "home" directory but it has red circle with line like I can't paste anything in home directory

---

### Post by zeiken on 2019-01-05
also Muon Package Manager shows I have sddm installed, how to open it?

---

### Post by CatKiller on 2019-01-05
> **zeiken said:**
> I've tried saving a picture to home directory, it does not let me paste anything in home directory. Many searches say rename a .png picture to .face and place in "home" directory but it has red circle with line like I can't paste anything in home directory

You don't put it in /home, you put it in /home/zeiken, or whatever your username on your computer is.

If you can't write to your own Home folder you have way bigger problems than your profile icon.

---

### Post by zeiken on 2019-01-05
> **CatKiller said:**
> You don't put it in /home, you put it in /home/zeiken, or whatever your username on your computer is.

If you can't write to your own Home folder you have way bigger problems than your profile icon.

already put it in my home/zeiken as .face   No change whatsoever. The other thing posted was to get sddm which was already installed and install the maui theme, which I did, then says to edit sddm.conf file which I have TWO of.. one gives me permission denied.. the other looks like a script.. WOW what a mission just to change the user image....

---

### Post by CatKiller on 2019-01-05
I've not used Lubuntu, but in Gnome, KDE and Xfce you can change your account's profile picture simply by clicking it in the user settings screen.

---

### Post by zeiken on 2019-01-05
*EDIT* After a whole week of trying to find a fix, I finally found it. The fix was quite easy, instead of saving an image as .face, save the image as .face.icon  in your /home/(username) folder. Not sure if image should be a .PNG file or not, but my image I saved as a png with no extensions. Might want to save the image with equal dimensions, though I'm not sure if it makes a difference. Didn't even need to use a different lock/start screen manager or different theme. Lubuntu 18.10 out of the box.

---

### Post by Dennis N on 2019-01-05
> **zeiken said:**
> also Muon Package Manager shows I have sddm installed, how to open it?

See this post for advice:

[https://ubuntuforums.org/showthread.php?t=2407308&p=13828678#post13828678](https://ubuntuforums.org/showthread.php?t=2407308&p=13828678#post13828678)

---

