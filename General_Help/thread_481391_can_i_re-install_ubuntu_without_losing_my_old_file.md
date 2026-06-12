---
title: "can i re-install ubuntu without losing my old files on the partition?"
date: 2007-06-22
forum: General Help
---

### Post by mikealive on 2007-06-22
i recently ran into a huge problem with ubuntu, a login problem..and got little help, and no resolve.  it really ticks me off because i really want to make the switch full time from windows, but i can have ubuntu doing this to me, without  a fix or even a reason why this happen... [http://ubuntuforums.org/showthread.php?t=479545](http://ubuntuforums.org/showthread.php?t=479545)


but now i'm going to reinstall ubuntu and give it another try. i took ALOT to get my ubuntu working w/ my wireless card, and customized it to death.  

now my question is, can i reinstall ubuntu, and not lose all my old files?  like pictures, videos, music, documents, etc etc.  is there a way i can see my partition on windows so i can save the files to a disc if i have to?

thanks in advance,

mike

---

### Post by nymphaeles on 2007-06-22
If you know where your files are, maybe you can run a live CD, and copy your files over to a usb thumb drive.

---

### Post by Ultra Magnus on 2007-06-22
Hey - For your next install you might want to consider making a separate home directory - that way you can do a clean install and keep all your files!

---

### Post by rax_m on 2007-06-22
just to clear up what ultra magnus meant... 

i think create your /home directory on separate hd partition. That way whenever you upgrade you never lose your home directory. 

sorry.. but now sure about your prev post.

---

### Post by Ultra Magnus on 2007-06-22
sorry - being totally retarded! - yep what I meant to say was make a separate partition for the /home - its pretty straight forward with the installer.

---

### Post by mikealive on 2007-06-22
ok thanks alot guys.  so still no luck on figuring out whats wrong with my old problem right?  [http://ubuntuforums.org/showthread.php?t=479545](http://ubuntuforums.org/showthread.php?t=479545)

i'm looking forward to a fresh install.  it should be alot easier to work w/ ubuntu, now that i have a better ideao of what im doing.

---

### Post by Silenus on 2007-06-22
How do you tell if home is a seperate partition becuse I have / for root, and then /home. I would guess it's not seperate, is there a way to change that without an install?

---

### Post by merlinus on 2007-06-22
In a terminal:

```
 
df-h

```If one of the partitions is listed as mounted on /home, then it is a separate one.

-merlin

---

### Post by Silenus on 2007-06-22
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             109G   26G   78G  25% /
varrun                248M  224K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
procbususb            248M  120K  248M   1% /proc/bus/usb
udev                  248M  120K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   33M  215M  14% /lib/modules/2.6.20-16-generic/volatile
george@george-desktop:~$ 


Guess not, I was reading 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
and saw a way to create a new home partition in use of a live cd, is this the correct way or is there a better way?

---

### Post by merlinus on 2007-06-22
I used those instructions to create a /home partition after my first installation.

Since, then, I make sure to create this on all other computers from the very beginning.

Good luck!

-merlin

---

