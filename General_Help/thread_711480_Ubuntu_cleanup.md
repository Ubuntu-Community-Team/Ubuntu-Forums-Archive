---
title: "Ubuntu cleanup"
date: 2008-02-29
forum: General Help
---

### Post by Mongo5000 on 2008-02-29
This might be my ex-Windows instinct working, but im just wondering if/how to do a general cleanup of the OS.

In windows, i used to do system scans for spyware, adware, etc.  Along with defraging the HD and cleaning up junk system files.  Also, I would uninstall apps that I don't need/use.

Is this really necessary in linux?

---

### Post by thenewgirl on 2008-02-29
Well, I am not experienced by any means, but from everything I've read you shouldn't have to worry about adware/spyware/malware of any kind. As far as cleaning out junk files I don't know.

And to uninstall apps you can do that from Add/Remove under Applications *I think*

---

### Post by pointone on 2008-02-29
You can clean out your cache of downloaded packaged occasionally by running "sudo apt-get clean" or "sudo apt-get autoclean", and occasionally run "sudo apt-get autoremove" to get rid of unnecessary packages.

Otherwise, that's about all you should need to worry about.

---

### Post by Mongo5000 on 2008-02-29
yeah, the adware/spware stuff was one of the reasons I moved to linux, but its just that mentality that in windows, you got to do that every now and then.

Thanks for the package commands!

---

### Post by Rocket2DMn on 2008-02-29
Check this out: [http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)
I don't know about those orphan and other packages, but the first steps with synaptic and apt-get are really easy and helpful.

---

### Post by kioftes on 2008-03-22
**_CAREFUL_** when removing orphan packages using deborphan or similar apps. It removed some "orphan" libraries from my system that were needed to run some other app i once compiled. After that i had to reinstall everything deborphan removed to make my precious little app run smoothly again...

---

