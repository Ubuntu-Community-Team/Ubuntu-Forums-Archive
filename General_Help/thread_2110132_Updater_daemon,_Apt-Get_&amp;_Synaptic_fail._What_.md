---
title: "Updater daemon, Apt-Get &amp; Synaptic fail. What to do Now??"
date: 2013-01-29
forum: General Help
---

### Post by bogan on 2013-01-29
Update Manager daemon lost or broken, Apt-Get error( core dropped), Synaptic fails, multiple "internal System Error"s and "'XXXX' has closed unexpectedly" messages. What Now??

I searched the General Help forum back to early 2012 but all the Update Manager faults seem to be source list and network failures.

Has anyone any notion of what might cause all these faults at once??

It is not hardware as three other installations of 12.10, 12.04 & 10.04 are unaffected.

The problem was first noticed in a routine update, having updated the previous day, including Proposed updates,  without problems.
Software Updater got as far as: 'loading Software list', when it crashed with a Warning window saying something about: "Unable to control or use XXXXX" "The daemon has been lost. Probably the daemon is broken."

So I tried: ```
sudo apt-get update # and also:
sudo apt-get -f install --fix-broken # both gave:
Cxxx ERROR (core dropped)
```  [ I cannot remenber the 'Cxxx'error - 'Concatination'??]```
dpkg-reconfigure -a
```That ran with no output, it took seven minutes.
 
Synaptic Manager run from both a Terminal and the GUI flashed its window for half a second and then closed with no messages.

Ubuntu Software Center did not do anything visible.

During more than three hours, of many reboots and cold restarts, this continued with no change or progress. Every time Update-Manager was 'run' it went straight to the same Warning window, as it also did when run from a Terminal.

Eight hours later, rebooting, 'apt-get install update' worked, and so did:```
sudo apt-get install --reinstall update-manager
```After which everything seemed to be back to normal.  

Cross Fingers & Touch Wood, 24 hours later it is still OK.
I do not normally ask 'WHY?' questions, but I would really like to know what caused this apparently terminal failure.

Also, what else, if anything, could I have tried?

Chao!, **bogan.**

[ Ubuntu 12.10. 3.5.0-23-generic #35-i686 . Proposed PPA enabled.]

---

### Post by dino99 on 2013-01-29
its time to:

-deactivate the ppas  : sudo gedit /etc/apt/sources.list

-clean the system: clean/autoclean/autoremove/gtkorphan/bleachbit

- reconfiguring: sudo dpkg-reconfigure -phigh -a
  (can take a while, be patient & wait it end itself)

- reboot : sudo shutdown -R now

- and update

-cross fingers :)

---

### Post by bogan on 2013-01-29
> **dino99 said:**
> its time to:
-deactivate the ppas  : sudo gedit /etc/apt/sources.list
-clean the system: clean/autoclean/autoremove/gtkorphan/bleachbit
- reconfiguring: sudo dpkg-reconfigure -phigh -a
  (can take a while, be patient & wait it end itself)
- reboot : sudo shutdown -R now
- and update
-cross fingers :)Thanks for your prompt response. As I Posted, I did run:```
 dpkg-reconfigure -a 
```It had no effect. Your cmd gives:```
:~$ sudo -i
[sudo] password for alan: 
root@alan-MS-7318:~# dpkg-reconfigure -phigh -a
E: Command line option ‘p’ [from -phigh] is not known.
:~# 
```Which is what I got when I tried it previously, is there a syntax error??

How could I :>  -clean the system: clean/autoclean/autoremove/gtkorphan/bleachbitwhilst 'sudo apt-get xxx' gives an error??

Chao!, **bogan**.

---

