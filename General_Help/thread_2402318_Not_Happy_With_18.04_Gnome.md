---
title: "Not Happy With 18.04 Gnome"
date: 2018-09-28
forum: General Help
---

### Post by brenneke on 2018-09-28
Can someone please point me in the right direction with how to best achieve a way to have desktop shortcuts? is it best to install Unity or does this create other problems? Are there any other alternatives to consider?
I have Show icons set to ON in Tweaks, dragging icons onto desktop still does not work. I also have no Trash icon or shortcut. 
Thank you.

---

### Post by Dennis N on 2018-09-28
Trash Icon: Tweaks > Desktop > Show Icons ON, Trash ON
Shortcuts: Open Terminal to Desktop folder, make symbolic link to target of shortcut:

Pattern:
```
ln -s target name-of-link
```
Example:
```
ln -s ~/Documents/Passwords.txt My_Passwords
```

---

### Post by brenneke on 2018-09-28
Nothing showing on Desktop despite icons on desktop all set to ON in Tweaks - any ideas as to why?

I will give symbolic links a go, thanks.

---

### Post by Dennis N on 2018-09-28
> **brenneke said:**
> Nothing showing on Desktop despite icons on desktop all set to ON in Tweaks - any ideas as to why?

Nope, but another tool is **dconf-editor**, which is not installed by default. Once installed, navigate to **org > gnome > nautilus > desktop** where there are switches to choose what to display. Check settings there. But, pretty sure this is what Tweaks does for you.

---

### Post by brenneke on 2018-09-28
How about just installing Unity - any downside to this?

---

### Post by deadflowr on 2018-09-28
> **brenneke said:**
> How about just installing Unity - any downside to this?

Not any real major downsides, runs well on 18.04.

See monkeybrain20122's post here:
[https://ubuntuforums.org/showthread.php?t=2393395&p=13772776#post13772776]("https://ubuntuforums.org/showthread.php?t=2393395&p=13772776#post13772776")
Pretty straight forward.

---

### Post by monkeybrain20122 on 2018-09-28
> **brenneke said:**
> How about just installing Unity - any downside to this?

No downside, Using unity on 18.04 here.

---

### Post by brenneke on 2018-09-29
I have installed Unity and uninstalled Gnome, still no desktop icons despite all my old shortcuts in Desktop folder. Other problems I am having is cannot change desktop background - when I attempt to select a pic from Pictures folder the folder cannot be found and then it freezes system. Any help or ideas will be much appreciated. 
Is there a way to reinstall 18.04 without losing data?

---

### Post by monkeybrain20122 on 2018-09-29
How did you install Ubuntu 18.04? Is it an upgrade or a clean install?

I hate to dump "icons" on the desktop but just to prove that it can be done I made this screenshot for you (see bino on the upper left corner). Also note the wallpaper, it is from the Picture folder.

P.S I just dragged the icon from  the dash to the desktop.

---

### Post by brenneke on 2018-09-29
OK, interesting. The pictures folder on my system is at: /home/gw/.local/share/teamviewer12/drive_c/users/Public
Should I move it?
I upgraded from 16.04 LTS.
Thanks for your help.

---

### Post by monkeybrain20122 on 2018-09-29
> **brenneke said:**
> OK, interesting. The pictures folder on my system is at: /home/gw/.local/share/teamviewer12/drive_c/users/Public
Should I move it?
I upgraded from 16.04 LTS.
Thanks for your help.

Why would it be in teamviewer? and drive_C is a wine thing, I am confused.

---

### Post by brenneke on 2018-09-29
I made Pictures, Music and Videos folders in my Home directory, the links in Files for these folders now work.
My Desktop shows nothing but the Bionic Beaver image. I can now change it to an image from my Pictures folder but Desktop still shows the Beaver. If I select the monitor icon from the top right corner (remember now Unity) and select my computer name, it takes me to a login screen that has the image I chose when trying to change Desktop image - as soon as I enter password and hit enter, goes back to the beaver again.
Any ideas anyone? It is alsmost as if I am logged in as different user.....?

---

### Post by brenneke on 2018-09-29
> **monkeybrain20122 said:**
> Why would it be in teamviewer? and drive_C is a wine thing, I am confused.
Yeah not sure. This has never been a dual boot machine and have never used Wine.

---

### Post by monkeybrain20122 on 2018-09-29
I would move the pictures to the Pictures folder.

---

### Post by mc4man on 2018-09-29
Go to the login scrren & then to a tty (ctrl+alt+F3 should work.
At the console login to your user (enter name, then password.
Once logged in run this command
```
mv .config/dconf/user .config/dconf/user.bak
```
If that completes successfully (i.e you're returned to prompt without message), then run this command
```
reboot
```
See if things improve..

Teamviewer doesn't use wine, it's for remote access to another device or remote access from another device to your computer. Get rid of it if not using. If installed via a .deb then purge with apt,  this will show if installed & name
```
apt-cache policy teamviewer*
```

---

### Post by brenneke on 2018-09-30
Went back to 16.04 LTS.

---

### Post by Paulgirardin on 2018-12-03
A late response for other viewers of this thread.

No need for icons on the desktop in Ubuntu Gnome.

Make sure you have a Files launcher in the Gnome dock.

Right clicking on the files button shows any Files book marks you have created such as Music, Videos etc

---

### Post by Quarkrad on 2018-12-04
I came across this problem with 18.04 - my solution was to do a clean install of Ubuntu Mate 18.04.  Works extremely well - offers a number of desktop layouts and all have full functioning icons on Desktop.

---

