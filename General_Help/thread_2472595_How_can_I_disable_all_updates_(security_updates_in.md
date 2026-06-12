---
title: "How can I disable all updates (security updates included)"
date: 2022-03-05
forum: General Help
---

### Post by wombyte on 2022-03-05
I'm using Ubuntu 20.04, 64 bit, Desktop.

I know I should never do that.
Besides that:

How can I disable all updates, also security updates?

I sometimes have a paid per use - internet connection (we live in the nowhere, a very small village). 
My internet billing could get very high if Ubuntu sometimes wants to download 100 mb update. As I use this paid per use internet only if the regular internet does not work (which is maybe 1-2 times per week). 

One main reason why I switched to Ubuntu was that Windows 10 was always spamming updates. I know they are important and so on.
But it seems you can't disable updates on Ubuntu any more than you can on Windows.

I tried everything, I changed the settings to "never" search for updates. But security updates are not affected by this setting. 
And I can only choose between "auto install" and "display immediatly" for security updates. 

Then I disabled  unattended-upgrades. Still no effect.

I don't want to get rid of updates at all, but I just want to have some more control about when I would like to install them.

---

### Post by mIk3_08 on 2022-03-05
> **wombyte said:**
> I sometimes have a paid per use - internet connection (we live in the nowhere, a very small village). 
My internet billing could get very high if Ubuntu sometimes wants to download 100 mb update. As I use this paid per use internet only if the regular internet does not work (which is maybe 1-2 times per week). 
 Do you have data capping internet? This is the kind of internet where it was so very poor distribution of internet and so very expensive. The service provider imposed limit on the amount of data transferred in every user account. Updates are very important for security purposes but saving the amount of data internet transfer is more very important cause if you fail not to save it at the middle of the month you already lose it then you will be miserable to all the remaining days left in the month. I feel you man. regards

---

### Post by wombyte on 2022-03-05
> **mIk3_08 said:**
> Do you have data capping internet?

Yes exactly. 

Well actually I have 2 internet providers, one is a flat, where I can use as much internet as I want. But that one sometimes does not work because of the place where I am living.
The second one is from my phone provider. There I have to pay per used GB.

---

### Post by Impavidus on 2022-03-05
> **wombyte said:**
> 
And I can only choose between "auto install" and "display immediatly" for security updates. 


"Display immediately" doesn't download anything (or at least, it shouldn't). It only shows a pop-up informing you that updates are available. If you also tell it never to check for updates automatically, this will only happen after a manual check.

I disabled unattended upgrades by simply removing the package unattended-upgrades. My system checks automatically for updates every day (as I have configured it), but only shows the updates. They are only downloaded and installed when I ask.

Updates for snap packages may be a different matter. They appear to be less configurable than the ordinary .deb packages and they are also larger. I've got no snap packages on my system. That may be something to look into.

---

### Post by mIk3_08 on 2022-03-06
> **wombyte said:**
> Yes exactly. 
Well actually I have 2 internet providers, one is a flat, where I can use as much internet as I want. But that one sometimes does not work because of the place where I am living.
The second one is from my phone provider. There I have to pay per used GB.
Just curious wombyte, what country are from? And what are those isp you mentioned you have? regards.

---

### Post by vanadium on 2022-03-06
Check settings in "Software & Updates" first.

Run the command "sudo dpkg-reconfigure unattended-upgrades" to turn the automatic install of important updates off.

You can turn off the update notifier by copying the file /etc/xdg/autostart/update-notifier.desktop to your ~/.config/autostart file. Add a line "Hidden=true" to disable that autostarter.

I am afraid that does not disable automatic update of snap packages: there is currently no user control on updates of snap packages.

---

### Post by grahammechanical on 2022-03-06
If we go to System Settings>WiFi and click the cog icon next to the name of our WiFi connection we will see a dialog with a check box with the label: Metered connections: has data limits or can incur charges. The small print underneath says: Software updates and other large downloads will not be started automatically.

Regards

---

### Post by vanadium on 2022-03-06
> **grahammechanical said:**
> If we go to System Settings>WiFi and click the cog icon next to the name of our WiFi connection we will see a dialog with a check box with the label: Metered connections: has data limits or can incur charges. The small print underneath says: Software updates and other large downloads will not be started automatically.

That will be the best suggestion of all for this case.

---

### Post by wombyte on 2022-03-06
> **grahammechanical said:**
> If we go to System Settings>WiFi and click the cog icon next to the name of our WiFi connection we will see a dialog with a check box with the label: Metered connections: has data limits or can incur charges. The small print underneath says: Software updates and other large downloads will not be started automatically.

Regards

That is perfect, I did not know it exists! 

Thanks alot!

---

### Post by ajgreeny on 2022-03-06
> **Impavidus said:**
> "Display immediately" doesn't download anything (or at least, it shouldn't). It only shows a pop-up informing you that updates are available. If you also tell it never to check for updates automatically, this will only happen after a manual check.

I disabled unattended upgrades by simply removing the package unattended-upgrades. My system checks automatically for updates every day (as I have configured it), but only shows the updates. They are only downloaded and installed when I ask.

Updates for snap packages may be a different matter. They appear to be less configurable than the ordinary .deb packages and they are also larger. I've got no snap packages on my system. That may be something to look into.
This exactly the way that I have configured my updates/upgrades.

I want full control over my system and thoroughly dislike automatic installation of anything on my computer; the first thing I do when I start my day on the computer is run commands (by use of aliases ***ud*** & ***ug*** to avoid too much typing)
```
sudo apt update && apt list --upgradable
sudo apt full-upgrade && ls /var/run | grep reboot-required
```
The first command updates the package database then lists all packages that can  be upgraded; the second command carries out those upgrades and then tells me whether a reboot is required.

I see that this is now appears solved for you so please mark as **SOLVED** from the Thread Tools menu up-top if it is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by wombyte on 2022-03-08
> **ajgreeny said:**
> This exactly the way that I have configured my updates/upgrades.

I see that this is now appears solved for you so please mark as **SOLVED** from the Thread Tools menu up-top if it is now solved to your satisfaction. It is a great help to other users searching the forum.


done :)

---

