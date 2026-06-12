---
title: "Creative Audigy SE - Can't get OSS working"
date: 2007-01-21
forum: General Help
---

### Post by Zaggy on 2007-01-21
Hi, I'm using Ubuntu Dapper (6.06) and I got myself working multiple sounds at once and microphone with ALSA by doing this:

#Getting Alsa to work for Creative Labs SB Audigy LS on Dapper
#1
sudo apt-get install build-essential linux-headers-$(uname -r)
#
#2
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.12rc2.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.12rc2.tar.bz2)
#
#3
tar xvjf alsa-driver-1.0.12rc2.tar.bz2
#
#4
cd alsa-driver-1.0.12rc2
#
#5
sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=ca106 --with-oss=yes sudo make sudo make install
#
#6
sudo make
sudo make install
#
#7
modprobe snd-ca0106
#
#8
aplay -l
#
#9
#plug in your mic into the blue hole and your sound into green hole
alsamixer
#set your alsamixer like this screenshot:
[[IMG]http://img348.imageshack.us/img348/2221/alsamixerca1062ca.th.png[/IMG]](http://img348.imageshack.us/my.php?image=alsamixerca1062ca.png)
#
#if this all worked out, put the line snd-ca0106 in /etc/modules, this way, the module will be load at startup.

So far so good, but everything that needs OSS doesn't work.
For example, Teamspeak and Wine.

I tried poking around with ~.asoundrc and aoss, but neither works.

Does anyone have experience with this?



Some info about my soundcard:
> zaggynl@AMD3200L:~$ cat /proc/asound/cards
 0 [CA0106         ]: CA0106 - CA0106
                      Audigy SE [SB0570] at 0xb000 irq 177


> zaggynl@AMD3200L:~$ lspci | grep audio
0000:00:09.0 Multimedia audio controller: Creative Labs SB Audigy LS


---

### Post by Zaggy on 2007-01-22
/bump

---

### Post by Zaggy on 2007-01-23
Someone has to know more of this :(

---

### Post by costis on 2007-01-23
It's ca0106 instead of ca106... Thank you very much for the tutorial!...
> **Zaggy said:**
> 
sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=ca0106 --with-oss=yes> modprobe snd-ca0106> #if this all worked out, put the line snd-ca0106 in /etc/modules, this way, the module will be load at startup.

---

### Post by Zaggy on 2007-01-24
Doh, thanks for the correction, I'm glad this was useful to you!

---

