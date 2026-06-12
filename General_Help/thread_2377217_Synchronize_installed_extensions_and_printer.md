---
title: "Synchronize installed extensions and printer?"
date: 2017-11-10
forum: General Help
---

### Post by orschiro on 2017-11-10
Hi all, 

To give context. I currently use Ubuntu 17.10 Gnome edition. 

Installed some 3rd-party Gnome extensions from extensions.gnome.org and configured my printers. 

Now I would like to do a fresh install of the 18.04 daily image. 

This would remove all my installed extensions and printers, correct?

It would be amazing to synchronize extensions and printers either using my Gnome account, Google account or Ubuntu account so that I can easily restore them once I installed 18.04.

Is this somehow possible?

Thank you!

Robert

:-)

---

### Post by DuckHook on 2017-11-10
> **orschiro said:**
> Installed some 3rd-party extensions and configured my printers.
Please specify printer make/model and what you mean by "extensions". Are these browser extensions? Please list them.
> Now I would like to do a fresh install of the 18.04 daily image. 

This would remove all my installed extensions and printers, correct?
Yes, correct.
> It would be amazing to synchronize extensions and printers either using my Gnome account, Google account or Ubuntu account so that I can easily restore them once I installed 18.04.

Is this somehow possible?
Browser extensions can be carried over on some browsers by logging into your browser account and re-synchronizing new browser settings to the old ones. You would need to enable synchronization on your browser first, before wiping the old install. BTW, this also works across devices too. Another method is to put your /home directory on a separate partition. That way, you can inherit it with any new install by simply pointing to it in the setup process. This has the additional advantage of preserving all of your old data files and personalized info: even your encryption keys. But note: **DO NOT** format this partition during install as this will wipe your /home partition of all old data.

To my knowledge, this strategy is not possible with system settings (like printers). Even if theoretically possible, there is no way I would trust automating or scripting such a process on a pristine install. The network upgrade process is presumably tested by the devs to allow inheritance of old settings, but this breaks often enough that these forums are full of pleas for help with the resulting problems. In a pristine install, there are so many changes from the old version that by the time one figures out what has changed and what has not, it's far simpler to just re-create the settings. After all, they are limited in number and not very hard to innumerate. I also treat the occasion of a new pristine install as an opportunity to start fresh and purge my system of any cruft that my have worked its way into my previous installation from experimentation and fiddling.

---

### Post by orschiro on 2017-11-11
Dear DuckHook,

I should have been more precise, sorry! 

I meant Gnome Extensions installed from extensions.gnome.org. There is no way I can sync them with any kind of user account, correct?

And regarding the printer, it's a network printer we use here in the office. I don't know the exact brand. I am wondering though why the printer is not stored under /home to preserve it upon new installations?

---

### Post by DuckHook on 2017-11-11
> **orschiro said:**
> There is no way I can sync them with any kind of user account, correct? To my knowledge, yes.

>  I am wondering though why the printer is not stored under /home to preserve it upon new installations?
Because a printer is a system device that not only uses system libraries, but is available to all users. It makes no sense to restrict it to a single user under only his /home directory. Moreover, printer libraries change as new models are constantly added. It makes no sense to duplicate these libraries for each user.

---

### Post by orschiro on 2017-11-12
Dear DuckHook,

Thanks! I found a solution to syncing the Gnome Shell extensions. They are synced if you're using the Gnome Shell Chrome extension [1]. That's cool. :-)

Regarding the printer, I am still hoping for a user-friendly way [2] as opposed to backing up /etc/cups [3].

[1] [https://bugzilla.gnome.org/show_bug.cgi?id=790208#c1](https://bugzilla.gnome.org/show_bug.cgi?id=790208#c1)
[2] [https://bugzilla.gnome.org/show_bug.cgi?id=790247](https://bugzilla.gnome.org/show_bug.cgi?id=790247)
[3] [https://askubuntu.com/questions/334267/how-do-i-back-up-network-and-printer-settings](https://askubuntu.com/questions/334267/how-do-i-back-up-network-and-printer-settings)

---

### Post by DuckHook on 2017-11-13
Great! I haven't really started using gnome yet. I've only got Aardvark installed on an experimental partition. My main system is still Xenial and Unity.

Re: Printing.

Please especially pay attention to the warnings in that last link you posted. Libraries, services and scripts change from version to version. Simply copying over whole files and directories from an earlier system is, in my opinion, an open invitation to system breakage. Therefore, I would strongly advise against just backing up/restoring /etc/cups. If the new cups uses a different set of scripts from the old cups, you will break cups.

While it is a spot of bother to note the printer settings from an older install and enter them into the dialogue boxes of a new install, it's not really that onerous. A few minutes doing so could save you hours of corrupted system files and perhaps being forced to do a reinstall.

---

### Post by orschiro on 2017-11-13
> While it is a spot of bother to note the printer settings from an older install and enter them into the dialogue boxes of a new install, it's not really that onerous. A few minutes doing so could save you hours of corrupted system files and perhaps being forced to do a reinstall.

I think this is a very good point. Thank's for raising that! I hope they (Gnome) are going to implement a graphical way to backup (export) and import a printer.

---

