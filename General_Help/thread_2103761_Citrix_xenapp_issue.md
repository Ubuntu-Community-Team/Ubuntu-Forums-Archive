---
title: "Citrix xenapp issue?"
date: 2013-01-11
forum: General Help
---

### Post by digimark on 2013-01-11
Hi All

Amhaving a bit of an issue...I installed the xenapp/citrix client

sudo apt-get install libmotif4:i386

this installed no problem.

However when i try to tell firefox to use

sudo ls -al /usr/lib/ICAClient/wfica

to run it....nothing.....this file does not exist anywhere on my system....ive run a general search for it but nothing.

I am following instructions from 

[https://help.ubuntu.com/community/CitrixICAClientHowTo#Citrix_ICA_Client_12_on_Ubuntu_12.04_64-bit](https://help.ubuntu.com/community/CitrixICAClientHowTo#Citrix_ICA_Client_12_on_Ubuntu_12.04_64-bit)

and

[https://help.ubuntu.com/community/CitrixXenAppPlugin](https://help.ubuntu.com/community/CitrixXenAppPlugin)

Am I missing something here? 

Many thanks

/M

---

### Post by digimark on 2013-01-11
Hi All

Amhaving a bit of an issue...I installed the xenapp/citrix client

sudo apt-get install libmotif4:i386

this installed no problem.

However when i try to tell firefox to use

sudo ls -al /usr/lib/ICAClient/wfica

to run it....nothing.....this file does not exist anywhere on my system....ive run a general search for it but nothing.

I am following instructions from 

[https://help.ubuntu.com/community/Ci...u_12.04_64-bit](https://help.ubuntu.com/community/Ci...u_12.04_64-bit)

and

[https://help.ubuntu.com/community/CitrixXenAppPlugin](https://help.ubuntu.com/community/CitrixXenAppPlugin)

Am I missing something here? 

Many thanks

/M

---

### Post by digimark on 2013-01-11
go here to get the client

[http://receiver.citrix.com/](http://receiver.citrix.com/)

I used the 32 bit client....works!

---

### Post by Steeperton on 2013-01-11
> **digimark said:**
> 
sudo ls -al /usr/lib/ICAClient/wfica


This is a terminal instruction to identify where wfica is located. When you get the "open wth..." dialogues in firefox (for the .ica file), navigate to /usr/lib/ICAClient, and select wfica to open the .ica file.  This assumes you've already downloaded and installed the citrix receiver .deb file from the citrix site (I'm using 64bit, without issue).

All should be fine then.

---

### Post by Toz on 2013-01-11
Duplicate threads merged.

---

