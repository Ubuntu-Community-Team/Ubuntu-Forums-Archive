---
title: "Firefox unusable after upgrade (xulrunner issues)"
date: 2008-06-10
forum: General Help
---

### Post by zbrox on 2008-06-10
Hello there,

First of all let me say that I've searched around the forums and Launchpad to find something similar to my problem, but to no avail. After an upgrade my Firefox just broke down. I found out that there was an incompatibility with Xulrunner. But this incompatibility wasn't at package level, so the upgrade went fine. After that however nothing was fine :)

The Add-On Firefox window reported that Xulrunner is incompatible with the current version and that was it. I decided to wait for an upgrade but after the upgrade came, nothing really happened. The windows were still messed up, no address bar, no search bar. Most of the features don't work, as xulrunner is a main part of Firefox.

I tried deleting my profile, purging the packages and reinstalling them, doing it again but from a different repository, then from the hardy-updates repo and so on. The problem persists. So I'm forced to use Opera. This is a very speedy browser and all, but I'm used to my Firefox with a couple of extensions.

Anybody else got that problem?

Thanks in advance!

---

### Post by Bubba64 on 2008-06-10
Have you tried the launchpad version of FF rc2 they have also been updating the xulruuner to run with rc2 I have mine running. I ask this inspite of your detailed description of your search for answers.

---

### Post by zbrox on 2008-06-10
I have tried the FTA PPA repo. It even had an upgrade to RC2 today, but yet again I don't see even a remote change in behaviour.

I forgot to mention that after a second start of Firefox, after cleanly creating a profile, I get a segmentation fault. If I delete the profile and start Firefox, at least it starts. But on the second run, it spews a segfault.

---

### Post by Bubba64 on 2008-06-10
> **zbrox said:**
> I have tried the FTA PPA repo. It even had an upgrade to RC2 today, but yet again I don't see even a remote change in behaviour.

I forgot to mention that after a second start of Firefox, after cleanly creating a profile, I get a segmentation fault. If I delete the profile and start Firefox, at least it starts. But on the second run, it spews a segfault.

I am not a true computer geek but I thought I would check where your at. I hope somebody can help you.

---

### Post by Mr Tim on 2008-06-10
I'm having the same problem (it just started today), I don't think that it is Firefox (or xulrunner) as I'm having the same trouble with Kompozer. Just for the record Firefox was crashing when I was using the 'close tab' command of firegestures and Kompozer was crashing when I used the '<' symbol when altering page source. 
I'll certainly keep watch to see if anyone can help with this problem.

---

### Post by zbrox on 2008-06-10
I've installed Thunderbird 3 just to see if there are similar problems. Judging by the Add-On, Preferences, etc xulrunner is the culprit. Thunderbird 3 is with the same problems.

Firefox 2 and Thunderbird 2 however don't have those problem, though they use xulrunner-1.9 too.

---

### Post by OliW on 2008-06-10
Well I thought I was going mad. No address bar. No extensions. No interface text-input boxes, at all. And no amount of config-wiping fixes it. Everything else you've said rings true here too.

[img]http://i.thepcspy.com/oli/firefoxhelp.jpg[/img]

Yes, I know that *says* RC2 (not sure if that's the case on a new profile with the other people here) but here are my versions:

firefox: 3.0~rc1+nobinonly-0ubuntu0.8.04.1
xulrunner: (none)
xulrunner-1.9: 1.9~rc1+nobinonly-0ubuntu1~8.04.2

---

### Post by dmflad on 2008-06-10
Thanks to the latest update set I applied today I no longer can use Firefox to connect to work. All was fine yesterday. All was actually better before moving to newest Ubuntu and its version of Firefox. Nothing but problems with web connects since then. 

So much quality control - so much hype - long term support indeed.

Now I have to send time tracking down the fixes so I can work from home again. (sigh) Not my grandma's Ubuntu Firefox this time folks - more like Hardy Herring (red herring).

---

### Post by kreese on 2008-06-10
I didn't know that there was a repo that allowed for download of RC2.  I needed to upgrade from firefox B5 so I got it installed by doing everything via command line.  

I downloaded the firefox RC2 from the firefox site.  You'll need to rename the folder so it doesn't conflict with some of the other folders.  The original firefox b5 is located in /usr/lib (need to sudo to mv the new folder into this location).

Once rc2 is moved into this folder, if you want your desktop icon to load firefox, just right click and go to properties then under command go to browse and find the file named "firefox" in the new rc2 folder.

I deleted the b5 folder once I knew rc2 was working.  I didn't have to reinstall any of my extensions, they showed up in rc2.

Hopefully that helps.  I never really cared for repos, they don't update the software I need fast enough for me.  I don't know if this will allow for automatic firefox updates yet (havent release a new version, but their code is there so it might).

my xulrunner version is 1.9b5, which I think is still around from the beta 5 version of firefox, but rc2 is running flawlessly.

---

### Post by Bentley on 2008-06-10
I'm seeing the same issue after updating Ubuntu this morning.  Firefox has no address bar!

I've tried running firefox in safe mode, I've tried reinstalling.  Help!

---

### Post by OliW on 2008-06-10
Is there a Launchpad bug for this yet? 

I'm amazed at how awesome I am (being able to navigate the web without an address bar == super1337) but I'm also getting tired of it too. So many ads too >_<

<3 AdBlock Plus.

---

### Post by skullmunky on 2008-06-10
If the problem you're having is with various betas and RC's of FF3, you can  also try installing Firefox 2 and wait 'til this gets fixed in a nice and clean way.

---

### Post by Bentley on 2008-06-10
> **skullmunky said:**
> If the problem you're having is with various betas and RC's of FF3, you can  also try installing Firefox 2 and wait 'til this gets fixed in a nice and clean way.

IIRC, firefox3 is the default browser in Hardy.

---

### Post by eljaco on 2008-06-10
Same problem here. 

Also, no navigation icons: I am using the Crashbit icon theme and none of my icons show up in firefox (except for favicons in bookmarks). Not sure if this is a firefox problem or a xulrunner problem...

Changed my settings to show Icons and Text (right-click navigation toolbar and click on customize... and then select Icons and Text from the drop-down) and now I can at least see the words "Back Forward Reload Stop Home" but Back and Forward do not work (they never become enabled.)

---

### Post by kreese on 2008-06-10
Did anyone happen to try a "sudo apt-get remove xulrunner xulrunner1.9 xulrunner-1.9-gnome-support" then, "sudo apt-get install xulrunner1.9 xulrunner-1.9-gnome-support"?  You could probably do it through synaptic as well, just search xulrunner.

if it is an xulrunner issue, I dont know if reinstalling firefox would get rid of the problem.  Reinstalling xulrunner should help, hopefully.  I can't recreate the problem so I'm trying to guess at possible issues.

---

### Post by eljaco on 2008-06-10
Reinstalling xulrunner helped - now I can see the icons, but still no address bar or search bar.

Thanks, kreese.

---

### Post by OliW on 2008-06-10
I've got a metric ton of stuff that depends on xulrunner. Canning it to reinstall would take too much with it :(

---

### Post by kreese on 2008-06-10
Ahh, I tried...  It might be caused by a corrupt localstore.rdf file.  Might try running firefox in safe mode then on the pop-up select the option "Reset toolbars and controls" and click "Make Changes and Restart".  

[http://kb.mozillazine.org/Search_engines_disappear_from_Search_Bar](http://kb.mozillazine.org/Search_engines_disappear_from_Search_Bar)

That might be the same issue?

---

### Post by kreese on 2008-06-10
Did you try a "Mark for Reinstallation" through Synaptic Package Manager?  I dont think that will whip all of the programs.

---

### Post by eljaco on 2008-06-10
kreese, reseting the toolbars and controls did not fix the issue.

Note, I ran firefox via the terminal, and this is what I got:

~$ firefox-3.0 
*** e = [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: chrome://browser/content/utilityOverlay.js :: getShellService :: line 307"  data: no]
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x805f150: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805f150: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805f150: NP_GetValue
GCJ PLUGIN: thread 0x805f150: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805f150: NP_GetValue return
GCJ PLUGIN: thread 0x805f150: NP_GetValue
GCJ PLUGIN: thread 0x805f150: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805f150: NP_GetValue return
*** Exception loading string bundle: Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIStringBundle.GetStringFromName]

(firefox:8293): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8293): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

---

### Post by OliW on 2008-06-10
Yeah resetting does nothing. I've tried nuked my entire ~/.mozilla dir and that does nothing to fix the issue. Not sure if there's an equivilent ~/ xul folder that I could try the same to nuke all xulrunner config.

---

### Post by kreese on 2008-06-10
eljaco, Did you try a reinstallation of firefox since updating xulrunner?  maybe a "sudo apt-get remove firefox-3.0" then, "sudo apt-get install firefox-3.0" (or again through synaptic).  I'm really just guessing now.

---

### Post by eljaco on 2008-06-10
Reinstalling firefox via Synaptic did not work. I bet we'll just have to wait til someone fixes this and pushes an update to the repos.

---

### Post by kreese on 2008-06-10
OliW, unfortunately, I don't see a ~/.xulrunner folder, you could try "sudo rm -r /usr/lib/xrunner1.9" and see if a "sudo apt-get install xulrunner1.9 xulrunner-1.9-gnome-support" does the trick

---

### Post by kreese on 2008-06-10
eljaco, what about a complete removal of all of the files?  Reinstallation might keep some local files in the directories, and one of these may be corrupt.

---

### Post by Zopilote on 2008-06-10
My workaround to this issue was to install FLOCK and import my Firefox profile.

[FONT="Courier New"]sudo apt-get install flock[/FONT]

Now, I'll wait until ubuntu developers release the fix, meanwhile is a PITA when Firefox is broken.

Chava Jiménez

---

### Post by kreese on 2008-06-10
Sounds good, I dont see how this is actually a "workaround" for the problem at hand though.

It does not sound like an ubuntu issue either.  I've just added the repo version of Firefox-3.0 and have had no problems with it.  There has to be a corrupt file somewhere in the firefox-3.0 folder.  It should just be a matter of finding the right file.

---

### Post by dmflad on 2008-06-11
I left the xulrunner bits alone - but removed Firefox3 bits by dropping its folder. Then went and got most recent Firefox2 from and installed it. Had to redo my Java and Juniper bits but I got what I needed: the ability to connect to work so I can work from home. Everything else seems to be running okay but I have a very plain/simple install on my Ubuntu LT. 

Still think whoever decided beta stuff belonged in an LTS release needs 20 lashes with a wet noodle.

---

### Post by OliW on 2008-06-11
Well I upgraded to the hardy-proposed versions of xulrunner-1.9 and firefox and the bug is still very much here. Time to go on a mass-deleting-and-reinstalling spree.

If this carries on for too much longer I'll be looking at a complete reinstall.

---

### Post by OliW on 2008-06-11
Well I've got a fix. It's ugly and not for the real beginners but if you follow it, you get a working address bar, working XUL stuff and last, but not least, FF RC2. RC2 brings a swathe of very real performance improvements for Linux (at least for me).

I used to use this to test the latest betas before I settled on repo versions but now this bug is here, I thought I see if this worked. The benefit of following this guide is that it should be non-destructive. As soon as there's a stable, fixed repo version, you can undo everything here with a couple of simple commands...

This guide is built off the back of a million others. It's been sitting in my Tomboy and I've hacked a few bits and smoothened of a couple of others... Needless to say this is all at your own risk and 

Start by opening up a terminal window at your home dir and backing up your mozilla profile:
```
cd ~
cp -R .mozilla .mozillabak
```

Download the latest version [from here]("http://www.mozilla.com/en-US/firefox/all-beta.html"), save it in your home dir (or cd to where you downloaded it) and then we need to untar it to /opt.
```
sudo tar -C /opt -jxvf firefox-3.0rc2.tar.bz2
```

We also need a C++ lib. Well I know this was the case for the betas.. It's probably not true now but it wont hurt:
```
sudo apt-get install libstdc++5
```

You can test that it works now, if you'd like. Just close all instances of Firefox, press alt+f2 and type: /opt/firefox/firefox

Assuming that all works for you, there are just two things to do: import your plugins in a sensible way and redirect "firefox" to our /opt version to keep all calls standard.
```
cd /opt/firefox/
sudo rm -rf plugins
sudo ln -s /usr/lib/firefox-3.0/plugins/ .

# First, /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
# Then, /usr/bin/mozilla-firefox, used as the default gnome browser
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
```

When you want to revert to a repo version:
```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm /usr/bin/mozilla-firefox
sudo dpkg-divert --rename --remove /usr/bin/mozilla-firefox
```

Good luck.

---

### Post by Bentley on 2008-06-11
Please follow (and contribute to if you can) this issue here:

[https://bugs.launchpad.net/bugs/238710](https://bugs.launchpad.net/bugs/238710)

---

