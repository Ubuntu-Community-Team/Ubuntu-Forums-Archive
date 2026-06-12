---
title: "renaming a folder on a network shared external HDD"
date: 2017-06-07
forum: General Help
---

### Post by rob141 on 2017-06-07
Hello, 

i have a networked shared external HDD connected on my router and that works ok.

The problem i have just found out is that some folders in there have spaces inbetween the folder name. For example:  Ubuntu backp 

Witch this folder is the files and folder that i did not want to loose before i install this latest version on Ubuntu. 

The problem is that within the GUID, the option rename is greyed out and in the command prompt, if i do sudo mv Ubuntu backup Ubackup for example ) it wont let me and i get the error saying that Ubackup is not a directory.


I am pretty sure that if i would just physically connect the HDD directly to my laptop i would probably be able to rename the folders i want but i think i rather learn that there is a way to do it in command promt somehow.   

its good learning ;)

---

### Post by TheFu on 2017-06-08
```
sudo mv "Ubuntu backup" Ubackup
```
or use tab completion to get the {space} escaped automatically.  If you find yourself typing more than 3 characters at a time in a terminal, then it is likely you are doing it the hard way. Learn about tab completion - for this skill, watching a few youtube videos really will open your eyes. Make using it a habit. No more misspelled commands, paths, filenames. Often, it will help with command options too - just depends on the specific command. "bash-completion" is the package which adds more completion commands and makes life easier. I think it is installed on all non-minimal Ubuntu installs.

Spaces are a major hassle for any scripting. I learned that long ago and do not use spaces in any filenames or directories.  "Ubuntu_Backup" would be the name I used, if I wanted it to appear that way.

A few other comments - mainly from personal experience over the years.
* I hope you don't need to use sudo for that command. Without seeing the permissions, I cannot tell.
* Plugging any storage into an internet facing router is a poor security choice unless you intend to share all the files with the entire internet. Forget what the router claims. It has many bugs which make those claims next to worthless.  If the router is just inside your home LAN - perhaps to keep the kids/guests on a different network from responsible adults, then I wouldn't worry too much.

---

### Post by rob141 on 2017-06-08
> **TheFu said:**
> ```
sudo mv "Ubuntu backup" Ubackup
```
or use tab completion to get the {space} escaped automatically.  If you find yourself typing more than 3 characters at a time in a terminal, then it is likely you are doing it the hard way. Learn about tab completion - for this skill, watching a few youtube videos really will open your eyes. Make using it a habit. No more misspelled commands, paths, filenames. Often, it will help with command options too - just depends on the specific command. "bash-completion" is the package which adds more completion commands and makes life easier. I think it is installed on all non-minimal Ubuntu installs.

Spaces are a major hassle for any scripting. I learned that long ago and do not use spaces in any filenames or directories.  "Ubuntu_Backup" would be the name I used, if I wanted it to appear that way.

A few other comments - mainly from personal experience over the years.
* I hope you don't need to use sudo for that command. Without seeing the permissions, I cannot tell.
* Plugging any storage into an internet facing router is a poor security choice unless you intend to share all the files with the entire internet. Forget what the router claims. It has many bugs which make those claims next to worthless.  If the router is just inside your home LAN - perhaps to keep the kids/guests on a different network from responsible adults, then I wouldn't worry too much.



Thank you so much for that info, it worked like a charm. Now i was able to rename all my folder who had spaces in them.  The tab is my new best friend  loll  

As for my sharing, i kinda have no choice to plug my external HDD to my router because it is shared between my laptop ( ubuntu ) over wifi and my Raspberry Pi 3 witch is physically connected to my router with RJ45.   

I have the latest firmware on it and i have setup a mac filter on it too. I think it is as much secured as this router can be. I dont even broadcast the name.  

Again, thank you so much for the help, you made my day  ;)

---

### Post by TheFu on 2017-06-08
You are welcome, but you DO have a choice.  You've just decided that convenience trumps security.
You can connect the USB HDD to the Pi and have the Pi share the storage via NFS with your Ubuntu machine or do it the other way around, have the HDD connected to the Ubuntu machine and shared with the Pi, but wifi should be avoided whenever possible.

MAC filters mean nothing, BTW.  MACs that are allowed in are broadcast with every packet, in the clear.  Similar for the SSID. 

IMHO.

---

### Post by rob141 on 2017-06-08
> **TheFu said:**
> You are welcome, but you DO have a choice.  You've just decided that convenience trumps security.
You can connect the USB HDD to the Pi and have the Pi share the storage via NFS with your Ubuntu machine or do it the other way around, have the HDD connected to the Ubuntu machine and shared with the Pi, but wifi should be avoided whenever possible.

MAC filters mean nothing, BTW.  MACs that are allowed in are broadcast with every packet, in the clear.  Similar for the SSID. 

IMHO.


Yeah, i did not think of that.  I would need to change the path in my Pi for my roms though because now they have the network path but if i connect it directly to it then the path changes.  i will try that this evening.

It may be more secure like you say.  thx for the advice  ;)

---

