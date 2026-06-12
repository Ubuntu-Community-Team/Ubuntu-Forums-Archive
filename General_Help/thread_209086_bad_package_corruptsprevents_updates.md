---
title: "bad package corrupts/prevents updates"
date: 2006-07-04
forum: General Help
---

### Post by torfinn on 2006-07-04
1. Clicking icon in upper right corner indicating software updates.
Find that 1 update is waiting: xserver-xorg-input-mouse

2. Clicks 'Install Updates' to start install
 
After download and some activity I get:

Changes applied, Update is complete, but not all changes and updates succeded....

I expand terminal and find: 
dpkg: parse error, in file `/var/lib/dpkg/available' near line 22311 package `language-pack-xh-base':
 field name `
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

I say close and nothing seems to have happened, the 'xserver-xorg-input-mouse' is still there, ready to be installed -  so it goes in loop. :cry: 

The error:
 [I]dpkg: parse error, in file `/var/lib/dpkg/available' near line 22311 package `language-pack-xh-base':
 field name `
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:[/I]

came yesterday, when unsuccessfully trying: $ sudo apt-get install lyx
I have tried: $ sudo apt-get clean lyx

How do I remove the source/cause of this error?
Torfinn

---

### Post by torfinn on 2006-07-04
answering it myself:    $ sudo dselect update 
(found after googling the error message)

but I had to do it twice, because first time the update in upper right corner
had similar complaint about a different package. On next try
it worked - but I am not convinced the "mouse" update was a good 
thing, I lost my mouse - tried to restart the X server, ctrl+alt+backspace
but no mouse. Eventually after a full restart it took long before my mouse 
was found - and then a speedy one 
cheers
t.

---

### Post by bbarrons on 2006-07-11
I also had the same problem. Your answer solved my problem. Thanks for the research
Bill

---

