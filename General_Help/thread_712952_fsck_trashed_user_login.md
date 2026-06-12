---
title: "fsck trashed user login"
date: 2008-03-02
forum: General Help
---

### Post by broden on 2008-03-02
My system started with a notification that the file system must be checked.
After completion I could not login as the default user.
I am using Kubuntu Gutsy on a AMD 64 processor and have /home on a seperate hard disk. 
I can get into the system using the recover option in grub as root I can even get the GUI by startx.

Observations: 
fsck used to screw up xserver under Fiesty, but a reboot would fix it.
Using Autofsck seems to be problematic.

Questions:

Is there a fix to get the default user running again? Where do I start?
Can I do a reinstall and get the system to use the user and /home on the other disk.

Any help or suggestions greatly appreciated.

Thank you

broden

---

### Post by broden on 2008-03-02
I received a reply in another forum that indicated a bad update caused the problem.

"I found this on another forum and it fixed mine..
Here it is!!!

Do both of the coomands!!


I experienced the looping login issue and I thought that it was fixed by the following
Code:
sudo apt-get remove language-pack-kde-en language-pack-kde-en-base

Further inspection, however, showed that I had begun having bizarre problems with XMMS and Kopete so I installed the language pack that just happened to be dated on my birthday!
Code:
sudo apt-get install language-pack-kde-en=1:7.10+20071012 language-pack-kde-en-base=1:7.10+20071012

I'm now back to having a very stable Kubuntu system and couldn't be happier."

Thanks to" kdlogie" for the fix.

broden

---

