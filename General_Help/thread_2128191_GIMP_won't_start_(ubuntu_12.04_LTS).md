---
title: "GIMP won't start (ubuntu 12.04 LTS)"
date: 2013-03-22
forum: General Help
---

### Post by zaly on 2013-03-22
I tried installing new brushes (puttng the brush files in the .gimp-2.6/brushes folder) and when I restarted gimp it didn't open. I removed and reinstalled gimp but it still doesn't open.   Can anyone help me please?

---

### Post by r-senior on 2013-03-22
Could you try running gimp from a terminal and see what errors it shows? Just open a terminal window and type 'gimp'.

---

### Post by JonathanLloydMedia on 2013-03-22
I had some issues in 2.6 as well.  back up your fonts and brushes folder and remove gimp and try installing 2.8. if that doesn't work.  I don't know but maybe using purge command might help or maybe update sources and try a restart if you haven't tried yet.

---

### Post by ManamiVixen on 2013-03-22
Are you sure the brushes are not Photoshop Brushes? Also there are brushes and such for GIMP 2.8, so be sure it's not for that version as you have GIMP 2.6 installed.

---

### Post by ManamiVixen on 2013-03-22
If you want to use GIMP 2.8, zaly:
sudo add-apt-repository -y ppa:otto-kesselgulasch/gimp
sudo apt-get update
gimp gimp-data-extras gimp-plugin-registry

---

### Post by zaly on 2013-03-22
Thanks for the answers!


> **r-senior said:**
> Could you try running gimp from a terminal and  see what errors it shows? Just open a terminal window and type  'gimp'.

I got no result, the program didn't run and the terminal just went to a new line after a couple of seconds.


> **ManamiVixen said:**
> Are you sure the brushes are not Photoshop Brushes? Also there are brushes and such for GIMP 2.8, so be sure it's not for that version as you have GIMP 2.6 installed.

Yes, they were for gimp 2.6

> **ManamiVixen said:**
> If you want to use GIMP 2.8, zaly:
sudo add-apt-repository -y ppa:eek:tto-kesselgulasch/gimp
sudo apt-get update
gimp gimp-data-extras gimp-plugin-registry

I'll try installing 2.8 now after removing the non-functioning 2.6 I had reinstalled

------EDIT

it still doesn't work

I did

sudo apt-get remove gimp sudo apt-get update  sudo apt-get purge gimp libgegl* libbabl* 
sudo apt-get autoremove gimp gimp-plugin-registry
sudo add-apt-repository ppa:otto-kesselgulasch/gimp sudo apt-get update
sudo apt-get install gimp
gimp gimp-data-extras gimp-plugin-registry

I tried to run gimp from the dashboard, the icon appeared as if the program was loading then it disappeared in a few seconds.
When I type gimp in the terminal nothing happens (like before), it just goes to a new line.

---

### Post by ManamiVixen on 2013-03-22
Also to note, 2.6 brushes are backwards compatible in 2.8. and I meant "sudo apt-get install gimp gimp-data-extras gimp-plugin-registry"

---

### Post by zaly on 2013-03-22
> **ManamiVixen said:**
> Also to note, 2.6 brushes are backwards compatible in 2.8. and I meant "sudo apt-get install gimp gimp-data-extras gimp-plugin-registry"

So I made a mistake when installing? Since I typed that command? Do you think it compromised the installation? Should I repeat all of the commands I listed in my previous post or just  "sudo apt-get install gimp gimp-data-extras gimp-plugin-registry"?

Thanks for your answers

---

### Post by ManamiVixen on 2013-03-22
Just run  "sudo apt-get update && sudo apt-get install gimp gimp-data-extras gimp-plugin-registry" that will upgrade GIMP and install the extra stuff like more brushes, filters, and fu scripts.

My keyboard is crap and it usually screws up my typing without me realizing it sometimes, sorry.

---

### Post by zaly on 2013-03-22
I did that and tried opening it again opening a .jpg file but it didn't work, I tried launching it from the terminal and I got this error (about the .jpg it seems) in a separate window

[IMG]http://s8.postimg.org/zau1yhojp/Schermata_del_2013_03_22_19_36_55.png[/IMG]

[IMG]http://s23.postimg.org/z0rtfz7mz/Schermata_del_2013_03_22_19_37_16.png[/IMG]

the text after 'unreportable reason is 'there are obsolete versions of these packages. Upgrade the following packages and verify if the error is still present

[IMG]http://s9.postimg.org/7kntmttrj/Schermata_del_2013_03_22_19_37_22.png[/IMG]

---

### Post by zaly on 2013-03-22
I installed the three packages mentioned in the error report and then did a sudo apt-get upgrade and then opened again gimp but nothing has changed

---

### Post by zaly on 2013-03-30
Gimp 2.8 now works, the problem is solved.

It started working after I installed the updates from the update manager.


Thanks to everyone who replied to this thread.

---

