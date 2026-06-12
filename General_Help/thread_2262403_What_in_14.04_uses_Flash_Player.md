---
title: "What in 14.04 uses Flash Player?"
date: 2015-01-24
forum: General Help
---

### Post by Cyber72 on 2015-01-24
Any messaging aps or anything else that use Flash Player? My single core laptop struggles with youtube in 32 bit 14.04. Planning to install 64 bit version, I understand that one possible problem is that when updating Flash Player there can be elements running some programs which means remnants of an old version remain. My plan is to remove all this software before I install Flash Player.

Does Flash Player come bundled with 14.04? If it is would I need to custom install to avoid having it before I've removed the programs I don't want? Would I be better to custom install and not install instant messenger and any other potentially troublesome aps?

Would leaving 14.04 32 bit as dual boot ruin my plan?

---

### Post by deadflowr on 2015-01-24
If you install flash, which does not come with Ubuntu-bundled, install it from the software center and whenever a new version comes the system will automatically update it to that.
If you're using anything that might be using it, like watching videos on youtube, you would need to restart the app.
You shouldn't have to remove anything, though.

But if it really bothers you that you do not know what apps may or may not be using flash, a reboot or log out will close all apps and restart with the fresh version of flash. 

I hope this isn't confusing.

---

### Post by monkeybrain20122 on 2015-01-24
I don't think there is any common application that uses flash (the only thing that comes to mind is webcam studio, but that is not 'common' and  I never use it, some web based voip things may use it)

You don't need flash for Youtube. 

You can use the Viewtube script on Firefox (install gecko-mediaplayer from the repo, install the greasemonkey addon for Firefox, restart Firefox and then install the script.
[http://isebaro.com/viewtube/?ln=en](http://isebaro.com/viewtube/?ln=en) Viewtube also works on other popular websites like Vimeo, Dailymotion etc.

Smtube is a standalone Youtube viewer, you can use vlc, mpv or Smplayer as its backend player. Install the up to date version from this ppa
[https://launchpad.net/~rvm/+archive/ubuntu/smplayer](https://launchpad.net/~rvm/+archive/ubuntu/smplayer)

---

### Post by Andrew_Lucas on 2015-01-25
I'm running an x64 install, with Flash installed. The plugin at least is installed with:

```
sudo apt-get install flashplugin-installer
```

In my experience, the only thing flash is used for e.g. in IM is for displaying adverts. The only other commonly used thing I can think of that might want it is Steam, which works without problem on my installation.

Also, isn't YouTube meant to be moving to something more open (i.e. non-flash)? Idk the latest developments, but I know Mozilla seem to be making a concerted effort to finish off Flash. It's just as well, since we Linuxers will be stuck with 11.2.X. Adobe stopped providing new versions years ago, only security updates are released.

---

