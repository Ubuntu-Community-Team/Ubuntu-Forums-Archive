---
title: "Troubleshooting Adept"
date: 2007-09-01
forum: General Help
---

### Post by Kolfinna on 2007-09-01
Good afternoon!

I'm having some issues with certain packages within Adept and I'm not sure how to fix them...

The two packages in question are sun-java6-bin and sun-java6-jre. It seems like every time I upgrade/install them, I get an error saying that the files are in a very bad/inconsistent state. When it tries to install anyway, the entire application hangs. I have to exit, go back to terminal, and run the dpkg --configure -a to be able to run Adept again.

How can I get rid of the sun-java6 packages? They prevent me from updating anything else... I can't remove them because they're not installed yet, and can't quite get it to cancel the upgrade. 

Thank you for your time and consideration,

~K

---

### Post by mcook2 on 2007-09-05
I'm having the same issue with Synaptic Package Manager ... sun-java-bin "is in a very bad inconsistent state: you should" 

This happened after getting a gray screen (Gnome) with a "Do you accept the software agreement" prompt.  With Java 5 you used to get these prompts in a terminal window instead I seem to remember.  At this stage either the prompt timed out and wouldn't accept a response thereafter, or it wouldn't accept a response anyway.

After numerous Force Quits and reboots I tried to upgrade to sun-java6-jre .... I ended up in the same place ... unable to respond to the License Agreement prompt. 

I'll let you know what I find out - looks like this problem has been around for a while ....

M.C.

---

### Post by Ayuthia on 2007-09-05
Have you tried using apt-get upgrade or apt-get install instead of synaptic or adept?  That might help.  If you want to remove it, you should be able to do it by apt-get remove.

---

### Post by mcook2 on 2007-09-05
Here's what I did:

Google search revealed [URL="https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/122325"].

I ran sudo apt-get -f install:

This cleaned up the problem and I was able to proceed with SPM and successfully install the sun-java6-jdk +fonts +doc +javadb packages.

---

