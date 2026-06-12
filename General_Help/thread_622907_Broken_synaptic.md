---
title: "Broken synaptic"
date: 2007-11-25
forum: General Help
---

### Post by the_cog on 2007-11-25
See attached for i386 system info.

I went to install my Brother printer and installed the cups wrapper before the lpn. Now my synaptics is hosed for some reason. How do I update / get rid of this botched package?

This is what I get in synaptic:

E: The package mfc5460cncupswrapper needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

and in terminal:

:~$ sudo apt-get remove --purge mfc5840cnlpr
[sudo] password for xxx:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package mfc5460cncupswrapper needs to be reinstalled, but I can't find an archive for it.

:~$ sudo apt-get remove --purge mfc5460cnlpr
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package mfc5460cncupswrapper needs to be reinstalled, but I can't find an archive for it.

:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package mfc5460cncupswrapper needs to be reinstalled, but I can't find an archive for it
.
:~$ sudo apt-get remove --purge mfc5460cnsupswrapper
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package mfc5460cncupswrapper needs to be reinstalled, but I can't find an archive for it.

Any help would be greatly appreciated.

---

### Post by spence686 on 2008-01-07
I am having the same problem.  Anyone know how to fix this? I would like to remove the packages and start again.  Thanks.

---

### Post by the_cog on 2008-01-07
I had to reinstall Ubuntu.  I now use the uBackup! script so that if it happens again, it will be a fairly automated recovery.  Sorry I cannot really help you.  Good Luck.

---

### Post by spence686 on 2008-01-08
Well, i did figure out how to get synaptic working. I removed the entry regarding the offensive package from /var/lib/dpkg/status.  I can now at least run synaptic.

---

### Post by AgentZ86 on 2008-01-21
> **spence686 said:**
> Well, i did figure out how to get synaptic working. I removed the entry regarding the offensive package from /var/lib/dpkg/status.  I can now at least run synaptic.

I had similar problem and also reinstalled be cause I didn't know how to fix

But when you say removed the entry, can you describe this topic some more incase I also run into this problem again ?

Thanks

---

### Post by AgentZ86 on 2008-01-25
I believe this is related to the installing of the cups wrapper before the lpr, but in any case you should be able to install the lpr, but then when you install the wrapper you need to create a temp. symbolic link to the lpr

like this:
sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd

Then you should be able to install  the cups wrapper with no dependency errors etc., should be able to just click and run/open with gecko or whatever, then remove/delete the symbolic link

And your printer should now be in the printer/ add printer section etc.

Hope this helps. and this should also solve the dependency errors with synaptic also.

---

### Post by w9wi on 2008-02-27
> **spence686 said:**
> Well, i did figure out how to get synaptic working. I removed the entry regarding the offensive package from /var/lib/dpkg/status.  I can now at least run synaptic.

THANK YOU THANK YOU THANK YOU!!!

I've just spent the last two hours trying to figure out how to get Synaptic working again.  In my case it involved python-louie (and an attempt to get UPnP working so I could use a Linksys Media Link) but the same symptoms - unable to install package, unable to uninstall package, no packages showing up in Synaptic, bunch of posts suggesting forcing removal & reinstallation, none of which worked.

Your recommendation worked.  THANK YOU!

(anyone got a schematic for a Linksys WML11B?  Figure I can at least use the speakers & audio amp.....)

---

