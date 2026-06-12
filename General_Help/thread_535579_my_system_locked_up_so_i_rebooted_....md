---
title: "my system locked up so i rebooted ..."
date: 2007-08-26
forum: General Help
---

### Post by Gas_Man on 2007-08-26
and this is the error message:

kinit: name_to_dev_t (/dev/disk/by-uuid/195c....real long number.....e5e76)=hda5(3,5)

kinit: trying to resume from dev/disk/by-uuid/195c....real long number....e5e76

kinit: no resume image doing normal boot

and i see that mystical standard getty login screen ...  no gnome, just a regular tty login prompt


amd64 3500 - the system has worked fine for the last three months and then i tried to install UT.

it installed fine. I ran a shell script to run ut and it complained about libX11.so,6 

so i symlinked the sucker ... or so i thought. Only i botched it and scorched the original libX11.so.6. in /usr/lib/ 

how do i get it back or do i have to flatted and reinstall Ubuntu again? 
or is there another way to boot into my Ubuntu



YES I"M A NEWBIE!:lolflag:

---

### Post by merlinus on 2007-08-26
Can you login at the prompt?

What about trying Recovery Mode from the grub menu?

-merlin

---

### Post by jamvegan on 2007-08-26
You could try:
```
sudo apt-get install --reinstall libX11-6
```

---

### Post by Gas_Man on 2007-08-26
> **merlinus said:**
> Can you login at the prompt?

What about trying Recovery Mode from the grub menu?

-merlin

yes i can but i get the same kinit error message,  right now i'm using livecd

---

### Post by merlinus on 2007-08-26
In your first post, you said that a tty prompt came up.  Can you login?

If not, you might try this:

sudo dpkg-reconfigure gdm

-merlin

---

### Post by Gas_Man on 2007-08-26
> **jamvegan said:**
> You could try:
```
sudo apt-get install --reinstall libX11-6
```

tried that but i get "could not resolve host: ca.archive.ubuntu.com"

---

### Post by Gas_Man on 2007-08-26
> **merlinus said:**
> In your first post, you said that a tty prompt came up.  Can you login?

If not, you might try this:

sudo dpkg-reconfigure gdm

-merlin

yes i can login as root or one of my two users
i'll try that.

thanks

---

### Post by Gas_Man on 2007-08-26
i get the following error message:
invoke-rc.d: initscript gdm, action "reload" failed

---

### Post by jamvegan on 2007-08-26
> tried that but i get "could not resolve host: ca.archive.ubuntu.com"
This suggests that you are either not connected to the network, or at least are not communicating with your Domain Name Server.  Is the machine, as far as you know, connected to the Internet?

---

### Post by Gas_Man on 2007-09-01
> **Gas_Man said:**
> and this is the error message:

kinit: name_to_dev_t (/dev/disk/by-uuid/195c....real long number.....e5e76)=hda5(3,5)

kinit: trying to resume from dev/disk/by-uuid/195c....real long number....e5e76

kinit: no resume image doing normal boot

and i see that mystical standard getty login screen ...  no gnome, just a regular tty login prompt


amd64 3500 - the system has worked fine for the last three months and then i tried to install UT.

it installed fine. I ran a shell script to run ut and it complained about libX11.so,6 

so i symlinked the sucker ... or so i thought. Only i botched it and scorched the original libX11.so.6. in /usr/lib/ 

how do i get it back or do i have to flatted and reinstall Ubuntu again? 
or is there another way to boot into my Ubuntu



YES I"M A NEWBIE!:lolflag:
thanks for all the suggestions, i've tried most of them with no success, but the problem is resolved.
I basically reinstalled the os from the live cd, resized the partition, imported my old user accounts, logged in and proceeded to copy all relevaent data from the resized partition to dvd ... then i flattened the hdd and reistalled from scratch ... 

:)
thanks all ...

---

