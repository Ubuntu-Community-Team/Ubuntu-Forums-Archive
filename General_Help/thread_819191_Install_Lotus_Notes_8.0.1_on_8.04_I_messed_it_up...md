---
title: "Install Lotus Notes 8.0.1 on 8.04: I messed it up..."
date: 2008-06-05
forum: General Help
---

### Post by HamburgerTS on 2008-06-05
My question:
How can i purge my lotus notes installation manually. 

Background:
I tried to install Lotus Notes 8.0.1 on Ubuntu 8.04. Successfully!

I run into a permission problem with pernames.ntf. I was unable to solve this with chmod'ing because i don't know that /etc/notes exists and the pernames.ntf is located there. 

Then i issued (as i said: i messed it up):
sudo rm -rf /opt/ibm
sudo rm -rf ~/lotus

after i realised that this folder exists:
sudo rm -rf /etc/lotus (/etc/notes ?)

if i now try to install the client again the install wizard is thinking that all files are alread there and copy not all necessary files (the installation procedure is very fast). 

I missed some files but i don't no where to find them...

i need to completely remove the broken installation from my system in order to make a clean and fresh install. 

Any suggestions?

---

### Post by HamburgerTS on 2008-06-05
I like to inform you that i've solved my problem. I "rm -rf"'ed around and finally managed to delete all remaining files which have confused the notes install script: 

```

sudo rm -rf /etc/ibm
sudo rm -rf /etc/lotus
sudo rm -rf /opt/ibm
sudo rm -rf ~/lotus

```
(I hope i haven't forgotten any relevant folders in this list.)

After the successful installation of the 8.0.1 client i've issued
```

sudo chmod -R 777 /etc/ibm
sudo chmod -R 777 /etc/lotus
sudo chmod -R 777 /opt/ibm
sudo chown -R username:username ~/lotus

```

Now the client runs without any problems. 

There is only one little thing but that doesn't seem to be a "problem" (at least until now); After logging into notes i got this error message:

> 
Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.


Many thanks to all who have read my post! :)

Greetings
HamburgerTS

---

