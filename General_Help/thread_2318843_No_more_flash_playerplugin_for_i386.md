---
title: "No more flash player/plugin for i386 ??"
date: 2016-03-29
forum: General Help
---

### Post by fizikz on 2016-03-29
Chromium/chrome no longer receives flash updates: 
> The pepflashplugin-installer package may be installed on Ubuntu 14.04 (Trusty) or newer, for the amd64 architecture. (Google dropped support for i386 as of March 2016.)[https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash](https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash)

I tried installing webupd8's freshplayerplugin, but flash content doesn't work in Chromium, even though "about://plugins" reports adobe flash player enabled.

Anything else to try?

---

### Post by TheFu on 2016-03-29
[https://askubuntu.com/questions/724093/no-more-updates-for-google-chrome-apt-get-update-error](https://askubuntu.com/questions/724093/no-more-updates-for-google-chrome-apt-get-update-error)

Options:
a) Load AMD64 OS and Chromium and flash, if your CPU supports it.
b) Stop using Flash.

That's all I got. Sorry.

---

### Post by fizikz on 2016-03-30
Unfortunately, not using Flash isn't an option. Doing a clean install is.... dreadful. I've been doing distribution upgrades since... I don't even remember... 2009? I've done so many little tweaks and really wanted to avoid the hassle of doing it all again. I guess when 16.04 LTS comes out I'll have no choice but to bite the bullet.

Right now my only access to Flash in Ubuntu is Firefox... using version 11.2.202.577 :P

I'd be glad to hear any other solutions!

---

### Post by SeijiSensei on 2016-03-30
You can use pipelight to run the Windows Flash player: [http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html)

I've been using this solution for quite some time now.  It has a few quirks (I have to Alt-Tab after the video ends to get back the cursor), but otherwise it's quite solid.  I subscribe to some Silverlight-based services and pipelight works with them as well.

---

### Post by fizikz on 2016-03-30
> **SeijiSensei said:**
> You can use pipelight to run the Windows Flash player: [http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html)


Thanks! I also had to do "sudo pipelight-plugin --create-mozilla-plugins" to get the plugin to show up in Firefox. 

Firefox now uses one of the latest Flash versions (21.0.0.182 vs 21.0.0.197 available). Does Flash get updated automatically through system software updates?

---

### Post by SeijiSensei on 2016-03-31
Yes, I've had to create the plugins as well.

Remarkably I cannot find any information about how updates to Flash (or Silverlight or other supported programs) are handled.  There's literally nothing on the main pipelight site, and a Google search failed to reveal anything either.  I think pipelight might check upstream when a plugin is loaded, but I'm not sure.  This is certainly a big hole in the documentation!

Flash won't get updated from the Ubuntu repository since it only contains the Linux version of Flash.  Pipelight would have to handle updates on its own.

---

### Post by fizikz on 2016-03-31
My guess is that updates to Pipelight (from the repository) might also prompt an automatic execution of "sudo pipelight-plugin --update" which would update the enabled plugins at that time, and of course that can be run manually as well.

Do you have the latest Flash version, or a slightly older one?

In any case, thanks for the help. I'll mark this issue as solved now.

---

### Post by SeijiSensei on 2016-03-31
My machine shows 20.0.0.306.  Running "sudo pipelight-plugin --update" just now didn't download a new version of Flash.

---

### Post by deadflowr on 2016-03-31
If the goal is simply to run an updated flash, then perhaps something as simple as installing Firefox in Wine would be suffice.
Of course this would mean you would need to be a tad more vigilant in updating, but it works well.
I'd recommend [clem's method]("https://community.linuxmint.com/tutorial/view/2028") which specifies you download Flash separately, rather then use the version Firefox tries to install.

But I'd only go that route if you only want flash.
If you want to have access to other plugins, like Silverlight et al, then Pipelight is an excellent choice.

---

### Post by fizikz on 2016-04-01
SeijiSensei, wow that is a somewhat old version of Flash! There are some websites that wont work without the very latest version. I wonder why running the update command didn't update your flash plugin, considering a newer version is clearly available given the version in my installation.

deadflowr, thanks, I also installed Firefox in Wine using clem's method, and this way I have access to the latest version of Flash. One concern I have with Pipelight, as clem mentions, is that it might introduce vulnerabilities or at the very least make a messy installation. Still, better to have a workaround (or two) than none.

---

### Post by TheFu on 2016-04-01
Flash is a security nightmare: [http://krebsonsecurity.com/tag/flash/](http://krebsonsecurity.com/tag/flash/)

---

### Post by SeijiSensei on 2016-04-01
Well if Flash runs under pipelight any security problems it might pose are limited to the disposable wine environment.

I went to Tools >Addons > Plugins, and the wine-flash-installer app ran.  I then had to rerun "--create-mozilla-plugins" again.  Now I have Flash 21.0.0.182.

---

### Post by fizikz on 2016-04-02
At least you found a way to update. 21.0.0.182 is the latest version in Windows for Internet Explorer and Edge, although not the latest version available for Firefox.

---

