---
title: "[SOLVED] Is it Possible to &amp;quot;Lock&amp;quot; a Package and Not Allow Auto Updates?"
date: 2008-03-31
forum: General Help
---

### Post by bunnyfly on 2008-03-31
Hello - I have recently upgraded to Hardy (I know there's a Hardy forum, but this isn't Hardy specific) and spent forever re-fixing my newly-broken Wifi after the upgrade.

My question is - now that I've got it working, is there a way to lock or freeze my Wifi packages and drivers so that there is no risk of accidentally upgrading them and risking them being broken again?

Thank you in advance,
[chloe]

---

### Post by Slushdoot on 2008-03-31
I'm interested in this as well.  Back in the day kernel upgrades would break a lot of things for me.  This hasn't been as much of an issue lately, though.  Perhaps it's just the distro improving, or perhaps it's that I switched most rigs to more Linux-friendly hardware.

---

### Post by Oldsoldier2003 on 2008-03-31
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/synaptic/+bug/42178](https://bugs.launchpad.net/synaptic/+bug/42178) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **bunnyfly said:**
> Hello - I have recently upgraded to Hardy (I know there's a Hardy forum, but this isn't Hardy specific) and spent forever re-fixing my newly-broken Wifi after the upgrade.

My question is - now that I've got it working, is there a way to lock or freeze my Wifi packages and drivers so that there is no risk of accidentally upgrading them and risking them being broken again?

Thank you in advance,
[chloe]

find the packages and lock them in synaptic. however this will not lock them in apt-get so you need to either create and edit /etc/apt/preferences or link it to /var/lib/synaptic/preferences

---

### Post by warp99 on 2008-03-31
You can lock a package in one of two ways. Say the package you want to lock is mplayer. From the command line:

```
echo "mplayer hold" | sudo dpkg --set-selections
```

the other way is to open Synaptic, highlight the package, then choose from the menu Package > Lock Version. Hope this helps.

Edit:

The command line option will lock the package in apt-get as well as Synaptic.

---

### Post by ibuclaw on 2008-03-31
And to link the to files together.

```
 sudo ln -fs /var/lib/synaptic/preferences /etc/apt/preferences 
```

Regards

---

### Post by bunnyfly on 2008-03-31
Thank you so much for the quick replies!

It's right there too! I guess I just supposed that if it wasn't in the context menu, it didn't exist in Synaptic. It appears to work - I might try the command line also just for good measure, thanks,
[chloe]

---

### Post by Oldsoldier2003 on 2008-04-01
> **bunnyfly said:**
> Thank you so much for the quick replies!

It's right there too! I guess I just supposed that if it wasn't in the context menu, it didn't exist in Synaptic. It appears to work - I might try the command line also just for good measure, thanks,
[chloe]

to truly lock it you'll need to use the command line because apt-get update does not respect Synaptics locks, its a bug :(

---

### Post by warp99 on 2008-04-01
Apt-get and their associated programs are **very** powerful package management tools:

[https://help.ubuntu.com/community/AptGetHowto](https://help.ubuntu.com/community/AptGetHowto)

---

