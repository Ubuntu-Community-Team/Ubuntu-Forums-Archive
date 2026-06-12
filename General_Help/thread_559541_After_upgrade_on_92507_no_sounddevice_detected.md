---
title: "After upgrade on 9/25/07 no sounddevice detected"
date: 2007-09-25
forum: General Help
---

### Post by thegreatbeste on 2007-09-25
Today i was informed that there is a software upgrade, some necessary for security and so on and so on. I installed it.

After reboot Ubuntu does not detect my sound device anymore.

cat /proc/asound/cards says --no soundcards-- 

I have a realtek ALC260 which worked just before the upgrade.

I run feisty.



Again i ask for a simple UNDO ENGINE that saves all the actions and changes to my system and is able to make them UNDONE.

Yes i know i should be happy, because now i can repair my computer HOOOOORAY -.-
But i had just one hour left in which i wanted to relax and play a game which was made impossible and yet for me unsolvable in one hour of free time left.

It would be very helpful to make the changes to my system undone so i could play for that one hour left and also help detecting which of the upgraded packages caused my sounddevice not to be detected anymore.

---

### Post by mustali on 2007-09-25
this worked for me. ```

cd /tmp/
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
tar xvf alsa-driver-1.0.14.tar.bz2
cd alsa*
./configure --with-oss=yes --with-cards=hda-intel
sudo make
sudo make install
sudo modprobe snd-hda-intel

```

I am running Fiesty on Dell Inspiron 630m laptop.

HTH

---

