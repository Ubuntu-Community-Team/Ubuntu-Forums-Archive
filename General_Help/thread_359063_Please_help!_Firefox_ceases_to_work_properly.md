---
title: "Please help! Firefox ceases to work properly"
date: 2007-02-11
forum: General Help
---

### Post by tylersticka on 2007-02-11
I'm hoping someone can help me with a near-disastrous problem...

I have been setting up a laptop with Xubuntu Edgy for the last week. Everything was going great, so I decided to search the forums for additional applications that people recommended.

Firefox worked fine, but started slowly, so I was intrigued when I read about Swiftfox.

I used Swiftfox's automated installer for my processor, it installed correctly, but ran even slower than Firefox had, and sometimes would not start at all.

Dissatisfied, I used Swiftfox's automated uninstall-swiftfox.sh to remove the program, and started up Firefox... or at least, I tried to.

Now, Firefox is acting the same way that Swiftfox did, starting up slowly and most of the time not at all.

I went into Synaptic Package Manager and marked Firefox for upgrade, but this did not fix the problem. Then, I forced a downgrade of the package, and still no change.

When I attempted to uninstall the application, it gave me a list of things like xfce-desktop that would be affected by its' removal, so I decided not to go with that option.

Is there any way possible that I could restore Firefox to its' exact state from the original installation CD without reinstalling my entire OS?

If you need any more information or details from me, please request them, I'll get them to you as promptly as possible.

---

### Post by tbroderick on 2007-02-11
Try deleting your ~/.mozilla folder.

---

### Post by davidvasta on 2007-02-11
You might want to head into the ADD/REMOVE and take out FireFox (uninstall it) and then I would reboot, I know you should not have to but to make sure you get a clean start with no hung files.

Ok so with that said you could also go into SYSTEM> ADMINISTRATION> SYNAPTIC PACKAGE MANAGER and find FireFox under "installed" and remove it and then resintall it. I would mark it for a "COMPETE UNINSTALL" and see what happens.

Either way it's needs to be removed. Once you have it removed I would resintall it using the SYNAPTIC PACKAGE MANAGER and see what happens.

-David

---

### Post by tylersticka on 2007-02-11
It won't allow me to remove it through the Add/Remove dialogue because it says other applications depend on it. Synaptic Package Manager tells me roughly the same thing, saying that removing the application will also remove "gnome-app-install," "gxine" and "xubuntu-desktop". All of those sound essential, hence my confusion.

---

### Post by tylersticka on 2007-02-11
> **tbroderick said:**
> Try deleting your ~/.mozilla folder.

This worked! I deleted the ~/.mozilla directory, upgraded Firefox to the latest version, restarted it, and now it works just as it did before.

Thanks so much for your help!

---

