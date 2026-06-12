---
title: "Firefox"
date: 2005-08-27
forum: General Help
---

### Post by John.Michael.Kane on 2005-08-27
I have just intalled ubuntu, and need to know how you apply updates to firefox, also how do you remove programs that you dont need. also i see raid drivers are loaded during boot up this being a laptop install how do you remove thoes you only need somuch stuff for a laptop install...

---

### Post by Tyrial on 2005-08-27
> I have just intalled ubuntu, and need to know how you apply updates to firefox, also how do you remove programs that you dont need. also i see raid drivers are loaded during boot up this being a laptop install how do you remove thoes you only need somuch stuff for a laptop install...

Wow... who would of thought that my first post would be helpful to someone, espicially considering I'm a noob myself... Anyway I was fiddling with this today just after I installed Ubuntu because it is horrible going on the net without Firefox set up right, the easiest way I found is to just use the Synaptic Package Manage. Just go to System->Administration->Synaptic Package Manager and scroll down until you get to mozilla-firefox and then mark it for re-installation. Alternatly you could use the bash console and type
**[INDENT]sudo apt-get install mozilla-firefox [/INDENT] **
although if you are going to do it this way then it is better off just using something I just found then while looking this up
**[INDENT]sudo apt-get upgrade[/INDENT] **
which should upgrade all your currently installed packets. You can also do this through the Synaptic Packet Manager by simply clicking the Mark All Upgrades button in the top right hand corner.

To remove software you can simply use the Synaptic Package Manager once again or use
**[INDENT]sudo apt-get remove "name of packet"[/INDENT] **

Hope that helped. But like I said, I'm a complete Noob (only just installed Linux this morning) so it might not work.

---

### Post by Qylvaran on 2005-08-27
System > Administration > Synaptic Package Manager is where you need to go for program updates, installation, and removal.  The RAID thing, I don't know, but it probably doesn't even start anything if you don't have any RAID setup.  I'm guessing it's a script which checks for RAID and starts the drivers if necessary.  If so, no need to worry about it.

---

### Post by Tyrial on 2005-08-27
> I have just intalled ubuntu, and need to know how you apply updates to firefox, also how do you remove programs that you dont need. also i see raid drivers are loaded during boot up this being a laptop install how do you remove thoes you only need somuch stuff for a laptop install...

Wow... who would of thought that my first post would be helpful to someone, espicially considering I'm a noob myself... Anyway I was fiddling with this today just after I installed Ubuntu because it is horrible going on the net without Firefox set up right, the easiest way I found is to just use the Synaptic Package Manage. Just go to System->Administration->Synaptic Package Manager and scroll down until you get to mozilla-firefox and then mark it for re-installation. Alternatly you could use the terminal and type
**[INDENT]sudo apt-get install mozilla-firefox [/INDENT] **
although if you are going to do it this way then it is better off just using something I just found then while looking this up
**[INDENT]sudo apt-get upgrade[/INDENT] **
which should upgrade all your currently installed packets. You can also do this through the Synaptic Packet Manager by simply clicking the Mark All Upgrades button in the top right hand corner.

To remove software you can simply use the Synaptic Package Manager once again or use
**[INDENT]sudo apt-get remove "name of packet"[/INDENT] **

Hope that helped. But like I said, I'm a complete Noob (only just installed Linux this morning) so it might not work.

---

### Post by John.Michael.Kane on 2005-08-27
@Tyrial sudo apt-get install mozilla-firefox dont work

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-firefox: Depends: firefox but it is not installable


Thanks  though

---

### Post by essexman on 2005-08-27
[QUOTE=SD-Plissken]@Tyrial sudo apt-get install mozilla-firefox dont work


The following packages have unmet dependencies:
  mozilla-firefox: Depends: firefox but it is not installable


Thanks  though[/QUOTE]
Try ```
sudo apt-get install mozilla-firefox --fix-missing
```

You may need to adjust your repositories - check the Ubuntu guide and this thread; [http://www.ubuntuforums.org/showthread.php?p=318495#post318495](http://www.ubuntuforums.org/showthread.php?p=318495#post318495) 
there have been some problem with firefox in Ubuntu but updating to 1.06 seems to fix things and is worth persvering.

I can remember how bad IE 4.01 was and there was nothing anyone could do about it.

Keep posting

Essexman

---

### Post by John.Michael.Kane on 2005-08-27
adjusted repositories and was able to get 1.06.. i do hope this is and other issues are ironed out in the next release..

---

### Post by John.Michael.Kane on 2005-08-27
To any other newusers please save your source file that was use to update fire fox  to cd-rw.. if you have to do a fresh install you will know that fire fox can be updated..

---

