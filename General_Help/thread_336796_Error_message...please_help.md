---
title: "Error message...please help"
date: 2007-01-12
forum: General Help
---

### Post by healthpellets on 2007-01-12
Greetings.  First, let me say thank you to all of you who help support this great OS.  

I'm brand new to the game, and have really enjoyed my experience so far.  But therein lies the problem...i'm new and have no idea what the following error message means or how to fix it.  So any help would be GREATLY appreciated.

Error:  Opening the cache (E:Type 'wget' is not known on line 34 in source list /etc/apt/sources.list, E:The list of sources could not be read.)

Thank you in advance.

---

### Post by bapoumba on 2007-01-12
Hello,
please open a terminal (if you're using GNOME : > Applications > Terminal ; if KDE, should be somewhere in the K menu), type : **cat /etc/apt/sources.list** and paste in here the complete output.

---

### Post by healthpellets on 2007-01-12
I entered the requested text and received the following result:

bash:  cat/etc/apt/sources.list: No such file or directory 



I forgot to mention earlir, but I'm running 6.06

Thank you.

---

### Post by megamania on 2007-01-12
> **healthpellets said:**
> I entered the requested text and received the following result:

bash:  cat/etc/apt/sources.list: No such file or directory 
looks like you forgot a space after "cat". you can try copying the text and then pasting it into the terminal.

---

### Post by healthpellets on 2007-01-12
thanks for the tip...here it is...


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C
sudo apt-key add -
sudo apt-get update
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

---

### Post by bapoumba on 2007-01-12
> **healthpellets said:**
> 
wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C
sudo apt-key add -
sudo apt-get update


Hello :)

These lines should not be there ;)

So open a terminal again, and run **sudo nano -B /etc/apt/sources.list**
You'll have to give your password in order to open the file (nothing will show on the screen, its normal. Type it and hit enter).
Nano is a small text editor. -B will backup your file with ~ extension.

When your file is open, you'll see it on the screen. Go down to the end of it with the down arrow. Delete the 5 lines I have quoted (and just these 5 ones).

Then hit CTRL key + O (like in Ocean) at the same time. This will save the file, hit enter to save it with the same name.

Then CTRL + X to exit nano.

Run **sudo apt-get update**. Do you still have errors ?

---

### Post by healthpellets on 2007-01-12
problem solved!  thank you sooo much!

---

