---
title: "[SOLVED] package manager not opening"
date: 2008-01-28
forum: General Help
---

### Post by sandclock on 2008-01-28
Hi 
When i try to start package mangager it doesnt open. doesnt show any error but doesnt open at all nothing happens any ideas?
Regards
Nik

---

### Post by Majorix on 2008-01-28
Can you please run "synaptic" from the terminal and post the output here? Maybe it doesn't spit out any errors in the GUI but shows them in the background...

---

### Post by sandclock on 2008-01-28
> **Majorix said:**
> Can you please run "synaptic" from the terminal and post the output here? Maybe it doesn't spit out any errors in the GUI but shows them in the background...

this is what i got in terminal 

root@nikhil-desktop:~# gksudo synaptic
root@nikhil-desktop:~# 

thanks and regards
Nik

---

### Post by Majorix on 2008-01-28
Hmm no errors there either... Odd.

You should try purging the synaptic and reinstalling it, like this:
```
sudo apt-get --purge synaptic; sudo apt-get install synaptic
```
and see if that helps.

---

### Post by sandclock on 2008-01-28
here is what i got for that one 
--------------------xxxxxxx----------------------
root@nikhil-desktop:~# sudo apt-get --purge synaptic; sudo apt-get install synaptic
E: Invalid operation synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
synaptic is already the newest version.
The following packages were automatically installed and are no longer required:
  libsilc-1.0-2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 186 not upgraded.
---------------xxxxxxxxxxxx---------------
Any Ideas?
Regards
Nik

---

### Post by sandclock on 2008-01-28
Bump Bump !!!
anyone?

---

### Post by Majorix on 2008-01-28
> **sandclock said:**
> here is what i got for that one 
--------------------xxxxxxx----------------------
root@nikhil-desktop:~# sudo apt-get --purge synaptic; sudo apt-get install synaptic
E: Invalid operation synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
synaptic is already the newest version.
The following packages were automatically installed and are no longer required:
  libsilc-1.0-2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 186 not upgraded.
---------------xxxxxxxxxxxx---------------
Any Ideas?
Regards
Nik

Oops sorry my mistake. I forgot the "remove" keyword. It should read:
```
sudo apt-get remove --purge synaptic; sudo apt-get install synaptic
```
I think too linguistic that I thought "purge" would suffice :p

Anyways sorry again. Try this and report back.

---

### Post by sandclock on 2008-01-28
heyy man thanks a lot it worked perfectly
no probs at all
thanks a lot Regards
Nik

---

