---
title: "Magic command destroys entire Kubuntu installation!"
date: 2005-10-17
forum: General Help
---

### Post by blastus on 2005-10-17
So I'm having problems with not being able to 
[compile my ltmodem drivers](http://www.ubuntuforums.org/showthread.php?t=77537). "cat /proc/version" returns gcc version 3.4.5 while "gcc -dumpversion" returns 4.0.2. So I decide to open Adept and mark gcc for removal. I click on the commit button and off it goes, uninstalling hundreds of packages including adept itself destroying the entire installation! :???:

---

### Post by Segovia on 2005-10-17
[QUOTE=blastus]So I'm having problems with not being able to 
[compile my ltmodem drivers](http://www.ubuntuforums.org/showthread.php?t=77537). "cat /proc/version" returns gcc version 3.4.5 while "gcc -dumpversion" returns 4.0.2. So I decide to open Adept and mark gcc for removal. I click on the commit button and off it goes, uninstalling hundreds of packages including adept itself destroying the entire installation! :???:[/QUOTE]
Remember back when you first starting using GNU/Linux, how everyone would warn you of the dangers of using root?  "A few wrong keystrokes and your whole install could be gone!!!"

Well, I always thought they were exaggerating, but I guess not!  :mad:

---

### Post by stodge on 2005-10-17
[QUOTE=Segovia]Remember back when you first starting using GNU/Linux, how everyone would warn you of the dangers of using root?  "A few wrong keystrokes and your whole install could be gone!!!"

Well, I always thought they were exaggerating, but I guess not!  :mad:[/QUOTE]


That's rather a pointless and irrelavant comment.

I had the same problem - I wanted to remove a package (can't remember the name), so I marked it for deletion and it deleted the whole KDE desktop. 

I always preview the changes (click the big PREVIEW button) before committing any changes. I saved myself this way - I wanted to remove OpenOffice, so I marked it for removal. I clicked the preview and it said it was going to remove KDE. This SHOULD NOT happen. I realise there are meta-packages that group things together, but removing OpenOffice should NOT remove the desktop!!!

---

### Post by Segovia on 2005-10-17
[QUOTE=stodge]That's rather a pointless and irrelavant comment.[/QUOTE]
Yep...  But with a thread Title of "Magic command destroys entire Kubuntu installation!" (which sounds like a Tabloid headline), I thought a little humor wouldn't be out of place.  ;)

---

### Post by One Quick Question on 2005-10-18
[QUOTE=stodge]I wanted to remove OpenOffice, so I marked it for removal. I clicked the preview and it said it was going to remove KDE. This SHOULD NOT happen. I realise there are meta-packages that group things together, but removing OpenOffice should NOT remove the desktop!!![/QUOTE]
If you realize there are meta-packages then you should realized that removing the kde (or kde-base or kubuntu-desktop) meta-packages cause no damage.

As to the original post, well, be careful of what you're doing.  Don't uninstall something important!

To be honest though, I wouldn't expect a feature any time in the near future that would warn against such things.  It would help to make the distro more user-friendly!

---

### Post by MisterMarshall on 2005-12-15
I don't know if someone give you all a fix for your problem?
I had the same problem when I removed GCC-4.0 (downgrade)

I reinstalled APT first (you also need te reinstall the depencies)
If you never cleaned your system the are all located at /var/cache/apt/archives/
So now use dpkg -i /var/cache/apt/archives/apt.***.deb and you can use apt again.
(I use kubuntu btw, so the names could be diferent)
then use the "apt-get update" and run "apt-get -f dist-upgrade" to fix most of you packages.
Then restore you distro default files with "apt-get install kubuntu-desktop" 
(btw I fixxed it with KDE running and by using adept)Now all the files you need will be restored, restore the rest you need manual.
This took me just 5 min so much faster than reinstall.

---

### Post by noigeaR on 2005-12-15
I think it's one of the biggest weaknesses of the current adept version that it doesn't show you a preview before commiting. That's one of the reasons the first package I install on a new kubuntu is still synaptic. It's just too easy to screw up your whole system in adept by forgetting to manually check the preview before clicking the commit button.

---

### Post by MisterMarshall on 2005-12-15
Yeah well I have to say it's all made very simple, I like that for a desktop/laptop.
But now can every noob ;)  remove there GCC and trash there system, but I think the guy's from Ubuntu will fix that (or I hope so, with a development tool for the advanced user), but it's funny that it has a build-in suicide function.

---

