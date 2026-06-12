---
title: "Missing File"
date: 2007-06-04
forum: General Help
---

### Post by Zihub on 2007-06-04
I duel boot Windows XP and Ubuntu 7.04. The other day windows randomly decided to put a temporary cache folder into the root directory of my Ubuntu distro. I then booted ubuntu and it decided that that file was a part of the OS. when i booted windows again it deleted the folder and so now whenever i boot ubuntu it tries to find this file and so stops half way through booting to open a maintenance shell saying that it cant find the folder. i hit Ctrl-D and it carries on booting.

can anyone help me with this and convincing ubuntu that this folder shouldnt be there?

having re-read the error screen i discovered that it had created a log of the incident saying:

Log of fsck -C -R -A -a 
Tue Jun  5 09:54:44 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Unable to resolve 'UUID=5dda7a37-2031-4ac6-9b9a-5530f53f19fa'

fsck died with exit status 8

Tue Jun  5 09:54:44 2007
----------------

---

### Post by jimbob on 2007-06-04
Something is seriously wrong to my way of thinking if Windoze can have the ability to write something from its own partitiion into your Ubuntu root partition.

Are you sharing a partition in XP with Ubuntu?  How do you know XP wrote this file? What is the name of the file?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by Zihub on 2007-06-04
im using ext2 (or something like that) so that i can write to my linux partition when in windows. 

i recognised the folder as a temporary cache file from windows. i cant remember what its called, its something really long and with loads of random letters and numbers.

---

### Post by nerdman978 on 2007-06-04
I formatted my Linux partition to ext3 and I can't write to my linux folders while in windows. I didn't think windows was able to write and save files to the the linux partition because it "doesn't have permissions" or something like that (thats the message i get when I try to write files to my windows stuff while in linux).

---

### Post by Zihub on 2007-06-04
my mate got this program for me so that i could write to the linux partition when in windows. Its called something like "ext2 IFS 1.10c for windows XP"

---

