---
title: "apt-get froze during java stack installation"
date: 2007-04-23
forum: General Help
---

### Post by tbird1988 on 2007-04-23
I tried to download JDKG, Glassfish, Netbeans5.5 and JavaDB as these are the apps that I believe were required. Everything was going fine until I reached the post-installation script to confirm with Sun MC. Apt wouldn't let me go to that site. I freeze at this prompt every time I go back into apt to finish Netbeans.

E: netbeans 5.5: subprocess post-installation script returned error exit status 1

I upgraded to Feisty two days ago with no problem. I rm'd /var/lib/dpkg/lock with no success. Should I just go back and remove these packages. I thought that there would be one package that installed these automatically. Any help with this would be appreciated as I don't really know how apt-get works .

 Thanks...

---

### Post by indytim on 2007-04-23
Try:

sudo apt-get -f install
sudo dpkg --configure -a

Good Luck,

IndyTim

---

### Post by tbird1988 on 2007-04-23
Thanks...will try...Kent... in Kansas...

---

### Post by tbird1988 on 2007-04-23
Hah!.. Maybe best to start over...that request returned

 E: Subprocess /usr/bin/dpkg returned an error code (1)

Trying though, I just don't want to give up and start from square one (I've done that too much and you don't learn that way. I've been around since Breezy but never got into the system this deeply)... Here's the full output from my console... I'm learning so much

Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of NetBeans IDE
dpkg: error processing netbeans5.5 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 netbeans5.5
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

