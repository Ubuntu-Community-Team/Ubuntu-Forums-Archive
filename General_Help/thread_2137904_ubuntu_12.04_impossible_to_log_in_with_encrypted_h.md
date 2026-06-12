---
title: "ubuntu 12.04 impossible to log in with encrypted home folder"
date: 2013-04-22
forum: General Help
---

### Post by Gingalone on 2013-04-22
I got a new Samsung laptop (ultrabook series 5) on which I installed Ubuntu 12.04 LTS with encrypted home folder.
After some basic installations everything worked OK (for a couple of weeks) but this morning when entering my user and pw at boot time (lightdm) the system bounces back to the initial login screen. To solve this trouble I tried some method suggested here (Ubuntu forums) but I see the encrypted home folder makes things more complex and those methods don't work...
What can I do?

---

### Post by diegolopmon on 2013-04-22
[COLOR=#333333][FONT=Ubuntu]Maybe you should add the boot option "user-setup/encrypt-home=true" to the kernel boot parameters.[/FONT][/COLOR]

---

### Post by Gingalone on 2013-04-23
Tried that, no effect: no login.
Thanks anyway...
Any other help?

---

### Post by Gingalone on 2013-04-26
At least I outlined the problem: after having had a long review in various Ubuntu web support sites, It looks that 'freezing login screen' trouble is quite a frequent one.
At the end I guessed my problem arose from the fact that I had just changed my login passwd and at the following boot the login screen (lightdm) was stuck because the system could not update my keyring file because the relative file was in the encrypted home folder. 
So, I got a terminal (Alt-Ctrl-F1) and changed my passwd to the old one. The following reboot was perfect!
Then I tried to changed my passwd again, changing also the keyring passwd in the same session, using the graphical 'Passwords and Keys' application. BUT at the following boot the problem was again there.....
SO, I would like to know a way the change the keyring passwd from command line, with the hope to solve this problem, otherwise I won't be able to change the login passwd of my encrypted system.
Could somebody help? Thanks in advance.

---

### Post by sudodus on 2013-04-26
Interesting! I did not realize that it is hard or impossible to change the password with an encrypted home folder. I have one, so I'm awaiting a solution too. 

(Maybe it would be possible to remove encryption, change password and install encryption again, maybe there is some shortcut.)

---

### Post by alphaamanitin on 2013-04-26
Damn, so glad I read this.  I was going to change my password soon and had just been putting it off.  

AlphaA

---

### Post by Gingalone on 2013-04-27
Obviously that's a bug: it is not possible to change the login password if the home folder is encrypted: that would lock the login screen.
Hope someone will fix it! Thanks in advance!!

---

