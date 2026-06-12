---
title: "Compiz plugins keep unchecking themselves in hardy"
date: 2008-04-26
forum: General Help
---

### Post by ram100987 on 2008-04-26
I have a dell 1420n w 7.10 preinstalled and compiz ran perfectly.  I recently upgraded to hardy which went flawlessly as far as I can tell.  I just realized however that whenever I go into the advanced desktop effects settings I can enable cube and rotate cube but if I try to enable most anything else(like animations, 3d windows, cube caps, etc.) it will uncheck itself as I'm looking at it after only a second or two. I've search google, ubuntu forums and compiz-fusion forum and can't find anything pertaining to this issue.  Any one else have this issue and/or know how to fix it?  This is really annoying.

p.s. my laptop has the nvidia 8000 series upgrade dell offers.

---

### Post by Karibbe on 2008-04-26
I have a similar problem but, only the 3D plugin unchecks itself. One thing to check is that you have selected "Custom Effects" in the new Ubuntu’s default Compiz desktop effects...it may help.

---

### Post by Zorael on 2008-04-27
If you're using ccsm to configure stuff (compizconfig-settings-manager), go into preferences, export your profile, change backend to flat-file and import the profile again. Should help.

---

### Post by ram100987 on 2008-04-27
> **Karibbe said:**
> I have a similar problem but, only the 3D plugin unchecks itself. One thing to check is that you have selected "Custom Effects" in the new Ubuntu’s default Compiz desktop effects...it may help.

I don't see where to select custom effects... It offers none, normal, or extra.

---

### Post by ram100987 on 2008-04-27
> **Zorael said:**
> If you're using ccsm to configure stuff (compizconfig-settings-manager), go into preferences, export your profile, change backend to flat-file and import the profile again. Should help.

although I didn't export and import my profile I did try changing it to flat-file and it did the same thing as with backend.

---

### Post by ACGarib on 2008-04-27
I've got the same problem you have after upgrading from gusty to hardy. Most of the plugins uncheck themselves if I check them.

I read somewhere that removing .compiz in the home directory if it's there helps, but it didn't work for me.

My jpeg plugin doesn't work either so I have to use png images for my backgrounds, but for some reason, the picture quality is very poor.

Hopefully there will be a fix soon.

---

### Post by ihatethedekoys on 2008-04-28
Same problem here. Nothing I've tried has worked.

---

### Post by ram100987 on 2008-04-29
I figured out how to select custom under apearance.  I had to install simpleccsm.  However, even though I can now set the appearance to custom, whether I use the original settings manager or the simple settings manager it does not effect anything.

---

### Post by Zorael on 2008-04-29
From the ground up, then.

Export your profile in CCSM so you have it saved someplace. Go into Software Sources and make sure that you don't have any third-party repositories enabled. Then enter the following.
```
$ sudo aptitude update
$ sudo aptitude clean
$ sudo aptitude purge ~ncompiz ~nemerald ~nlibdeco ~nberyl
$ rm -r ~/.compiz     # gets rid of your compiz settings completely
$ sudo aptitude install compiz compizconfig-settings-manager emerald
```
Then start up compiz and see if it works. If so, go ahead and import your profile again.

---

### Post by Karibbe on 2008-04-29
Thanks Zorael...it worked. I lost the wallpaper plugin (which I'll reinstall now), but I can now check the 3D plugin and it works.

---

### Post by cygnine on 2008-04-30
> **Zorael said:**
> From the ground up, then.

Export your profile in CCSM so you have it saved someplace. Go into Software Sources and make sure that you don't have any third-party repositories enabled. Then enter the following.
```
$ sudo aptitude update
$ sudo aptitude clean
$ sudo aptitude purge ~ncompiz ~nemerald ~nlibdeco ~nberyl
$ rm -r ~/.compiz     # gets rid of your compiz settings completely
$ sudo aptitude install compiz compizconfig-settings-manager emerald
```
Then start up compiz and see if it works. If so, go ahead and import your profile again.

This didn't work for me. I did exactly the above (I actually added simple-ccsm to the list of installed packages since otherwise there isn't even a `custom' option in System->Preferences->Appearance->Visual Effects. There's a comment about installing this package at [http://tombuntu.com/index.php/2008/03/27/custom-compiz-effects-in-ubuntu-804/]("http://tombuntu.com/index.php/2008/03/27/custom-compiz-effects-in-ubuntu-804/")). 

Anyway, it didn't work: if I try to select custom effects, it switches back to 'extra effects' upon closing and opening up the appearance menu. Any changes I make in preferences (the simple-ccsm package) don't save at all.

I can make changes in the advanced settings manager (the compizconfig-settings-manager package) to effects that **already are enabled**, but I cannot enable or disable any effects.

Anybody know how to fix this?

---

### Post by cygnine on 2008-05-01
Sorry for the double-post, but I think I fixed the problem: the compiz settings aren't in ~/.compiz like they were in Gutsy. Instead, they're now in ~/.config/compiz.

So doing the same steps as Zorael mentioned above, but removing ~/.config/compiz instead of ~/.compiz should do the trick. It worked for me, anyway.

---

### Post by dr_james2k on 2008-06-10
Yup, worked here in hardy with:

> $ sudo aptitude update
$ sudo aptitude clean
$ sudo aptitude purge ~ncompiz ~nemerald ~nlibdeco ~nberyl
$ rm -r ~/.config/compiz     # gets rid of your compiz settings completely
$ sudo aptitude install compiz compizconfig-settings-manager emerald

(except for the 3D plugin but I've gotten that working through CCSM preferences -> plugin list then by disabling "automatic plugin sorting" I can enable 3d there.

---

### Post by MrGrey1 on 2008-07-28
Strangely I had ~/.compiz and ~/.config/compiz on a clean install of Hardy? 

$ sudo aptitude update
$ sudo aptitude clean
$ sudo aptitude purge ~ncompiz ~nemerald ~nlibdeco ~nberyl
$ rm -r ~/.compiz     # gets rid of your compiz settings completely
$ rm -r ~/.config/compiz # both of them? just in case
$ sudo aptitude install compiz compizconfig-settings-manager emerald

then I also added fusion icon and set it to start on login by adding it to startup programs
$ sudo aptitude install fusion-icon
( [http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/](http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/) )

Now all working nicely!

---

### Post by Shazaam on 2008-07-28
> **MrGrey1 said:**
> Strangely I had ~/.compiz and ~/.config/compiz on a clean install of Hardy? 

$ sudo aptitude update
$ sudo aptitude clean
$ sudo aptitude purge ~ncompiz ~nemerald ~nlibdeco ~nberyl
$ rm -r ~/.compiz     # gets rid of your compiz settings completely
$ rm -r ~/.config/compiz # both of them? just in case
$ sudo aptitude install compiz compizconfig-settings-manager emerald

then I also added fusion icon and set it to start on login by adding it to startup programs
$ sudo aptitude install fusion-icon
( [http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/](http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/) )

Now all working nicely!

I had the same problem but I fixed it with only installing fusion-icon and setting it to start a boot. I didn't have to move/delete any files.
If you uninstall the repo version of compiz and reinstall from source (including ccsm and any plugins) the problem doesn't occur.

---

### Post by ram100987 on 2008-08-04
Whenever i try the command:

$ sudo aptitude purge ~ncompiz ~nemerald ~nlibdeco ~nberyl

It says that it could not find any of these packages...

---

### Post by MrGrey1 on 2008-08-06
> **ram100987 said:**
> Whenever i try the command:

$ sudo aptitude purge ~ncompiz ~nemerald ~nlibdeco ~nberyl

It says that it could not find any of these packages...

Just try continuing with the rest of the steps?

---

### Post by wallas on 2008-08-07
> **ram100987 said:**
> I don't see where to select custom effects... It offers none, normal, or extra.

That means you haven't installed compizconfig-settings-manager (ccsm). Look in the [The Great Desktop Effects FAQ of 2008]("http://ubuntuforums.org/showthread.php?t=809695") for more help. I've installed 3d effects in an inspiron 1420 with no problem.

:)

W.-

---

### Post by thawkins1 on 2008-08-08
I had that problem when I updated compiz but later there was another update for the ccsm and it fixed all the problems.

---

### Post by LeftNut on 2008-10-15
> **Zorael said:**
> From the ground up, then.

Export your profile in CCSM so you have it saved someplace. Go into Software Sources and make sure that you don't have any third-party repositories enabled. Then enter the following.
```
$ sudo aptitude update
$ sudo aptitude clean
$ sudo aptitude purge ~ncompiz ~nemerald ~nlibdeco ~nberyl
$ rm -r ~/.compiz     # gets rid of your compiz settings completely
$ sudo aptitude install compiz compizconfig-settings-manager emerald
```
Then start up compiz and see if it works. If so, go ahead and import your profile again.

after i tried this i still can't use any of the plugin's and now i cant even use atlantis which i had working. So if anyone could help to get this to work i would appreciate it alot.

Thank you for any input,
Gary

---

### Post by cptr13 on 2008-10-15
I had this issue after upgrading compiz.  A simple reboot resolved the problem.

---

### Post by borlosky on 2008-11-12
i had similar issues with options unchecking them selves, what i did to resolve for good, was to completely remove all compiz related software, from both add/remove software, and from synaptic as well. then i installed compiz from git, and EVERYTHING works fine now.

---

