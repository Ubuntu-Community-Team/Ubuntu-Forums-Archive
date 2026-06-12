---
title: "Ubuntu 13.04 installed for 5 weeks no problem then all gone but the basic programme"
date: 2013-06-17
forum: General Help
---

### Post by alreston on 2013-06-17
Please help Ubuntu 13.04 was installed and running well then I switched on and all was gone files pictures downloads etc. I was back to installed 13.04 even the resolution I had set was gone, what would cause this ?
Alreston

---

### Post by Bashing-om on 2013-06-17
[COLOR=#000000]alreston;
Did you install onto a USB device, and "persistence" not provided for ?
A bit more info in this respect will help us help you.
[/COLOR][INDENT][COLOR=#000000]
ubuntu, operating system of choice

[/COLOR][/INDENT]

---

### Post by alreston on 2013-06-17
I installed too my  pc which I have two hardrives one for Linux and one for Microsoft I like to keep them separate. I installed 13.04 using disc from Linux shop. I have used Ubuntu for years this has never happend before.

---

### Post by Bashing-om on 2013-06-17
[COLOR=#000000]alreston;

I too have never encountered a situation as this... All I can think of is there are multiple users on the machine and somehow the "profiles" have become confused... What is different if you log into the guest account from normal  ?

Any file system errors reported ? Journal file system should never loose track of a file, and in the event of an error the operating system remounts to read only or maybe forces a file system check. 
This is not happening...-> file system is intact !

Might try resetting a couple of you preferences, save and reboot... do the changes stick ?
[/COLOR][INDENT=2][COLOR=#000000]
tough to isolate

[/COLOR][/INDENT]

---

### Post by alreston on 2013-06-18
Happy ubutu'n ,Thank you for your  quick responce I think I must have lost my reply to you so here it is again I am the only user on my PC ! it is a problem. I have now removed and started again with a fresh install of 13.04  should it happen again I will submit another post on the subject.
Thank you again
Alreston

---

### Post by ibarnon on 2013-10-04
Exact same thing just happened to me. **EVERYTHING IS GONE** and seems to show like it was a fresh install of ubuntu 13.04. This is very scary. I mean ALL files are wiped out and it happened almost instantly. 

Few things I was doing before this happened:
=> emptied out trash
=> unzipped an eclipse tar.gz file

I don't know how to recover anything, the only good thing is this that I have a backup from a week ago.
Some details:
-> Ubuntu 13.04 64bit, uninstalled amazon lens, uninstalled ubuntu-one
sudo apt-get remove unity-lens-shopping
[COLOR=#333333][FONT=Ubuntu]sudo apt-get purge ubuntuone-client python-ubuntuone-storage*[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR]-> Dell Latitude E6410 core-i5 4GB
-> Single user account
-> One partition
I'm wondering if its due to the fact the I removed ubuntu-one. Please help.

---

