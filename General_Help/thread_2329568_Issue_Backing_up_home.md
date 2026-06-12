---
title: "Issue Backing up /home"
date: 2016-07-03
forum: General Help
---

### Post by Richard_Alexander on 2016-07-03
I am finding it very frustrating trying to backup my /home on my laptop.  I have an instance of vbox installed obviously in my home directory.  When I try to run a back-up through the built-in backup client or even trying to tar it up to a mounted NAS drive it takes forever (days) and the system along with the backup will suspend.  Is there a better way?  I really want to backup my data but, it should not take that long.  I must be doing something wrong.  I am a new user to Ubuntu so, dumbness possibly playing a serious role here.  Can someone point me in the right direction?

---

### Post by HermanAB on 2016-07-03
Howdy,

The best way to backup anything is with rsync using a one line script.  Most backup programs are graphical front ends for rsync, that makes it more difficult to use.

A simple way to control what will be backed up, is to put a size limit on the files, to avoid making backups of ISO files and virtual machines.  The following is a script from my Mac.  It should work for you too:

#! /bin/bash
rsync -avz --progress --delete --max-delete=10 --max-size=20M ~/Documents /wherever/NAS/directory/

Read the rsync man page for details.  The above one liner will help you to understand it.

I do backups to an encrypted USB memory stick.  The above one liner is on the stick.  So I simply plug it in, get a pop-up for the password, then the file browser pops up and I click the script to run it and that's it.

---

### Post by Richard_Alexander on 2016-07-03
Herman,
  Thanks for the reply.  I will give it a shot.  I really want to make Ubuntu work because I like it so much.  I just wish I could get everything to work without a stupid Windows VM.  :)

---

