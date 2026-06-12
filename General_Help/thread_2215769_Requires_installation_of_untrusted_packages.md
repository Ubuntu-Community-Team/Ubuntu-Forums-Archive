---
title: "Requires installation of untrusted packages"
date: 2014-04-08
forum: General Help
---

### Post by sandman55 on 2014-04-08
Hi Guys when I install updates on mu Ubuntu 12.04 I get two files to update as you can see in the attached pic "libmagic1" and when I do, I get a prompt saying "requires installation of untrusted packages" this is a fairly new installation and the only thing that I can think that I have installed is my Epson XP-600 printer.  I let Ubuntu find the drivers and install them for the printer.  So far only the printer works and not the scanner.  Should I uninstall the printer and find better drivers? Can anyone help me with this problem?

---

### Post by anaconda on 2014-04-08
Your printer has nothing to do with that error, so dont remove its driver..

Ubuntu's package repositories (the places, where you install programs to ubuntu) are signed with a pgp key, which is used in verifying that you are indeed installing programs from a trusted source. and not from any untrusted place.

It seems, that you might have lost that key. or added a new repository without adding its key.
You should add the key again.

99.99% of the times these kind of problems are with the pgp key missing on your end.  And only very very rarely (if ever) someone is trying to get you to install some malicious code and pretend that he is the real ubuntu repository...

I wouldnt worry.  . I would install the package anyway. and then try to repair the missing key problem.. but that is just me.

---

### Post by sandman55 on 2014-04-08
Thanks anaconda I have only been applying updates from the normal update centre I go into system settings then click details and I get the prompt you see in the pic I posted. Also updates come in automatically and I apply them.  Maybe one of my updates have corrupted the key.  I cant install the package it is a loop of download try to install then I get the message "requires the installation of untrusted packages" I close that prompt and it downloads the update again and it goes on till I close it all.  I could probably do it in terminal but I don't know the code and I don't know how to get and apply the key.

---

### Post by slickymaster on 2014-04-08
Most probably it's due to the missing of some GPG keys like anaconda stated.

If you want to fix this, just open a terminal window and run the following command:```
sudo apt-get update

```You will get an error saying that some public key is not available (take a note of the key string  after the NO_PUBKEY; eg:E6B6DB186A68F637 )
To install the missing public keys, run the command below for each missing key. Replace XXXXXX with the key obtained previously```
sudo apt-key adv --recv-key --keyserver keyserver.ubuntu.com XXXXXXXXX
```After that just run```
sudo apt-get update
```and everything should be ok.

---

### Post by sandman55 on 2014-04-08
Thanks for your help guys but this morning my updates came in and I was showing my sister what was happening and to my surprise Ubuntu updated as it should without me going into Terminal and after that it applied other updates so it seems to have fixed itself.

EDIT: perhaps I should wait for updates and not go into system settings and then details and look for updates.

---

