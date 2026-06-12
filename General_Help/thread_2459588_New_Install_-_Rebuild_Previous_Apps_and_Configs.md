---
title: "New Install - Rebuild Previous Apps and Configs"
date: 2021-03-22
forum: General Help
---

### Post by Quarkrad on 2021-03-22
I need to reinstall 20.04; fortunately I have separate **/** and **/home** partitions.  Over the years I have read snippets about using apt to reinstall, from a Backup, previous (manually) installed apps and then manually copying the respective config files.  Although reading numerous snippets I have never come across a resource that explains in detail how this is actually done (config files could be in numerous locations). This would save a lot of time/effort and be fantastic if it can actually be done.  If anyone could point me to a resource that details this I would be very grateful.

---

### Post by guiverc on 2021-03-22
Why not re-install using "*Something-else*" ?

If you re-install using "*Something else*", and select your existing partitions, and do **not**format any, that will cause a re-install, ie.


[LIST]
[*]it'll note your current installed packages 
[*]erase system directories 
[*]install new system from the media (*which can be a different release*) 
[*]attempt to add back your *additional* packages noted earlier, and will succeed if they are available in the Ubuntu repositories for your 'new' release (*they may not be if you changed release or were from a 3rd party source*) 
[*]it won't touch user files UNLESS you formatted. 
[/LIST]
 
As system directories are wiped, some server program configs (*which can store config/conf files in system directories*) will require restoration from backups, but desktop applications store their configs within user directories, which are *not* touched unless the user formatted the partition.

This is by the far the fastest way to upgrade (ie. *upgrade via re-install*) in my opinion.  It's also a super-fast way to correct a really-screwed up system.

  If you use a lot of 3rd party applications you can have issues, as you can with packages that no longer exist (eg. python2 & Qt4 were removed during 2019 so a 18.04 to 20.04 upgrade using this method would have given an error that not all packages were found and thus couldn't be re-installed; but in my experience that's only very few and not a drawback).

Key is the "**format**" checkbox, as it not only causes format, but triggers the **clean **install, where this is sort of *unclean* install (due to no-format), but I think it's a ***GREAT*** feature of Ubuntu (and *flavors*).

I hope it remains in the new installer we'll see in 21.10 (*for Ubuntu Desktop & many flavors*)

---

### Post by Quarkrad on 2021-03-22
Thank you. I normally do reinstall using the method you described - hence having separate **/** and **/home**.  I've been 'playing' with various network settings (bridge connections/kvm) and despite making backups (mainly in /etc/) cannot get things back to where they were.  I'm not sure if any other config files are in /etc/ pertinent to apps I've installed (I guess not) - similar to me messing up my kvm/lib vert environment due to the network configs in /etc/. I've dabbled with something I'm not capable of changing and paid the price. Thanks for your reply.

---

### Post by dragonfly41 on 2021-03-22
[COLOR=#000000]> I'm not sure if any other config files are in /etc/ pertinent to apps I've installed
Have you considered *hidden* files and folders .. such as

$HOME/.config[/COLOR]

---

