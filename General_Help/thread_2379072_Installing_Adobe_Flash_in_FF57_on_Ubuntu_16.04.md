---
title: "Installing Adobe Flash in FF57 on Ubuntu 16.04"
date: 2017-11-30
forum: General Help
---

### Post by cscj01 on 2017-11-30
Flash has been disabled for version 25.0.0.171 for security reasons.  Got it.  So in Add-ons Manager, I click Update Now for Shockwave Flash which takes me to a Firefox Blocked Add-ons page which says to "check for updates on Adobe's Flash Page.  That, in turn provides a link to [https://get.adobe.com/flashplayer/](https://get.adobe.com/flashplayer/), where I have a pull down to select my option for installing version 27.0.0.187.  The page recognizes my OS, and in the pull down, I select Apt for Debian/Ubuntu. I then click Download now and get a message saying "This link needs to be opened with an application.  Send to:".  The default is AptURL which makes no sense to me.  So I choose another application, namely apt, which is what I use to install applications.  Though the title bar of the window says "Launch application" it doesn't do that.  It really wants a link to some location.  I know I could use a .tar.gz file and manually install Adobe Flash, but has anyone successfully used apt to upgrade Adobe Flash and its plug-ins?  I put this question on Mozillazine as well, but I assume it has more to do with Ubuntu.

---

### Post by walts48 on 2017-12-01
I just let Flash update through Ubuntu software updates which installs the flashplugin-installer.

The current version is 27.0.0.187.

I have Updates in my Software & Updates Settings, set to install updates from "Important security updates".

Doesn't answer your question, but it is much easier.

---

### Post by ajgreeny on 2017-12-01
Many users, including me, install flash by enabling the canonical-partner repos in **Software and updates** and then search for and install adobe-flashplugin.

I think it will install the same flash version as the flashplugin-installer, but have not used that for some time so I'm not totally certain.

What I can say is that I now seldom need flash as just about all the sites I visit use html5 instead, so hopefully the time will very soon come when it's no longer needed.

---

### Post by walts48 on 2017-12-02
I have that repo enabled, so I'm not sure if the flashplugin-installer comes from that repo or another, but it is much simpler than what the OP is doing.

---

### Post by cscj01 on 2017-12-05
> **ajgreeny said:**
> Many users, including me, install flash by enabling the canonical-partner repos in **Software and updates** and then search for and install adobe-flashplugin.

I think it will install the same flash version as the flashplugin-installer, but have not used that for some time so I'm not totally certain.

What I can say is that I now seldom need flash as just about all the sites I visit use html5 instead, so hopefully the time will very soon come when it's no longer needed.

I used Synaptic to install flashplugin-installer.  That removed what I had installed from Adobe, but installed an upgraded Shockwave Flash.  It seems to be at the same level as what I had installed from Adobe.  I then searched for adobe-flashplugin and installed that.  It removed the flashpulgin-installer and installed the same two files that were installed from the Adobe site.  So either way for the last two posts works.

However there is one issue.  For some reason, neither installation removed the old Shockwave Flash add-on.  If one goes to Tools->Plugins, you can see that the old Shockwave Flash add-on (version 25.0) is still installed.  I can disable it, but there seems to be no way to remove it.  Any ideas?

---

