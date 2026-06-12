---
title: "Howto interrupt boot process for entering truecrypt passphrase?"
date: 2007-02-14
forum: General Help
---

### Post by arturh on 2007-02-14
Hi folks!

i'm looking for a way to automount my truecrypt volume (an encrypted filesystem), which interactivly asks for the volume passphrase to mount a tc volume as my home directory, before gdm launches.
i've set up my system for dual boot with windows xp, using the tcgina program to load my windows user profile from the tc volume, and would really like the same convienience on my ubuntu box.

With tcgina, your login password can be used to load the tc volume as well as logging into windows (given that both passwords are equal)... is it possible to tell gdm to do the same?
or if thats not possible, could i maybe otherwise interrupt the boot process at a given time, to be able to enter the password?

as a workaround i currently just switch to the console with ctrl+alt+f1 to login, start the script, enter the password, log out again, switch to gdm, and log in there... 
but it would be a lot nicer if i could just enter the volume pass on boot, and then normaly login to gdm

any help would be great!!

Artur

---

### Post by HDave on 2007-12-14
BUMP -- Anyone??

I am looking to do the exact same thing.  Been a TCGINA user on windows for 2+ years...dying to get it for Ubuntu/Linux....

---

### Post by arturh on 2007-12-14
hi,

i found a little workaround, i just disabled the autostart of gdm, log in via text console, start my tcmount script, which if I enter my password correctly starts gdm, where I need to login again.

cons:
2x login
text console login is afterwards still active


not perfect, but ...

Artur

---

### Post by HDave on 2007-12-14
Good idea!

Can you please share how you disabled the autostart of gdm?

After you mount the TC partitions, how do you start gdm?  Is it as simple as "sudo gdm"??

Thanks for your help

---

### Post by arturh on 2007-12-14
hi,

i can't remember the "correct" way of doing it, there is some script which does it automatically, but you can just delete all the files in the /etc/rc?.d/ folders with the command

sudo rm /etc/rc?.d/S*gdm*

after this command gdm won't be started automatically, but stopped when the computer shutdowns.


sudo /etc/init.d/gdm start

starts gdm

greetings from germany,
Artur

---

### Post by HDave on 2007-12-15
Danke Artur from the USA!

---

### Post by HDave on 2007-12-20
Hey -- want to give everybody a heads up that there is a great HOW-TO on how to do this...

[http://ubuntuforums.org/showthread.php?t=645247]("http://ubuntuforums.org/showthread.php?t=645247")

---

### Post by HDave on 2008-01-02
I found another approach to doing this that uses the PAM facility that comes with Ubuntu. It worked great:

[http://www.fstab.de/twiki/bin/view/Main/PamTruecrypt](http://www.fstab.de/twiki/bin/view/Main/PamTruecrypt)

Please note that in order to get it to compile I needed add:

Code:

#include <sys/syslog.h>

in the pam_truecrypt.c file.

Other than this little glitch it works exactly like TCGINA -- and reuses your login password to mount the truecrypt partition -- without storing your password anywhere!

Cool, eh?

---

### Post by ~LoKe on 2008-01-02
> **arturh said:**
> hi,

i can't remember the "correct" way of doing it, there is some script which does it automatically, but you can just delete all the files in the /etc/rc?.d/ folders with the command

sudo rm /etc/rc?.d/S*gdm*
Bad idea.  I would suggest installing sysv-rc-conf and disabling it through there.  If you're going to go the same route, I would suggest renaming it to at least have a backup.
```
sudo cp /etc/rc0.d/K01gdm /etc/rc0.d/k01gdm
```
```
sudo cp /etc/rc6.d/K01gdm /etc/rc6.d/k01gdm
```

---

