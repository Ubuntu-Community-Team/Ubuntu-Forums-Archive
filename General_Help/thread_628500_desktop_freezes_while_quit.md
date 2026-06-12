---
title: "desktop freezes while quit"
date: 2007-12-01
forum: General Help
---

### Post by rishav on 2007-12-01
Hi,

I am using Ubuntu 7.10 on desktop. Whenever I click quit, the desktop stops responding for about 2 minutes expect the mouse cursor. Then the quit dialog box appears. This happens only for the first time. I mean if I click cancel and then again click quit the box appears instantly. 

I noticed a interesting thing. When the dialog box appears after freezing for two minutes I can't see the standby and hibernate option. Then if I click cancel and again click quit then the two option appears.

So my guess is the desktop freezes as it is doing something with the power properties. 

What can be the problem?

---

### Post by rishav on 2007-12-02
This is one of the prime difference between windows and linux. You get any problem on windows there will be tons of resources and suggestion pouring in. No help so far here.

---

### Post by jpittack on 2007-12-02
If you don't recieve an answer its because no one who has looked at your thread means they don't have an answer.  The operating systems have little to do with the forums, or the knowledge of those that are browsing them.  Please don't compare the OSes forums.

I do not have an answer.

I suggest posting more about your desktop enviorment. Your graphics card, your chosen driver for the card.  Do have have very little RAM?  Are you running a massive amount of applications when you try to shutdown?

Since you are on a desktop, is your power supply fine, since you think its a power problem.  

I suggest just reinstalling if you have nothing to lose.  Perhaps you had a bad cd.

---

### Post by rishav on 2007-12-03
The day I regret most is when I replaced XP with Ubuntu.

---

### Post by jpittack on 2007-12-03
Have you tried a reinstallation?  I'm sure this will solve the problem.  Sounds like a few files got corrupted.

---

### Post by rishav on 2007-12-04
Will I lost all my installed softwares and my personal settings and user accounts if I do re-installation??

Isn't there an option like "repair" that we get in windows XP.

---

### Post by jpittack on 2007-12-04
I have heard bad stories about repair.  You are welcome to try it.

Re-installation will delete your personal settings, user accounts, and installed software only if you have one partition dedicated to Ubuntu.  If /home is on a seperate partition, nothing will be lost unless it is compiled specific to the kernel, such as the ndiswrapper solution I have for my wireless.

Here is what I suggest.  Try a repair after backing up data to external sources.  If this fails, re-install a clean copy.  Check out Google searchs or forum searchs about putting /home and / on seperate partitions.  It is your choice if you want /boot on a seperate one as well, but I have a feeling you will not need to do this.

There are a lot of resources to help you along with this from google searches or just searching the forums.  Google will probably provide you with some pictures, something I won't be able to give you.  I suggest using the alternate install text based CD for setting up partitions, I find it much easier.

---

### Post by onion221 on 2007-12-04
I have run into this problem, what I do is go into system monitor and press end task on nautilus. Nautilus restarts and the problem fixes for me.

---

### Post by bbwolf on 2008-04-26
make sure both acpi-support and acpid are running from boot-up. they are important for laptop and desktop computers to do power management stuff.
I used to have the exactly same problem.

---

### Post by bbwolf on 2008-04-26
sorry, please ignore my previous reply. The process that matters is gnome-power-manager. For desktop, even acpi-support and acpid are disabled and gnome-power-manager is enabled from boot-up, you still can have suspend and hibernate options. But for laptops, I would say leave both acpi-support and acpid on.

---

### Post by docomo on 2008-04-27
I experienced this problem on Hardy. I had previously un-checked gnome-power-manager in Preferences - Sessions - Startup programs. When I re-enabled gnome-power-manager, the problem went away after logging in again.

---

