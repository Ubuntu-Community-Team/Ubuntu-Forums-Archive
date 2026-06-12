---
title: "Gimp 2.4"
date: 2007-11-24
forum: General Help
---

### Post by measekite on 2007-11-24
I just installed Gimp 2.4 under Windows and it looks better than Gimp 2.x.

I would like it to run under Feisty 7.04.  I do not, at the present time want to upgrade to 7.10.  My preference would be to skip Gutsy and go with the next version.

Apparently, the powers to be (unless they can be persuaded) are not going to update the Feisty repositories.  I do not know why.

[COLOR=Magenta]**So I ask:**[/COLOR]

Has anybody successfully installed Gimp 2.4 under Feisty.  If that is the case would you please post a detailed howto for a person who does not know C or the C compiler.

My second question is how do you email the powers to be so one can request that Gimp 2.4 be put in the repositiory.

---

### Post by daengbo on 2007-11-24
The most straightforward way to get Gimp 2.4 is to download the source, type the following commands in a terminal,
sudo apt-get install build-essential
sudo apt-get install build-dep gimp
Then unpack the source and compile following the directions in the source.

There may be one already compiled and in .deb format for Feisty on the web, but I don't like to trust third-party repositories.

---

### Post by measekite on 2007-11-24
> **daengbo said:**
> The most straightforward way to get Gimp 2.4 is to download the source, type the following commands in a terminal,
sudo apt-get install build-essential
sudo apt-get install build-dep gimp
Then unpack the source and compile following the directions in the source.

There may be one already compiled and in .deb format for Feisty on the web, but I don't like to trust third-party repositories.

You are using Gutsy.  I am using Feisty.  Feisty does not have 2.4 in the repository so I do not think that apt_get install will get that version but rather 2.2.  I have read posts that people who have tried to compile 2.4 for Feisty have had much trouble and were not successful.  Some said they have tried to find dependencies and were still not able to get it running.

---

### Post by daengbo on 2007-11-25
Ummm. I guess I wasn't clear enough. The apt commands just install the dependencies you will need for compiling. Then you need to go to the Gimp website and download the sources for Gimp 2.4 (and anything else they recommend). Unpack, read the README file, and compile following those instructions.

---

### Post by FuturePilot on 2007-11-25
You might want to check this out
[https://help.ubuntu.com/community/GIMP2.4-on-Feisty]("https://help.ubuntu.com/community/GIMP2.4-on-Feisty")

---

