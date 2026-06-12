---
title: "Which of the different updates to use"
date: 2016-11-13
forum: General Help
---

### Post by FerryGnu on 2016-11-13
Just installed 16LTS and finding my way around. I have found different options for updates. 

If I run each one sequentially, they all do some updates.  

Do I need to go through all three processes to get a completely updated system?  
sudo apt-get update 
sudo apt-get upgrade  

AND -  
Software Updater 
 
AND-
System Settings 
 Details
--Check for updates  

Is there one process that will do it all? 

 Corn-fused! :D

---

### Post by &amp;KyT$0P# on 2016-11-13
```
sudo apt-get dist-upgrade
```

But there is a reason you don't get all the updates through Software Updater - [https://wiki.ubuntu.com/PhasedUpdates]("https://wiki.ubuntu.com/PhasedUpdates")

---

### Post by wildmanne39 on 2016-11-13
Hello, welcome to the forum! you can use the terminal with the following command:
```
sudo apt-get update && sudo apt-get upgrade
```
or you can just use the gui update tool, it has settings to install updates daily and weekly.

The first part of the command updates the repositories so you will be able to install the latest updates and the second part of the command does the upgrade of the software.

---

### Post by FerryGnu on 2016-11-13
@halogen2:
Thanks for that link, I like to understand what and why and that helped a lot.

@WildMan:
I had not realized that the update configuration was duplicated in the Software & Updates thing. I had looked at the "Settings" in the Updater but still did not understand why they all added something.

I will just us the GUI then.

---

### Post by deadflowr on 2016-11-13
Aren't software updater and the install updates from the details page the same?
(both run software updater / update-manager)

I know there are 3 distinct update mechanisms on 16.04 and up.
1)apt command line
2)software updater aka update manager
3)gnome software updates

apt is probably the most verbose, giving you very important information on exactly what's being done and exactly when.
(not sure either graphical updaters will show eta status on how long downloading updates will take.)
But it does not have phased updates baked in, as of yet.
So chances of an update causing problems with apt does increase, even if slightly.

software updater is probably the simplest, and maybe the safest, since it has phased updates baked into it.
But it also has the release upgrader baked in, so sometimes, (if users have the notify me of new versions set to newest version)
if the users unintentionally chooses the wrong option (Upgrade), they might end up upgrading the release from whatever version they have (16.04) to the next release available (16.10)

gnome software, also known now as Ubuntu Software, the newest update mechanism and probably the least of the 3.
requires gnome software to always be running
(in the background, but running (and eating resources) none the less.)
and will still run, even after closing, unlike the other two which stop when you exit or close them.
(you would need to run a kill command to actually stop it)

I guess each one has it's own pluses and minuses.
So which one you choose to use is entirely up to you.
You might even find yourself using all three in various rotations.

And you might even decide to ignore all 3 and instead setup full unattended upgrades
[https://help.ubuntu.com/lts/serverguide/automatic-updates.html]("https://help.ubuntu.com/lts/serverguide/automatic-updates.html")
[https://help.ubuntu.com/community/AutomaticSecurityUpdates]("https://help.ubuntu.com/community/AutomaticSecurityUpdates")

So I guess there are actually 4 methods...:D

As I ramble away

---

### Post by wildmanne39 on 2016-11-13
Your welcome! if this answers your question please use thread tools at the top of the page to mark the thread solved.
Thanks

---

