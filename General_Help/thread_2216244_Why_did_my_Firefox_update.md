---
title: "Why did my Firefox update"
date: 2014-04-10
forum: General Help
---

### Post by caver12 on 2014-04-10
[I]I had firefox 28 locked in synaptic. Yet all of a sudden while I was using it it updated to fire fox 29. Don`t want it.
Using Ubuntu 12.04. Haqve already reinstalled Firefox 28. I don`t want this to happen again.
Ant ideas?
Caver12
[/I]

---

### Post by tripp98 on 2014-04-10
it sounds like you have the ppa or software repository for firefox's daily build installed.  as 29 hasnt been released to the masses yet.  under system software & updates under the other tab do you have anything like **ppa:ubuntu-mozilla-daily/ppa **
listed?  

i dont know what the current version of firefox inside ubuntu 12.04 but it isnt the latest version (28)  a quick google search appears to be 11.

---

### Post by Impavidus on 2014-04-10
The current version of firefox in Ubuntu 12.04 (and in any other supported Ubuntu) is 28. I don't know when 29 will be released, but I don't see it announced on the firefox website yet. Of course, not every Ubuntu user would get it at the same time. It can take a number of days.

---

### Post by monkeybrain20122 on 2014-04-10
Not sure why. Firefox 29 will be released on April 28 [https://wiki.mozilla.org/RapidRelease/Calendar](https://wiki.mozilla.org/RapidRelease/Calendar)
Maybe you time travelled to the future.

---

### Post by caver12 on 2014-04-10
> **tripp98 said:**
> it sounds like you have the ppa or software repository for firefox's daily build installed.  as 29 hasnt been released to the masses yet.  under system software & updates under the other tab do you have anything like **ppa:ubuntu-mozilla-daily/ppa **
listed?  

i dont know what the current version of firefox inside ubuntu 12.04 but it isnt the latest version (28)  a quick google search appears to be 11.



It`s not the ppa. The ppa updates thru update manger. This update came out ot the blue. As I said i was using FF when all of a sudden it just upgraded. No update manager.

---

### Post by 23dornot23d on 2014-04-10
What have you got set in 

Under the Edit tab at the top of the screen .....

Preferences - Security - Warn me when sites try to install addons .......... is it ticked 

and what exceptions are there ............

__________________________________________________

Mine had Firefox in there as exeptions .... but after seeing your post - I have removed them for now .....

Can you post a screen shot of the about page ... is it an official version 29

Do you have any addons in place No-script / Adblock Plus etc .......

Seen a couple of odd reports this week on Firefox doing strange things but not sure if its planned or unplanned.

---

### Post by caver12 on 2014-04-10
> **23dornot23d said:**
> What have you got set in 

Under the Edit tab at the top of the screen .....

Preferences - Security - Warn me when sites try to install addons .......... is it ticked 

and what exceptions are there ............

__________________________________________________

Mine had Firefox in there as exeptions .... but after seeing your post - I have removed them for now .....

Can you post a screen shot of the about page ... is it an official version 29

Do you have any addons in place No-script / Adblock Plus etc .......

Seen a couple of odd reports this week on Firefox doing strange things but not sure if its planned or unplanned.


when FF tries to install addons is checked to warn me first.
I got no warning 
I can`t show you the about page as I have already removed FF 29.
But it did show as being FF 29.

---

### Post by Impavidus on 2014-04-11
Standard firefox is capable of upgrading itself, although it shouldn't do so before the new version is released. This feature is removed from the firefox in the ubuntu repos, as the ubuntu package manager already takes care of upgrading in a more secure manner.

---

### Post by caver12 on 2014-04-11
> **Impavidus said:**
> Standard firefox is capable of upgrading itself, although it shouldn't do so before the new version is released. This feature is removed from the firefox in the ubuntu repos, as the ubuntu package manager already takes care of upgrading in a more secure manner.



I know that and I set the update properties to never update. So if you go to Help-about FF there is a button to check for 
updates so there is no automatic update.

---

### Post by Frogs Hair on 2014-04-11
I have a fresh 14.04 installation fully updated and FF 28 . Are you sure you didn't install one of the PPAs ? If you have for example installed the nightly build, locking the version wouldn't work because it is named the firefox-trunk and not Firefox. I don't know if other PPA builds code names as well.

---

### Post by caver12 on 2014-04-11
> **Frogs Hair said:**
> I have a fresh 14.04 installation fully updated and FF 28 . Are you sure you didn't install one of the PPAs ? If you have for example installed the nightly build, locking the version wouldn't work because it is named the firefox-trunk and not Firefox. I don't know if other PPA builds code names as well.



No I have never done the nightlies. The ppas update thru update manager, which never opened.

---

### Post by monkeybrain20122 on 2014-04-11
> **caver12 said:**
> No I have never done the nightlies. The ppas update thru update manager, which never opened.

It doesn't matter whether update-manager opens or not, you could have run a 'sudo apt-get update' , 'sudo apt-get upgrade' somewhere without remembering it...or you could have run the Software centre or synaptic with a few clicks without noticing what happened. If you have the ppa activated then it will get upgraded. So have you added the ppa or not? Time travel may be possible, but doesn't sound likely. :)

BTW, ppas and other updates don't happen just through update-manager, you can update with other means like Software Centre or Synaptic or the terminal. So in a way the update-manager is not needed, in fact I never use it for updating, always use synaptic manually.

---

### Post by caver12 on 2014-04-11
> **monkeybrain20122 said:**
> It doesn't matter whether update-manager opens or not, you could have run a 'sudo apt-get update' , 'sudo apt-get upgrade' somewhere without remembering it...or you could have run the Software centre or synaptic with a few clicks without noticing what happened. If you have the ppa activated then it will get upgraded. So have you added the ppa or not? Time travel may be possible, but doesn't sound likely. :)

BTW, ppas and other updates don't happen just through update-manager, you can update with other means like Software Centre or Synaptic or the terminal. So in a way the update-manager is not needed, in fact I never use it for updating, always use synaptic manually.




Good for you. I use both update manager and synaptic. Sorry but I did none of the above. I was using FF then all of a sudden it opened the check for addons box and the next thing I knew was that I was using FF29. Went into synaptic deleted it, then I had to force the version to get 28 back. A few clicks without knowing what was happening didn`t happen. A ppa will not upgrade without one of the upgrade routes opening.If that was the case and one of them did open it would have opened on top of the FF window which didn`t happen. that would be hard to miss.:?

---

### Post by sammiev on 2014-04-11
I have 3 versions of ?ubuntu on my computer and my FF on all 3 versions are FF28 by default. If you have FF29 you had to add a PPA. Post your source list so we can view it.

---

### Post by monkeybrain20122 on 2014-04-11
> A ppa will not upgrade without one of the upgrade routes opening.If  that was the case and one of them did open it would have opened on top  of the FF window which didn`t happen.

What does this means? If you add a ppa to your sources list then it just upgrades like everything else in your 'normal' repo, that is the whole point of ppa.

---

### Post by caver12 on 2014-04-11
> **monkeybrain20122 said:**
> What does this means? If you add a ppa to your sources list then it just upgrades like everything else in your 'normal' repo, that is the whole point of ppa.



But it just  doesn`t do it by itself. It uses either synaptic or the update manager, just like the 'normal' repo does.

---

### Post by monkeybrain20122 on 2014-04-11
So you are saying that you have never updated??!! Now that would be very unusual to say the least.

Instead of arguing and getting all puzzled why don't you just show us the content of your sources.list and the list of files in /etc/apt/sources.list.d so we can solve the mystery?

Open the terminal and post the outputs of 
```
cat /etc/apt/sources.list
```
and
```
ls /etc/apt/sources.list.d
```

---

### Post by caver12 on 2014-04-11
> **monkeybrain20122 said:**
> So you are saying that you have never updated??!! Now that would be very unusual to say the least.

Instead of arguing and getting all puzzled why don't you just show us the content of your sources.list and the list of files in /etc/apt/sources.list.d so we can solve the mystery?

Open the terminal and post the outputs of 
```
cat /etc/apt/sources.list
```
and
```
ls

```

okay here goes.
Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /
deb-src [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /
deb [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) precise main
deb-src [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) precise main
brenda@brenda-laptop:~$ 
anddeb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

and

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /
deb-src [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /
deb [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) precise main
deb-src [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) precise main


I never said that I never updated. I had the ppa for FF but I got rid of them after 28 because I didn't want 29.
I don't like it.  PPA's only update thru synaptic and update manager. I am not stupid nor am I a linux genuis.
I do know what I am doing. Synaptic only after you open, it give your password, tell it to mark for update or install,
click on apply twice. Update manager wont install anything unless you open it and tell it what to install. Those are the only two ways that a ppa can install anything.;)

---

### Post by monkeybrain20122 on 2014-04-11
What about /etc/apt/sources.list.d?
If you have added the ppa there should be a file called "mozillateam-firefox-next-precise.list" or something similar. Check /etc/apt/sources.list.d, if you find it open it in gedit, if you have disabled or removed the ppa the entries in the file should be commented out or there should be no entry (blank file)

> I don't like it.  PPA's only update thru synaptic and update manager. I am not stupid nor am I a linux genuis.


So do all other updates. The point is, if a ppa is enabled, packages will get update through the normal channel, you won't get told where the updated package come from unless you go through some length to check.

Here is another idea. Open synaptic, locate Firefox, right click and choose properties > version and it will tell you where it comes from. 

Also you might have upgraded BEFORE you removed/disabled ppa,--if you ever did, which I doubt as you seem to have some wrong ideas about how ppa works. In that case the packages installed from the ppa will not be downgraded unless you 'purge' the ppa with ppa-purge.

Edited: Not saying you are stupid but  it is simply impossible unless you upgraded through ppa, **FF29 has not been released **so it is not even in the normal software channel. Well unless you time travelled.

---

### Post by caver12 on 2014-04-11
sources.list.d is a directory not a file.
 /etc/apt/sources.list.d
bash: /etc/apt/sources.list.d: Is a directory.
So I gave you /etc/apt/sources.list.

O know that you don't know if it came from a ppa or thru the 'normal' repository. but a ppa will not update out of the blue. It still has to come thru synaptic orupdate manager. PPAs are not magic. They still follow rules.
FF28- 28.0+build2-0Ubuntu0.12.04.1 (precise-updates) is where it came from. And from the bottom of that window it states,
" Note: To install a version that is different from the drfault one, choose Package-> Force Version...from the menu"
After I deleted 29 that is exactly what I did. I purged the ppa a while back. So the update to 29 did not come from the ppa. I updated to 28 thru the ppa. Then after 29 installed, out of the blue, I uninstalled it thru synaptic and force 28 to install.
And no it is not impossible as that is exactly what happened.
I think you need to tell me how yoou think ppas work.
Even if I did have the ppa enabled, it will update thru the normal channels not by itself. It would still update thru synaptic or update manager. And no ppas will not update thru Ubuntu Software Center.
Also it updated quite awile after I purged the ppa. Even if you doubt that I did.
I know exactly how ppas work. Also I didn't wait to see if it was a beta version. I just immediatly uninstalled it.

---

### Post by caver12 on 2014-04-11
Yes you can get ppas thru Ubuntu Software Center but thy do not update thru it.

---

### Post by Frogs Hair on 2014-04-11
You can't get get a not yet released version of FF through normal updates without having a software source for it enabled . You would find the source in software sources - other software . If you select help and go to about Firefox the version will be displayed and if says anything other than Firefox there is PPA source enabled.  I notice that you have sources in the posted list going back to 9.04 Jaunty and I'm not sure how you can update without errors unless the Ubuntu old repositories are enabled.

---

### Post by monkeybrain20122 on 2014-04-11
> **caver12 said:**
> sources.list.d is a directory not a file.
 /etc/apt/sources.list.d
bash: /etc/apt/sources.list.d: Is a directory.
So I gave you /etc/apt/sources.list. 

I know it is a directory, that's why I asked you to post the outputs of TWO commands, the second lists all the files in the directory.

> O know that you don't know if it came from a ppa or thru the 'normal' repository. but a ppa will not update out of the blue. It still has to come thru synaptic orupdate manager. PPAs are not magic. They still follow rules.

Yeah so you must have time travelled. The Software Centre, synaptic and update-manager are all front ends of the same thing: apt-get. When you add a ppa, it becomes part of the software pool and when you install/update something from any of these front ends or apt-get you get the highest version in the pool which usually is the ppa version.

---

### Post by caver12 on 2014-04-12
> **monkeybrain20122 said:**
> I know it is a directory, that's why I asked you to post the outputs of TWO commands, the second lists all the files in the directory.



Yeah so you must have time travelled. The Software Centre, synaptic and update-manager are all front ends of the same thing: apt-get. When you add a ppa, it becomes part of the software pool and when you install/update something from any of these front ends or apt-get you get the highest version in the pool which usually is the ppa version.

And I did  use both and the second one is at the top. If you will notice that there is aspereration "and" after I posted the results of 
cat /etc/apt/sources.list. so before that "and" is those results. If you new that the second was 
 a directory and would post no results why did you askfor it?

  I did not update using The Software Center , synaptic, or apt-get. Iknow it is part of the software pool as it will be listed in the software repositories. But you still have to go into one of those and activate the update feature for them to update. I DID NOT DO THAT.

---

### Post by monkeybrain20122 on 2014-04-12
Well so you have never updated any sofware? I find it hard to believe. My guess is that you have done an update before you removed the ppa so the version stayed. Since it is not there anymore you can't find out where it is from. But there is no way that it happened out of thin air as Firefox 29 has not even been released and therefore not in the normal software channel.

---

### Post by caver12 on 2014-04-12
> **monkeybrain20122 said:**
> Well so you have never updated any sofware? I find it hard to believe. My guess is that you have done an update before you removed the ppa so the version stayed. Since it is not there anymore you can't find out where it is from. But there is no way that it happened out of thin air as Firefox 29 has not even been released and therefore not in the normal software channel.

I never said that I never updated any software. You need to comprehend what you read. I do it all the time. I only updated FF  using the mozilla ppa up to FF28. Then stopped using the ppa. If You have a vesion locked in synaptic neither the normal repositories nor your ppas will be able to update the version. and even if you don't have it locked they cannot updated without your approval. When I locked the version the updates for FF quit showing up.
And it did  update out off thin air as neither synaptic nor update manager were opened.This update happened without my approval.

---

### Post by monkeybrain20122 on 2014-04-12
> **caver12 said:**
> I neber said that I never updated any software. You need to comprehend what you read. I do it all the time. I only updated FF  using the mozilla ppa up to FF28. Then stopped using the ppa. If You have a vesion locked in synaptic neither the normal repositories nor your ppas will be able to update the version. and even if you don't have it locked they cannot updated without your approval.
And it did  update out off thin air as neither synaptic nor update manager were opened.This update happened without my approval.

That was what I  said, when you update with synaptic and choose 'update all' or with the terminal you may not be very careful to see all the packages. You can check synaptic's history if you want but I bet you updated FF inadvertently somehow before you disabled the ppa.

What is your alternative theory? That space aliens did it or you time travelled to the future and get FF29?  

FF get updated when it is released in the normal channel so I don't even know why you need the ppa in the first place if you are not using the beta. And as someone said earlier, if you use the ppa the firefox package name would be different (like firefox-trunk or whatever instead of firefox) so the synaptic lock will not work.

---

### Post by caver12 on 2014-04-12
> **monkeybrain20122 said:**
> That was what I  said, when you update with synaptic and choose 'update all' or with the terminal you may not be very careful to see all the packages. You can check synaptic's history if you want but I bet you updated FF inadvertently somehow before you disabled the ppa.

What is your alternative theory? That space aliens did it or you time travelled to the future and get FF29?  

FF get updated when it is released in the normal channel so I don't even know why you need the ppa in the first place if you are not using the beta. And as someone said earlier, if you use the ppa the firefox package name would be different (like firefox-trunk or whatever instead of firefox) so the synaptic lock will not work.



i was using the ppa because by using it I was way ahead of Ubuntu to get there. Once Ubuntu got there I no longer needed the ppa. I *did try *29beta but I downloaded it and place it on my desktop to use instead of installing it. that way
I found out that I didn't like it. And  all I had to do was delete it after I was done. No uninstalling.
But it did not upgrade thru synaptic. Synaptic never opened. Synaptic will not install any updates unless you give it permission to.  Which never happened. 
At this time I have no other theory because I don't know how it happened.
Being that you have to open synaptic and tell it to apply updates and and enter my password,which I didn't do, synaptic would have been the top window, which it wasn't for me to inadvertently update, you tell me how I inadvertently did itAnd update manager didn,t do it as it would have been ontop, which it wasn't, I would have to had to have pushed the install button. Also neither synaptic nor update manager open themselves. And neiter does terminal.

While I was using FF, and it was the only thing opened, all of a sudden the checking your addons opened and closed just about that fast. So I went to help:about and it stated that it was version was 29. So I ***immediately ***got rid of it. I didn't even look at it long enough to see if it was a beta, but it is sure starting to look like chrome.
Get your head around that it had nothing to do with the ppa.
As I showed you I have other ppas in my sources list and none of them update without my approval. If you think they do then you need to learn how to update your own system.

---

### Post by 23dornot23d on 2014-04-12
I have a feeling if you ran the 29 version it left something in the configuration settings ........ but not completely sure on this one


Second option there .......... looks like it will do the update and install ........... but the more
you say about running this version - the more seems it may have left something behind that
then did this automatic update and install ...........

Not sure if it will still be there - in your configurations for firefox - if you did a clear out and clean install afterwards.

See Update 59 on this link >>>  [http://www.askvg.com/download-mozilla-firefox-latest-nightly-version/](http://www.askvg.com/download-mozilla-firefox-latest-nightly-version/)


This picture came from the above link .... only put it here for ease of finding it and viewing what it does ........

[IMG]http://media.askvg.com/articles/images5/Firefox_New_Automatic_Update_Options.png[/IMG]

---

### Post by sammiev on 2014-04-12
If you would have read the first post in this [thread]("http://ubuntuforums.org/showthread.php?t=1712247") you would be in the mess your in.

---

### Post by monkeybrain20122 on 2014-04-12
> **caver12 said:**
> 
While I was using FF, and it was the only thing opened, all of a sudden the checking your addons opened and closed just about that fast. So I went to help:about and it stated that it was version was 29. So I ***immediately ***got rid of it. I didn't even look at it long enough to see if it was a beta, but it is sure starting to look like chrome.
Get your head around that it had nothing to do with the ppa.
As I showed you I have other ppas in my sources list and none of them update without my approval. If you think they do then you need to learn how to update your own system.

Well you never told us where FF29 came from and you blamed the software manager for it all along. Now the mystery is solved. You downloaded it yourself and since you didn't use a new profile to test it some of its settings get left in your .mozilla folder. I think 23dornot23d makes a lot of sense. It didn't matter that you closed FF29 immediately, those settings were created as soon as you started FF29. 

Now I don't think Firefox actually got upgraded even though it might report itself as FF29, because, if you installed FF28 through the software channel you can't upgrade it without root permission and whatever mozilla automatic update is supposed to do it can only alter your configuration file (~/.mozilla) which may or may not change FF's look.

You can clean everything (and lose your bookmarks, addons etc) by simply removing the ~/.mozilla folder though I think that would be overkill, it is not like you get a virus or something.

---

### Post by caver12 on 2014-04-12
23dornot23d
I know I need to clean them out. No I don't have the old repositories enabled and I don't get any errors. I guess that's why I keep forgetting to  cleaning them out.

---

### Post by caver12 on 2014-04-12
23dornot23d
No I don't ever let any programs automatically update. I always set the update feature to do not update. When  I had the 29 beta I set up a seperate profile which was deleted at the same time. If you don't set up a seperate profile then when you open one or the they act like a new installation. Nothing was installed.

---

### Post by caver12 on 2014-04-12
> **sammiev said:**
> If you would have read the first post in this [thread]("http://ubuntuforums.org/showthread.php?t=1712247") you would be in the mess your in.

[ ]("http://ubuntuforums.org/member.php?u=628319")[**[COLOR=#000000]sammiev[/COLOR]**]("http://ubuntuforums.org/member.php?u=628319")
I wrote the first post. I am not in a mess. I already took care of it. Just don't know why. Any ways how would rereading my first post solve anything?

---

### Post by caver12 on 2014-04-12
> **monkeybrain20122 said:**
> Well you never told us where FF29 came from and you blamed the software manager for it all along. Now the mystery is solved. You downloaded it yourself and since you didn't use a new profile to test it some of its settings get left in your .mozilla folder. I think 23dornot23d makes a lot of sense. It didn't matter that you closed FF29 immediately, those settings were created as soon as you started FF29. 

Now I don't think Firefox actually got upgraded even though it might report itself as FF29, because, if you installed FF28 through the software channel you can't upgrade it without root permission and whatever mozilla automatic update is supposed to do it can only alter your configuration file (~/.mozilla) which may or may not change FF's look.

You can clean everything (and lose your bookmarks, addons etc) by simply removing the ~/.mozilla folder though I think that would be overkill, it is not like you get a virus or something.


23dornot23d  did make a lot of sense. So far you haven't. Aliens and I must have inadverdently clicked on something, When it would take morte than an inadverden click. Read what I replied to him.
You need to reread all the posts and comprehend them. Nowhere did I blame the software manager. In fact I  said it couldn't be it. Mainly for those reasons that it can't open itself let alone update by itsself.  Since I set up a seperate profile for it(FF29)see reply to 223dornot23d  , there was no conflict with 28. See my other post to 23dornot23d as to why I set up its own profile. It was deleted at the same time as 29 was. No installing.
As far as being updated I was. It no longer looked like 28. It looked like the chrome browser.
As far as being updated thru the update channel I have said all along that I couldn't have been. You are the one that
kept insisting that I must have clicked on something inadvertently. 
The automatic update was set to never. The config file wasn't changed. In fact the file firefox.last-version shows it as being 5.0. If 29  changed things the second it was installed why didn'f it show in tha23dornot23d t file?  There is nothing in my files that show 29. As far as only change tne config file and not the version, Why did it look like chrome?

---

### Post by buzzingrobot on 2014-04-12
Just to clarify a point, installed PPA's are part of the update process no matter how you run the updates. I invariably update via apt- get and PPA's are updated along any other source on the list.

It's been my experience that locking packages in Synaptic will not prevent their update via another tool.

---

### Post by caver12 on 2014-04-12
> **Frogs Hair said:**
> You can't get get a not yet released version of FF through normal updates without having a software source for it enabled . You would find the source in software sources - other software . If you select help and go to about Firefox the version will be displayed and if says anything other than Firefox there is PPA source enabled.  I notice that you have sources in the posted list going back to 9.04 Jaunty and I'm not sure how you can update without errors unless the Ubuntu old repositories are enabled.



I know you can't get an update without having a source for it and there is no mozilla ppa in my sources list and hasn't been for a while. As I already got rid of it I can't show you the source.
None of the old repositories show up in Synaptic.

---

### Post by 23dornot23d on 2014-04-12
Fact that OP is adamant about it makes me believe you saw it happen and cannot explain it ........ but without a log.

What can we say ...... by deleting everything to do with it ......... the evidence went missing - see post #28

> 
While I was using FF, and it was the only thing opened, all of a sudden  the checking your addons opened and closed just about that fast. So I  went to help:about and it stated that it was version was 29. So I ***immediately ***got rid of it.** I didn't even look at it long enough to see if it was a beta**, but it is sure starting to look like chrome.



Still sounds like only the customization of the window got changed ...... but .........

Try this for next time  ........ [https://developer.mozilla.org/en-US/docs/Mozilla/Debugging/HTTP_logging](https://developer.mozilla.org/en-US/docs/Mozilla/Debugging/HTTP_logging)

Might give some more clues as to what happened should it occur again .......

---

### Post by sammiev on 2014-04-12
> **caver12 said:**
> [ ]("http://ubuntuforums.org/member.php?u=628319")[**[COLOR=#000000]sammiev[/COLOR]**]("http://ubuntuforums.org/member.php?u=628319")
I wrote the first post. I am not in a mess. I already took care of it. Just don't know why. Any ways how would rereading my first post solve anything?

Read my post above and click on the word "thread" in orange. I never said your 1st post.

---

### Post by caver12 on 2014-04-12
> **23dornot23d said:**
> Fact that OP is adamant about it makes me believe you saw it happen and cannot explain it ........ but without a log.

What can we say ...... by deleting everything to do with it ......... the evidence went missing - see post #28



Still sounds like only the customization of the window got changed ...... but .........

Try this for next time  ........ [https://developer.mozilla.org/en-US/docs/Mozilla/Debugging/HTTP_logging](https://developer.mozilla.org/en-US/docs/Mozilla/Debugging/HTTP_logging)

Might give some more clues as to what happened should it occur again .......



Thanks for the link. Never had the need to do it before. To bad it is too late as I can't reproduce what happened. What I read there is HTTP logging only is good if you can reproduce the problem.
How would the customization be the only thing changed when about:firefox and synaptic showed 29? That's why I had to force the version to get 28 back.
Thanks for your help.):P

---

### Post by caver12 on 2014-04-12
> **sammiev said:**
> If you would have read the first post in this [thread]("http://ubuntuforums.org/showthread.php?t=1712247") you would be in the mess your in.


Okay, I'll bite. What post were you refering to? As far as I know this is all 1 thread. So my post was first. I can find nowhere in Ubuntuforums about changing to a thread view like you can in Thunderbird.
I even googled it and found nothing. In fact near the top of this page it is showing that I am repling to this thread but there is  no change in the in the order in which the posts are shown. So I was first in this thread.

---

### Post by caver12 on 2014-04-12
> **sammiev said:**
> If you would have read the first post in this [thread]("http://ubuntuforums.org/showthread.php?t=1712247") you would be in the mess your in.



Sorry I didn't view your threads as a link to another web page. I was thinking "this thread". When I did go to that page it stated 
"repository ppa:mozillateam/firefox-next   [I][B][COLOR=DarkOrange]This ppa upgrades your default Firefox installation,
 only with beta versions.[/COLOR][/B][/I]"  Then "To upgrade to the latest aurora version use the *[firefox-aurora]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/firefox-aurora")* ppa" "
I never had the aurora ppa. I only had the firefox-next ppa. And when it updated I no longer had the firefox-next ppa
So being that I never had the aurora ppa how did it upgrade to 29 which is aurora..
So how did viewing that page solve my problem. And I have never used the nightlies.

---

### Post by sammiev on 2014-04-13
> **caver12 said:**
> Sorry I didn't view your threads as a link to another web page. I was thinking "this thread". When I did go to that page it stated 
"repository ppa:mozillateam/firefox-next   [I][B][COLOR=DarkOrange]This ppa upgrades your default Firefox installation,
 only with beta versions.[/COLOR][/B][/I]"  Then "To upgrade to the latest aurora version use the *[firefox-aurora]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/firefox-aurora")* ppa" "
I never had the aurora ppa. I only had the firefox-next ppa. And when it updated I no longer had the firefox-next ppa
So being that I never had the aurora ppa how did it upgrade to 29 which is aurora..
So how did viewing that page solve my problem. And I have never used the nightlies.

Now you can save your bookmarks add the correct ppa and install FF28.

---

### Post by caver12 on 2014-04-13
> **23dornot23d said:**
> I have a feeling if you ran the 29 version it left something in the configuration settings ........ but not completely sure on this one


Second option there .......... looks like it will do the update and install ........... but the more
you say about running this version - the more seems it may have left something behind that
then did this automatic update and install ...........

Not sure if it will still be there - in your configurations for firefox - if you did a clear out and clean install afterwards.

See Update 59 on this link >>>  [http://www.askvg.com/download-mozilla-firefox-latest-nightly-version/](http://www.askvg.com/download-mozilla-firefox-latest-nightly-version/)


This picture came from the above link .... only put it here for ease of finding it and viewing what it does ........

[IMG]http://media.askvg.com/articles/images5/Firefox_New_Automatic_Update_Options.png[/IMG]




Bering that I had seperate profilesthat woudn'tt happen. But Then i got thinking if I did have 1 profile every time I would 
open one after another then newly opened one would always overwrite the other. So I get rid of one the other alwys checks its profile and overwrites it if needed. No 29. That's why if you use one profile when one is opened after the other 
they always act as if they were just updated. I leared that quite a while back so if I am trying anew version at the same time that I have another version, use two profile.
I went to the link about nightlies that you supplied. 1 I havenever used the nightlies. 2. It said this "Finally Mozilla has finalized the "**Silent Background Update**" feature in Firefox. The latest **Firefox 15.0**  nightly build comes with this new feature enabled. Now when you install  an update in Firefox and restarts it to apply the update, Firefox no  longer takes too much time to install the update and no longer shows any  screen such as "Installing update...". Now the update is installed in  background while you are using Firefox.out"
That is truebut that is if you leave the setting in Prefrences-Advanced-Updates the way Mozilla set it up. Then everytime you go to Help-About firefox it would automaticly in Windows. But if you change that setting to never update it won't you have to do it manually. But in Ubuntu the only thing I  have  in Prefrences-Advaced- Updates is automatically update addons, opening About-Firefox only shows you what version you have, and that is  in the direct download, ppas, and the Ubuntu package.

---

### Post by caver12 on 2014-04-13
> **sammiev said:**
> Now you can save your bookmarks add the correct ppa and install FF28.

Never lost my bookmarks, backed them up. Already reinstalled thru synaptic after a version force. Don't need the ppa any more as Ubuntu repository is up to 28 and I don't want to go to 29. Also in doing that dosn't explain why it updated without opening synaptic, update manager, or the terminal.

---

