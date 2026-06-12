---
title: "[SOLVED] How do I install 'install_flash_player_9_linux.tar.gz'?"
date: 2008-05-12
forum: General Help
---

### Post by grs on 2008-05-12
I've downloaded Flash player to install for Firefox to run some websites
I extracted the contents from install_flash_player_9_linux.tar.gz then clicked on the install file and selected to run from the terminal but here is what happened:

---------------------

----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/myname/.mozilla

Proceed with the installation? (y/n/q): y
cp: cannot stat `/libflashplayer.so': No such file or directory

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.

chmod: cannot access `/home/myname/.mozilla/plugins/libflashplayer.so': No such file or directory

Installation complete.


Perform another installation? (y/n): 

-----------------------

How do I install Flash?

---

### Post by dje on 2008-05-12
You do not need to use that package, just open up a terminal (Applications >> Accessories >> Terminal) and type:
```
sudo apt-get install flashplugin-nonfree
```
then restart firefox and enjoy flash

hope that helps,
dje

---

### Post by grs on 2008-05-12
I got that running now I can play videos from youtube etc but there is no sound.

---

### Post by pedro_orange on 2008-05-12
30 seconds googling and here you are: (Google is your friend)

```
mv ~/.asoundrc .asoundrc.old
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old
```

Restart Firefox and you're laughing.

---

### Post by grs on 2008-05-12
Tried that, no difference.

---

### Post by dje on 2008-05-12
EDIT - First try this:
```
sudo apt-get install libflashsupport
```

If that doesn't work then try the first post in [this thread]("http://ubuntuforums.org/showthread.php?t=204022")

hope that helps,
dje

---

### Post by grs on 2008-05-12
Got it running with your code. Thanks

---

### Post by dje on 2008-05-12
No problem grs, glad you got it working :)

dje

---

