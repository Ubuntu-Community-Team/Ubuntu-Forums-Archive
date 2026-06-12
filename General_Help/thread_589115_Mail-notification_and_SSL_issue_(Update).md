---
title: "Mail-notification and SSL issue (Update)"
date: 2007-10-23
forum: General Help
---

### Post by jrattner on 2007-10-23
Has anyone generated a Debian package which includes SSL support for the mail-notification package?


If not, has anyone been successful at building this package from source (with SSL enabled), and if so, which -dev packages were prerequisites?

---

### Post by drdnl on 2007-10-26
Oh good, I have the same problem, tried compiling it myself but no luck. Hope there's an answer soon.

---

### Post by racmar on 2007-10-29
Add me to the list.  I had ssl working fine in feisty, but I can't remember if I recompiled or if the standard package had it included.

---

### Post by Whoopie on 2007-10-29
Short howto:

cd /tmp
apt-get source mail-notification
sudo apt-get build-dep mail-notification
sudo apt-get install libssl-dev fakeroot
cd mail-notification-4.1.dfsg.1
vi debian/rules (remove --disable-ssl in line 11)
dpkg-buildpackage -rfakeroot
sudo cp debian/mail-notification/usr/bin/mail-notification /usr/bin/mail-notification

You can check if you have SSL support with "ldd /usr/bin/mail-notification | grep libssl"


Best regards,
Whoopie

---

### Post by racmar on 2007-10-29
@whoopie

Thanks, but I just followed [this howto]("http://ubuntuforums.org/showthread.php?t=581210&highlight=mail+notification+ssl") to use stunnel for handling the imaps stuff.  Using stunnel will not require me to rebuild mail-notification in the future.  However, I'll bookmark your solution and Thanks!

---

### Post by jrattner on 2007-10-29
Thank You!

---

### Post by sockrebel on 2008-02-28
> **Whoopie said:**
> Short howto:

cd /tmp
apt-get source mail-notification
sudo apt-get build-dep mail-notification


I get:
"E: Build-dependencies for mail-notification could not be satisfied."

?!?

---

### Post by jetole on 2008-06-13
As far as using stunnel and not wanting to re-build it for upgrades etc. Well that just seems like the wrong way to do it IMHO. Your adding unessacary complexity to a simple task. I would suggest putting mail-notification on hold after you re-install it. Also with the howto? You can copy the mail notification file itself if you want but you are also creating a .deb here in the parent folder so for keeping apt and cache etc etc up to date I simply install the deb file with dpkg -i ../<file>.deb .

As far as putting the file on hold goes you can run "dpkg --get-selections > selections && sed -i -e "s/mail-notifications\(\t\t*\)install/mail-notifications\1hold/' selections && dpkg --set-selections < selections && apt-get update && rm -f selections"

---

