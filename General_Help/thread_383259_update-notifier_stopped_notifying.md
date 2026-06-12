---
title: "update-notifier stopped notifying"
date: 2007-03-13
forum: General Help
---

### Post by hang3r on 2007-03-13
Hi, for the past week or so the update-notifier has failed to display an update icon in the notification area, I've had to update manually.

Synaptic->Settings->Repositories->Internet updates, shows that automatic updates are in fact enabled and set to check daily. The gnome notification area applet is added to my panel, I see x-chat, gaim and beryl icons in there, so it's not that. Also system->preferences->seasions->startup  programs shows update-notifier as being there and it is enabled.

So I'm out of ideas, does anyone have any idea why I'm not seeing any update notification icon in the notification area?

Thanks in advance,

-Hang3r

---

### Post by hang3r on 2007-03-14
*bump*

I fail to believe nobody knows how to resolve this, anybody know where it stores its config so I can reset it back to defaults?

(Sorry for bumping).

---

### Post by treesurf on 2007-03-14
Hmmm...this happened to me once too, but it was because I accidentally deleted the notification area from the panel.  It took me days to figure it out, and boy did I feel stupid!

Sorry I couldn't be more help...

---

### Post by hang3r on 2007-03-14
> **treesurf said:**
> Hmmm...this happened to me once too, but it was because I accidentally deleted the notification area from the panel.  It took me days to figure it out, and boy did I feel stupid!

Sorry I couldn't be more help...

Yeah well like I said I know it's there because I can see it, gaim, xmms and xchat are appearing there so It's working correctly.

Just wish I could resolve this.

---

### Post by hang3r on 2007-03-15
Ok, so I decided to reinstall update-notifier and update-manager and all configuration for the two with:

> apt-get --reinstall --purge install update-manager update-notifier

IT STILL fails to notify me of updates... 

Someone out there has to know what is going on.

---

### Post by hang3r on 2007-03-15
I spoke to soon! removing and reinstall both update-notifier + update-manager and all their configuration did work! Shortly after manually running apt-get update there was my nice update notification in the notification area telling me I had updates.

So for anyone looking for a resolution to this problem in the future, run the following:

> sudo apt-get --reinstall --purge install update-manager update-notifier && sudo apt-get update

This will entirely reinstall both update-manager and update-notifier including their configurations.

So it was just a config problem somewhere, don't know how it happened or why, but it's all good now.

---

### Post by gwpritch on 2007-03-15
my update-notifier also stopped notifying. However it will appear in the notification area if I manuallly do an apt-get update. This seems to me to defeat the purpose however.

---

### Post by warjowuch on 2007-04-22
Same here, it appears if I intend to update my packagelist with apt-get update, but the notifier should do this by itself. THis way it is totally un usefull...
Any solutions?

---

### Post by rkh on 2007-04-25
I have the same problem. About a week ago I reinstalled the update-notifier through Synaptic & nothing changed. Since then I have upgraded to Feisty. I hoped that this would somehow fix things but it didn't. Just to say I did, I reinstalled using apt-get as recommended by hang3r, but still nothing. 

This isn't a big problem. I just have to check for updates manually on a regular basis. It just bothers me that the notifier isn't working properly. I really would like to know why and how to fix it. Anyone have any ideas?

---

### Post by gweaver on 2007-05-03
Both of my Feisty installs suffer from the same issue, which was also an issue before upgrading from Edgy To Feisty.

---

### Post by giruzz on 2007-06-23
Hi,

anyone solved this issue?

thanks

g.

---

### Post by jaka on 2007-09-20
I have the same problem on Gusty Gibbon.

---

