---
title: "A strange problem with Firefox"
date: 2008-05-16
forum: General Help
---

### Post by djhyland on 2008-05-16
Hello all,

I'm having a strange problem with Firefox.  I'm using a multi-boot system.  My setup is Ubuntu 8.04 on one partition, Fedora 9 on one partition, and a shared /home directory on the last partition.  I was careful to set up two user accounts so that they share the same user name, user ID, group ID, primary group, and home directory: the works.

The directory sharing thing is working swimmingly:  I can access all the data for each user on either OS, my settings are the same, and all that.  The only problem, as stated by the thread title, is Firefox.  On my primary user account, Firefox works fine.  All of my bookmarks and settings are available under either OS.  However, on the other account (used for testing), Firefox will launch, but it won't bring up a homepage, or have any bookmarks under the bookmark menu, or have a record of the history, or anything.  I can type addresses into the address bar, and the browser will take me there accordingly, and I can follow links from there, but still the navigation buttons (back, forward, reload and such) are inactive.  Again, this is the situation in both OSes.  Firefox, at least in my testing account, is pretty useless.  (For the curious, Firefox worked fine for both accounts before I installed Fedora.)

So, I'm at a loss.  I've tried a number of things such as launching firefox from a terminal and looking for error messages after launch, uninstalling and reinstalling firefox, and trawling around in the hidden files in my temporary account's home directory.  So far, no luck.

Any idea as to what's going on?  Any help would be appreciated.  Thank you in advance.

EDIT: I forgot to add these error messages from Firefox's Error Console.  These are from the problematic account's Firefox.  I hope these help in diagnosing the problem!

```
Error: oldInstallLocation is null
Source File: file:///usr/lib64/xulrunner-1.9pre/components/nsExtensionManager.js
Line: 2812
```

```
Error: uncaught exception: [Exception... "Component returned failure code: 0x8007000e (NS_ERROR_OUT_OF_MEMORY) [nsIDocShellHistory.useGlobalHistory]"  nsresult: "0x8007000e (NS_ERROR_OUT_OF_MEMORY)"  location: "JS frame :: chrome://browser/content/browser.js :: prepareForStartup :: line 740"  data: no]
```
```

Error: uncaught exception: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: file:///usr/lib64/xulrunner-1.9pre/modules/utils.js :: anonymous :: line 104"  data: no]
```

---

### Post by Bakon Jarser on 2008-05-16
Could this be caused by the fact that Ubuntu ships its own special version of Firefox?  Maybe they don't sync up so well.

I'm interested in running the same kind of setup you are doing with Hardy and Linux Mint but am pretty clueless how to do it.  Is there another thread or a wiki you could point me to for some info?

---

### Post by djhyland on 2008-05-16
> **Bakon Jarser said:**
> I'm interested in running the same kind of setup you are doing with Hardy and Linux Mint but am pretty clueless how to do it.  Is there another thread or a wiki you could point me to for some info?

This I can help you out with.  First, though, how do you have your partitions set up?  Do you have a separate home partition?  If not, look at this: [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")
(I recommend using a live cd like Parted Magic to do so, although it's possible to do it from within Ubuntu using the gparted package.)

Then, after you've separated your /home directory to its own partition, mount that partition at /home.  You can then resize the existing /root directory for Ubuntu to make room for another partition to install /root for another distro.

Hopefully, this helps you.  Good luck!

---

### Post by Gunman1982 on 2008-05-16
Mhh are both systems 64bit versions?
It can be that on the first run of firefox it sets some specific properties in your ~/.mozilla/ directory regarding the installed version, if you boot to 'problematic' account (which I supposed is the other OS) it uses a different version of firefox which can't handle specific settings in your .mozilla directory ... you could try to log in to your troublesome account, move your .mozilla directory away (i.e. 'mv ~/.mozilla ~/mozilla_backup') and then start firefox and see what happens.

---

### Post by Bakon Jarser on 2008-05-16
> I was careful to set up two user accounts so that they share the same user name, user ID, group ID, primary group, and home directory: the works.


This is the part I was curious about.  I'm getting a new hard drive and my old one is going in the trash so setting up a seperate home directory won't be a problem.  But what about the user ID, group ID, and primary group?  I don't even know what those are.

---

### Post by gustl on 2008-05-18
I am not sure if it's really the two partitions causing the problem.
I am experiencing exactly the same problem djhyland is, and my firefox is on a straight one partition ubuntu hardy. 
For me this problem occurred after I installed and deinstalled firestarter.

---

### Post by gustl on 2008-05-18
Hi this seems to be a bug of firefox. 
Creating a new firefox profile via firefox -ProfileManager and importing my old bookmarks worked. This solution is not so comfortable though, because you have to redo your settings and all the saved passwords are gone.
But it worked for me, maybe you try it...

---

