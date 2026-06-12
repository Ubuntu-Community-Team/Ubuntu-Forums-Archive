---
title: "No GCC/Cant Boot Windows?"
date: 2006-07-09
forum: General Help
---

### Post by kLOTTiS on 2006-07-09
I have two problems

1) I cant seem to get gcc and make working, I have reinstalled ubuntu and its still not working? I have updated everything, Can anyone help?

2)I cant boot into windows with grub, I have installed grub now over the MBR, as previously I had installed Ubuntu when Windows was not present, however it still wont boot? Can anyone please help? I really like Ubuntu and i dont want to give up on it AGAIN! [-o<

---

### Post by Dr. Nick on 2006-07-10
for make/gcc have you installed build-essentioal?
[B]
sudo aptitude install build-essential
[/B]
Whats wrong with windows?  Do you just not have a entry in grub for it?
look at the file /boot/grub/menu.lst

Thier is a example in their for how to boot XP when xp is on the 1st partiton

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive

---

### Post by DJ Scribblinni on 2006-07-10
To answer the first question I'll need to ask a quick question, is gcc and build essential installed? If not there goes some ```
sudo apt-get install build-essential
```
that should include everything needed to build and compile packages.  If perhaps it is installed already....sorry dude, I can't exactly help ya any further.
 
For the second question, you'll need to provide a bit more info.  Is windows listed in the GRUB selection menu.  Is there an error provided that we can take a gander at.  Until then...

---

### Post by kLOTTiS on 2006-07-10
[I]sudo aptitude install build-essential
**[Asks for Password]**
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/I]

does that say much?

and for the booting menu.lst says (for the windows bit)
[I]
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1[/I]

Ubuntu is on Primary
Windows is on Slave

---

### Post by kLOTTiS on 2006-07-10
> **DJ Scribblinni said:**
>  ```
sudo apt-get install build-essential
```

[I]shaun@ubuntu:~$ sudo apt-get install build-essential
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/I]

---

### Post by Dr. Nick on 2006-07-10
Close synaptic if open, It will cause that error

I am not sure how to troubleshoot XP being on slave though.

---

### Post by DJ Scribblinni on 2006-07-10
For the first part nothing happened becuase two processes are keeping any package from installing.  Close synaptic, and re run the sudo apt-get install build-essentail.  

I'm out of the loop with the windows boot.

You quick, I'm recieving emails as I type this...

---

### Post by Dr. Nick on 2006-07-10
Maybe read this for windows/grub
[http://ubuntuforums.org/showthread.php?t=184947&highlight=grub+slave+window](http://ubuntuforums.org/showthread.php?t=184947&highlight=grub+slave+window)

---

### Post by kLOTTiS on 2006-07-10
> **Dr. Nick said:**
> Close synaptic if open, It will cause that error





I dont really know that much about linux but im pretty sure that synaptic is not open, ive checked the system monitor, what does it do?

---

### Post by Dr. Nick on 2006-07-10
synaptic is a graphincal version of the apt-get command.

try this from a terminal

sudo killall synaptic
sudo killall apt-get

---

### Post by kLOTTiS on 2006-07-10
> **Dr. Nick said:**
> 
sudo killall synaptic
sudo killall apt-get

shaun@ubuntu:~$ sudo killall synaptic
synaptic: no process killed
shaun@ubuntu:~$ sudo killall apt-get
apt-get: no process killed
shaun@ubuntu:~$

---

### Post by DJ Scribblinni on 2006-07-10
I'm assuming your running GNOME.  I'm wondering if the update manager is interfering with something also.  I am almost inclined to tell to reboot real quick.  Then immediately just go ahead and run those wonderful commands we stated earlier.  Otherwise I really don't know what could be causing that error especially from a fairly clean install.

---

### Post by kLOTTiS on 2006-07-10
Yes I am running GNOME, and I will try rebooting now, I apreciate all the help from you guys, even if i cant get it working, i might try downloading 6.06

---

