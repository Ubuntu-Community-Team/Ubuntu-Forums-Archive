---
title: "same /home partition/folder for Ubuntu and Mac OSX ?"
date: 2006-10-31
forum: General Help
---

### Post by ahaller on 2006-10-31
Hi

I will get me a macbook in a few days and would like to test Mac OSX on it. Or in other words i want to run OSX and Ubuntu Linux on one Machine. And heres my question:
Is it possible to use the same ~ folder for both OSs?
I assume that OSX can handle a ext3 partition, but it is possible to use the same /home directory and using, for instance, mozilla firefox on both systems? Or it is not recommend, because the settings of Linux and OSX can mess each other up or something? Or maybe permission stuff is likely to get obscure?

Bye,
 Andreas

---

### Post by autocrosser on 2006-10-31
I was using OSX up til a few months ago (have moved only to Ubuntu with a custom-built machine) & EXT3 support is still a bit "iffy"--I would keep a seperate dual-boot & look at sourceforge for the current status of the EXT3 plugin (can't remember the projects name right now--you could look back thru my past posts)

---

### Post by nikhilk on 2006-10-31
There was a similar post few days back. That guy had tried sharing /home between Ubuntu and some other Linux distro (Fedora if memory serves right).
Borrowing from Taurus here
"it is theoritacally possible but different distros handle things differently so you probably will run into trouble"

Most of the difference in in the way things inside the hidden folders (e.g. ".kde", ".gnome") in your /home are handled. If you want to share data, make a different folder/partition for it and share it.

---

### Post by ahaller on 2006-10-31
Thanks for your replies. Hm... OSX cannot handle ext3 natively :/ so this will be an issue. As far as i see there are two solutions:

ext2 for OSX: [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)
or
hfs+ for linux: [http://www.ardistech.com/hfsplus/](http://www.ardistech.com/hfsplus/)

Or do you have any more ideas?

So ext3 is out. EDIT: Or not? Because an ext2 driver can read ext3, it only does not use the journaling extenstion?

---

### Post by frenkel on 2006-10-31
It still is a problem, as Firefox on Mac OS X doesn't store it's settings in ~/.mozilla, but in ~/Library/Application Support/Firefox (which is the way to go in Mac OS)

---

### Post by ahaller on 2006-10-31
@frenkel Oh, maybe that is a good thing. Because so the two OSs are totally independent with their settings-handling, but i can use the same files and Folders (dokuments and stuff) with both systems.

---

### Post by Ramses de Norre on 2006-10-31
It might be safer to just make a symlink in the homedir of one of them pointing to the homedir of the other one. 
In that way you can easily access all your files and you wont run into problems with different styles of config file formatting.

---

