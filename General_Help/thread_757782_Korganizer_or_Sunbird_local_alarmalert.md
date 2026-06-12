---
title: "Korganizer or Sunbird local alarm/alert"
date: 2008-04-17
forum: General Help
---

### Post by Manojo on 2008-04-17
Hi,

I am looking for an agenda/todo-list application that starts at boot, and that can display alarms. I have checked at Korganizer (under Gnome), but it doesn't seem to automatically start up. 
Does that feature actually work ? Is it possible to do the same under Sunbird?

Thanks,
Manojo

---

### Post by Brucevdk on 2008-04-17
You can add anything to startup by simply adding it to your session (System -> Preferences -> Sessions). I personally just use Mozilla Thunderbird in combination with Lightning (which is basically Sunbird integrated into Thunderbird I believe) and alltray (to hide it in the tray).

---

### Post by Manojo on 2008-04-17
Cool Brucevdk, thanks a lot, that's something I didn't know about, its a great feature.

Manojo

---

### Post by SummerStorms on 2008-04-18
Bruce, I can't seem to get Lighting to work properly in Gutsy. It throws the whole T-Bird screen off and makes it hard to do anything. Did you experience this as well, and if so, how did you resolve it?

---

### Post by Brucevdk on 2008-04-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/lightning-sunbird/+bug/191787](https://bugs.launchpad.net/ubuntu/+source/lightning-sunbird/+bug/191787) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **SummerStorms said:**
> Bruce, I can't seem to get Lighting to work properly in Gutsy. It throws the whole T-Bird screen off and makes it hard to do anything. Did you experience this as well, and if so, how did you resolve it?

I did indeed experience that, but I didn't think it was a bug (just a local configuration problem). I downloaded the binary from the Mozilla website and booted that up which solved the issue for the Ubuntu installation too. 

I just searched LaunchPad and came across [Bug #191787](https://bugs.launchpad.net/ubuntu/+source/lightning-sunbird/+bug/191787). They say the problem is solved when installing libstdc++5, so try that first. 

```

sudo apt-get install libstdc++5

```

---

