---
title: "beryl 0.1.3"
date: 2006-12-10
forum: General Help
---

### Post by Naegling23 on 2006-12-10
So, beryl 0.1.3 was released today, any idea when it will be hitting the repro's?  
[URL="http://blog.beryl-project.org/?p=9"]
http://blog.beryl-project.org/?p=9[/URL]

also it says that it includes the kde window decorator, does this mean my kde themes will work in beryl, or just that there will be some kde styled themes for beryl....im so confused.

---

### Post by OffHand on 2006-12-10
It's already there  ;)

Edit: Oops sorry, I am running Beryl svn. I think it will take some time before it makes it to the official repos.

---

### Post by Azakus on 2006-12-10
Check every couple of minutes or so. That's what the Beryl people said to do, as the repos are in the middle of updating.

---

### Post by HighD on 2006-12-10
> **Naegling23 said:**
> So, beryl 0.1.3 was released today, any idea when it will be hitting the repro's?

[http://www.ubuntuforums.org/showthread.php?t=263851&page=124&highlight=beryl](http://www.ubuntuforums.org/showthread.php?t=263851&page=124&highlight=beryl)

See what Pricey says

---

### Post by PriceChild on 2006-12-10
Yup, you'll have to wait for iXce to build the packages, and then for me and lupine to update our mirrors.

Takes some time :)

Pricey

---

### Post by testube_babies on 2006-12-10
See here for a 0.1.3 repo:

[http://download.tuxfamily.org/3v1deb/index.html](http://download.tuxfamily.org/3v1deb/index.html)

---

### Post by PriceChild on 2006-12-10
> **testube_babies said:**
> See here for a 0.1.3 repo:

[http://download.tuxfamily.org/3v1deb/index.html](http://download.tuxfamily.org/3v1deb/index.html)That's svn packages and won't be as stable as the 0.1.3 release.

I advise you all to wait until the repos are updated.

---

### Post by ronmarley1 on 2006-12-10
> **PriceChild said:**
> Yup, you'll have to wait for iXce to build the packages, and then for me and lupine to update our mirrors.

Takes some time :)

Pricey
Hi Pricey,
Thanks for all you do in this forum and with the  Beryl Project.  I thought I read somewhere that lupine's repo would not have 0.1.3.  Am I wrong?  Below are the repos I've used for Beryl in the past.  Could you please let me know which to use and which I can trash?  I just would like to clean up my sources list a bit.
Thanks in advance!
1.  deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
2.  #deb [http://ubuntu2.beryl-project.org](http://ubuntu2.beryl-project.org) edgy main
3.  #deb [http://beryl-mirror.lupine.me.uk](http://beryl-mirror.lupine.me.uk) edgy main
4.  #deb-src [http://beryl-mirror.lupine.me.uk](http://beryl-mirror.lupine.me.uk) edgy main
5.  #deb [http://ubuntu2.lupine.me.uk/](http://ubuntu2.lupine.me.uk/) edgy main

---

### Post by PriceChild on 2006-12-10
```
http://ubuntu.beryl-project.org/
```Is the official repository.

This points to a random one of the official ubuntu repositories currently available.

At the moment, the following repositories are available which the above will point to:
```
http://beryl.lupine.me.uk/
http://beryl-mirror.pricechild.co.uk/
```This means you can currently use either of the following lines in your sources list **for edgy**.```
deb http://ubuntu.beryl-project.org edgy main
deb http://beryl.lupine.me.uk edgy main
deb http://beryl-mirror.pricechild.co.uk edgy main
```Enjoy :)

---

### Post by HighD on 2006-12-10
Ok so I'm upgrading to beryl 0.1.3, now when I run apt-get update OR just hit RELOAD from synaptic the following message appears:

W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA

Is it a repo issue? Is it ok or not? As far as I understand I need this "key" in order to download from the repo, am I right? I'm sorry I'm kinda new to this. Thanks in advance for any help.

Strangely...i see my Ubuntu Update Manager showing the updates to Beryl 0.1.3....:rolleyes:

---

### Post by croppyboy on 2006-12-10
Yeah . . . I got the same error . . . but I upgraded with no problems so I am now running 0.1.3 

It is pretty cool . . . thanks for all the work getting this out . . .

---

### Post by Russty of Oz on 2006-12-10
I just tried an apt-get update and I got the following 

Failed to fetch [http://ubuntu2.beryl-project.org/dists/edgy/main/binary-i386/Packages.gz](http://ubuntu2.beryl-project.org/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://amaranth.selfip.com/dists/edgy/lrm/binary-i386/Packages.gz](http://amaranth.selfip.com/dists/edgy/lrm/binary-i386/Packages.gz)  404 Not Found


Is there something wrong in my sources.list?

---

### Post by jfinkels on 2006-12-10
My apt-get update isn't reflecting the update to 0.1.3 either.

EDIT: Update Manager just gave me the updates, said they're not authenticated though :P.

---

### Post by croppyboy on 2006-12-11
> **Russty of Oz said:**
> I just tried an apt-get update and I got the following 

Failed to fetch [http://ubuntu2.beryl-project.org/dists/edgy/main/binary-i386/Packages.gz](http://ubuntu2.beryl-project.org/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://amaranth.selfip.com/dists/edgy/lrm/binary-i386/Packages.gz](http://amaranth.selfip.com/dists/edgy/lrm/binary-i386/Packages.gz)  404 Not Found


Is there something wrong in my sources.list?

I got this error message as well . . . in my sources.list I had 

```
deb http://ubuntu.beryl-project.org main edgy
```

I changed it to . . .

```
deb http://ubuntu.beryl-project.org edgy main
```

and it worked . . .

---

### Post by Russty of Oz on 2006-12-11
Mine does say edgy main, so I removed the 2 after ubuntu and now that one doesn't show as 404 but the other one still does :confused: 

I have done an apt-get update but still only have beryl 0.1.2

SIGH! :(

---

### Post by igknighted on 2006-12-11
apt-get update refreshes the list, try apt-get upgrade

---

### Post by croppyboy on 2006-12-11
What are you using [http://amaranth.selfip.com/](http://amaranth.selfip.com/) for?

I had been using them for the nvidia drivers but I think the site is closed . . .

Here is where I get my nvidia drivers from now . . .

```
## nvidia drivers
deb http://albertomilone.com/drivers/unstable/edgy/32bit binary/
```

---

### Post by Azakus on 2006-12-11
I got everything going by replacing the ubuntu.beryl-project.org link with one of the mirrors. Now my problem is that beryl-settings is seg faulting. How do I fix that?

---

### Post by hadiriazi on 2006-12-11
ok guys help me out here??

What do I do exactly to upgrade to 0.1.3 ??

---

### Post by croppyboy on 2006-12-11
> **hadiriazi said:**
> ok guys help me out here??

What do I do exactly to upgrade to 0.1.3 ??

I just added the following to my /etc/apt/sources.list

```
## beryl and emerald repo 
deb http://ubuntu.beryl-project.org edgy main
```

started Synaptic and hit **reload** . . . **mark all upgrades** . . . and all of the packages for beryl 0.1.3 appeared in the lis of upgrades . . .

---

### Post by Rodneyck on 2006-12-11
I tried this and it updated all but one packet that got an error. So now, when I hit the update button, it says, "You have 1 broken package on your system!

Use the "Broken" filter to locate it."

What is the Broken filter and where is it?

*edit: Nevermind, I just reinstalled everything through synaptic and it worked.

---

### Post by hadiriazi on 2006-12-11
> **croppyboy said:**
> I just added the following to my /etc/apt/sources.list

```
## beryl and emerald repo 
deb http://ubuntu.beryl-project.org edgy main
```

started Synaptic and hit **reload** . . . **mark all upgrades** . . . and all of the packages for beryl 0.1.3 appeared in the lis of upgrades . . .
thanks croppyboy i did what you told me, how do I see the changes?
Do I need to reboot?

---

### Post by joergenlie on 2006-12-11
Looks nice! one problem though. Beryl settings manager seems to be broken. I can't open it. I have rebooted but no luck. Anyone else with this experience?

Jørgen

---

### Post by croppyboy on 2006-12-11
I haven't had any problems with the manager . . . or any other aspect  of 0.1.3 . . . yet

---

### Post by Rodneyck on 2006-12-11
Me either. 

I must say, "wow", some nice changes/plugins. The developers are really doing some wonderful things with Beryl.

---

### Post by Russty of Oz on 2006-12-11
> **croppyboy said:**
> What are you using [http://amaranth.selfip.com/](http://amaranth.selfip.com/) for?

I had been using them for the nvidia drivers but I think the site is closed . . .

Here is where I get my nvidia drivers from now . . .

```
## nvidia drivers
deb http://albertomilone.com/drivers/unstable/edgy/32bit binary/
```

I didn't know it had changed.  How do we know when these things change?

Well I have changed it now.  Thanks!

---

### Post by hadiriazi on 2006-12-11
beryl 0.1.3 up and running :D

Only one thing where are the other window decorators and how could I get more themes for them?

---

### Post by Russty of Oz on 2006-12-11
OK!  I have got 0.1.3 running now.  

GREAT!:D

I have noticed that now the package manager wants to uninstall nvidia-glx ??  

Why does it want to do this?  I remember that it did this on 2 previous occasions and after that I couldn't get anything to work after rebooting.  I have told it not to remove it but it still shows up as an update.

---

### Post by raveneffct on 2006-12-11
> **Russty of Oz said:**
> OK!  I have got 0.1.3 running now.  

GREAT!:D

Does anyone know how much system resources Beryl takes up?

---

### Post by mcduck on 2006-12-11
> **raveneffct said:**
> Does anyone know how much system resources Beryl takes up?

there's no single answer to that question. It depends on what plugins you are using. With only some simple ones like the cube it's using 1-2% CPU on my laptop, and with all bells and whistles it can jump very high during some animations.

---

### Post by Azakus on 2006-12-11
It looks like Beryl-Settings has not been updated to 0.1.3, which is why it's seg faulting. Great.

---

### Post by joergenlie on 2006-12-11
> **Azakus said:**
> It looks like Beryl-Settings has not been updated to 0.1.3, which is why it's seg faulting. Great.

Right. It has to be the problem. Anyone knows why beryl-settings hasn't been upgraded? If the package isn't upgradable, is there another solution to the problem? Things works fine, but it's nice to be able to change the settings.:-D 

Jørgen

---

### Post by ronmarley1 on 2006-12-11
> **PriceChild said:**
> ```
http://ubuntu.beryl-project.org/
```Is the official repository.

This points to a random one of the official ubuntu repositories currently available.

At the moment, the following repositories are available which the above will point to:
```
http://beryl.lupine.me.uk/
http://beryl-mirror.pricechild.co.uk/
```This means you can currently use either of the following lines in your sources list **for edgy**.```
deb http://ubuntu.beryl-project.org edgy main
deb http://beryl.lupine.me.uk edgy main
deb http://beryl-mirror.pricechild.co.uk edgy main
```Enjoy :)

Thank you, sir.  0.1.3 installed and running.  It's a 3D world!

---

### Post by thread on 2006-12-11
I'm guessing I need that beryl-settings manager in order to enable the new effects... I'll be eagerly awaiting a fix to this one.

---

### Post by AusIV4 on 2006-12-11
> **PriceChild said:**
> 
This means you can currently use either of the following lines in your sources list **for edgy**.
Any word on a dapper release of 0.1.3? Beryl is awesome, but every once in a while it loads without the window decorations.

---

### Post by 16777216 on 2006-12-11
All of the repos seem to be down.:-k](*,)[-(

---

### Post by PriceChild on 2006-12-11
Ok, I just woke up to find a nice little tarball for my mirror. I've just finished editing it for my server and its uploading now.

There is a new key... "root@lupine.me.uk.gpg" instead of "1609B551.gpg"

Enjoy.

---

### Post by croppyboy on 2006-12-11
> **Azakus said:**
> It looks like Beryl-Settings has not been updated to 0.1.3, which is why it's seg faulting. Great.

Mine updated with no problems . . . 

There was an emerald package that didn't upgrade so I just killed emerald and re-ran Synaptic and it updated that package . . .

You might want to try killing beryl-manager and then try to update/upgrade beryl-settings . . .

---

### Post by Rodneyck on 2006-12-11
> **croppyboy said:**
> Mine updated with no problems . . . 

There was an emerald package that didn't upgrade so I just killed emerald and re-ran Synaptic and it updated that package . . .

You might want to try killing beryl-manager and then try to update/upgrade beryl-settings . . .

Same here...

---

### Post by PriceChild on 2006-12-11
Ok both mirrors are updated.

Please go to here: [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851) and check that you have the correct repositories, and install the new key.

Pricey

---

### Post by OffHand on 2006-12-11
A little bit off topic but does anyones 3d world plugin work?

---

### Post by HighD on 2006-12-11
> **OffHand said:**
> A little bit off topic but does anyones 3d world plugin work?

Mine does! Looks great by the way, doesn't yours?

---

### Post by 23meg on 2006-12-11
> does anyones 3d world plugin work?Working here.

---

### Post by deep.tinker77 on 2006-12-11
> **HighD said:**
> Mine does! Looks great by the way, doesn't yours?

If you are going to reply, try to help and don't act like like a little child by trying to be funny [-(

---

### Post by thread on 2006-12-11
beryl-settings is still at 0.1.2-0ubuntu2 for my AMD64 install...

---

### Post by AdamDunn on 2006-12-11
Comparing the listings at
[http://beryl.lupine.me.uk/dists/edgy/main/]("http://beryl.lupine.me.uk/dists/edgy/main/")
and
[http://beryl-mirror.pricechild.co.uk/dists/edgy/main/]("http://beryl-mirror.pricechild.co.uk/dists/edgy/main/")
it looks like Pricechild's mirror does not have the beryl-settings_0.1.3~0beryl1_amd64.deb package, which is probably the cause of some AMD64 users (myself included) not getting beryl-settings_0.1.3, and being held back to 0.1.2. I'm going to try changing my repository from the general ubuntu.beryl-project.org over to lupine's.

Edit: that seems to have worked wonderfully. Until Pricechild's mirror gets the missing package, AMD64 users will want to specify Lupine's mirror.

---

### Post by HighD on 2006-12-11
> **deep.tinker77 said:**
> If you are going to reply, try to help and don't act like like a little child by trying to be funny [-(

Hey, I'm just happy mine works, and IT IS reason for me to act like a little child, I just think this whole beryl thing is pretty neat. I asked OffHand if his or her plugin worked so maybe he o she'd explain a little about his or her situation so then I could help.

---

### Post by PriceChild on 2006-12-11
> **AdamDunn said:**
> Comparing the listings at
[http://beryl.lupine.me.uk/dists/edgy/main/](http://beryl.lupine.me.uk/dists/edgy/main/)
and
[http://beryl-mirror.pricechild.co.uk/dists/edgy/main/](http://beryl-mirror.pricechild.co.uk/dists/edgy/main/)
it looks like Pricechild's mirror does not have the beryl-settings_0.1.3~0beryl1_amd64.deb package, which is probably the cause of some AMD64 users (myself included) not getting beryl-settings_0.1.3, and being held back to 0.1.2. I'm going to try changing my repository from the general ubuntu.beryl-project.org over to lupine's.

Edit: that seems to have worked wonderfully. Until Pricechild's mirror gets the missing package, AMD64 users will want to specify Lupine's mirror.Just checked and mine seems to be there... Could you check?

---

### Post by PriceChild on 2006-12-11
> **deep.tinker77 said:**
> If you are going to reply, try to help and don't act like like a little child by trying to be funny [-(

> **HighD said:**
> Hey, I'm just happy mine works, and IT IS reason for me to act like a little child, I just think this whole beryl thing is pretty neat. I asked OffHand if his or her plugin worked so maybe he o she'd explain a little about his or her situation so then I could help.Calm down, stop being so silly.

---

### Post by deep.tinker77 on 2006-12-11
> **HighD said:**
> Hey, I'm just happy mine works, and IT IS reason for me to act like a little child, I just think this whole beryl thing is pretty neat. I asked OffHand if his or her plugin worked so maybe he o she'd explain a little about his or her situation so then I could help.

Ok, sorry then, I thought you were trying to be mean. I'm happy mine is working also, just trying to figure how to get the snow :D

---

### Post by HighD on 2006-12-11
> **deep.tinker77 said:**
> Ok, sorry then, I thought you were trying to be mean. I'm happy mine is working also, just trying to figure how to get the snow :D

That's fine :mrgreen: Let's all just get along. Snow?:confused: I saw the effect on an earlier post by PriceChild, is it available on 0.1.3?

---

### Post by Hurons on 2006-12-11
Maybe someone can help me.

When I try to open settings manger nothing happens.With that said, I opened beryl- settings  in the terminal and got this error:

 beryl-settings
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libdbus.so' plugin


Anu ideas how to make this go away so I can open settings manger?

Thank You

---

### Post by lupine_nickt on 2006-12-11
Hi people,

Sorry about the somewhat, ahem, bumpy repository update... completely my fault. I just plain forgot to build beryl-settings 0.1.3 for amd64! So, of course, it wasn't in the tarball I sent to pricechild... ooops. 

My mirror now has it - it's at [http://beryl.lupine.me.uk/pool/edgy/main/beryl-settings/beryl-settings_0.1.3~0beryl1_amd64.deb](http://beryl.lupine.me.uk/pool/edgy/main/beryl-settings/beryl-settings_0.1.3~0beryl1_amd64.deb) :). But just using the repo as usual should work fine.

I've sent a new tarball and a nudge to PriceChild, so hopefully he'll be good enough to fix my mistake for me... :s

0.1.4 /will/ be smoother. I promise :)

Regarding libdbus.so - make sure beryl-dbus is installed. 0.1.3 /is/ in the repo, for amd64 and i386 :). However, it's not a fatal error so won't stop beryl-settings from starting. And nobody really uses dbus for anything, anyway...

Oh, and to clarify the situation w/rt the repos... ubuntu.beryl-project.org is the /only/ URL you should be using. Unless I break stuff again, anyway! 
beryl.lupine.me.uk is me, beryl-mirror.pricechild.co.uk is Pricechild. ubuntu.beryl-project.org gets you to choose one or the other randomly. 

If anyone else has oodles of space bandwidth, they can volunteer to be a mirror as well. As a rough guide, I get hit for ~8GB/day. 

Also... if anyone has a ppc-architecture machine and wants to build packages (it's mostly really easy, don't worry :) ), then I could add that architecture to the repo as well...

xF,

...Nick

---

### Post by Hurons on 2006-12-11
> **lupine_nickt said:**
> Hi people,

Sorry about the somewhat, ahem, bumpy repository update... completely my fault. I just plain forgot to build beryl-settings 0.1.3 for amd64! So, of course, it wasn't in the tarball I sent to pricechild... ooops. 

My mirror now has it - it's at [http://beryl.lupine.me.uk/pool/edgy/main/beryl-settings/beryl-settings_0.1.3~0beryl1_amd64.deb](http://beryl.lupine.me.uk/pool/edgy/main/beryl-settings/beryl-settings_0.1.3~0beryl1_amd64.deb) :). But just using the repo as usual should work fine.

I've sent a new tarball and a nudge to PriceChild, so hopefully he'll be good enough to fix my mistake for me... :s

0.1.4 /will/ be smoother. I promise :)

Regarding libdbus.so - make sure beryl-dbus is installed. 0.1.3 /is/ in the repo, for amd64 and i386 :). However, it's not a fatal error so won't stop beryl-settings from starting. And nobody really uses dbus for anything, anyway...

Oh, and to clarify the situation w/rt the repos... ubuntu.beryl-project.org is the /only/ URL you should be using. Unless I break stuff again, anyway! 
beryl.lupine.me.uk is me, beryl-mirror.pricechild.co.uk is Pricechild. ubuntu.beryl-project.org gets you to choose one or the other randomly. 

If anyone else has oodles of space bandwidth, they can volunteer to be a mirror as well. As a rough guide, I get hit for ~8GB/day. 

Also... if anyone has a ppc-architecture machine and wants to build packages (it's mostly really easy, don't worry :) ), then I could add that architecture to the repo as well...

xF,

...Nick


Thanks for all your work. Any idea why I cant open settings manger? agin here is the error:
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libdbus.so' plugin
Segmentation fault (core dumped)

its driving my bonkers.

---

### Post by deep.tinker77 on 2006-12-11
> **lupine_nickt said:**
> Hi people,

Sorry about the somewhat, ahem, bumpy repository update... completely my fault. I just plain forgot to build beryl-settings 0.1.3 for amd64! So, of course, it wasn't in the tarball I sent to pricechild... ooops. 

My mirror now has it - it's at [http://beryl.lupine.me.uk/pool/edgy/main/beryl-settings/beryl-settings_0.1.3~0beryl1_amd64.deb](http://beryl.lupine.me.uk/pool/edgy/main/beryl-settings/beryl-settings_0.1.3~0beryl1_amd64.deb) :). But just using the repo as usual should work fine.

I've sent a new tarball and a nudge to PriceChild, so hopefully he'll be good enough to fix my mistake for me... :s

0.1.4 /will/ be smoother. I promise :)

Regarding libdbus.so - make sure beryl-dbus is installed. 0.1.3 /is/ in the repo, for amd64 and i386 :). However, it's not a fatal error so won't stop beryl-settings from starting. And nobody really uses dbus for anything, anyway...

Oh, and to clarify the situation w/rt the repos... ubuntu.beryl-project.org is the /only/ URL you should be using. Unless I break stuff again, anyway! 
beryl.lupine.me.uk is me, beryl-mirror.pricechild.co.uk is Pricechild. ubuntu.beryl-project.org gets you to choose one or the other randomly. 

If anyone else has oodles of space bandwidth, they can volunteer to be a mirror as well. As a rough guide, I get hit for ~8GB/day. 

Also... if anyone has a ppc-architecture machine and wants to build packages (it's mostly really easy, don't worry :) ), then I could add that architecture to the repo as well...

xF,

...Nick

No worries man, we all appreciate you and PriceChild for all of your work getting the update out to everyone:D Thanks to you two, I've got the prettiest laptop in Baghdad, now only if I can get the snow, lol

---

### Post by joergenlie on 2006-12-11
I had problem with beryl-settings manager because of upgrade problems, but killall beryl-manager, apt-update, apt-upgrade solved it.

Jørgen

---

### Post by PriceChild on 2006-12-11
I'm just updating my repository now.

We'll have 2 perfect mirrors for you in roughly 5 minutes :)

Pricey

---

### Post by gotgenes on 2006-12-11
libemeraldengine0 has some choking when trying to be installed during the upgrade
```
Errors were encountered while processing:
 /var/cache/apt/archives/libemeraldengine0_0.1.3~0beryl1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
This is resolved by repeating an apt-get installation of the package libemeraldengine0, after which beryl-manager, emerald-themes, and beryl will finish installation.

---

### Post by Isntitknoying on 2006-12-11
Guys, I'm running edgy with an ATI X1300pro AGP, fglrx driver, and XGL. Beryl  0.1.1 worked beautifully, but with 0.1.2 or 0.1.3 I get a segmentation fault when trying to run beryl-xgl. Beryl manager starts, but the window decorator section is greyed out, and trying to do an emerald --replace also throws an error. 
Does anyone have any idea what's going on? I've checked and re-checked the packages, they seem to all have updated, have purged and removed everything and reinstalled, with the same result. 
I am completely taken with Beryl, it's fantastic, but I'd hate to be stuck at 0.1.1 (for as long as I can still get a hold of those packages.)

---

### Post by AusIV4 on 2006-12-11
Can we be expecting a Dapper backport, or am I stuck on 0.1.1?

---

### Post by PriceChild on 2006-12-12
> **AusIV4 said:**
> Can we be expecting a Dapper backport, or am I stuck on 0.1.1?There are Dapper packages about.

However Dapper is not officially supported by Beryl.

---

### Post by ayoli on 2006-12-12
> **gotgenes said:**
> libemeraldengine0 has some choking when trying to be installed during the upgrade
```
Errors were encountered while processing:
 /var/cache/apt/archives/libemeraldengine0_0.1.3~0beryl1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
This is resolved by repeating an apt-get installation of the package libemeraldengine0, after which beryl-manager, emerald-themes, and beryl will finish installation.

had the same error, but fixed with a sudo apt-get -f install
thanks for the work pricechild :)
0.1.3 seems faster on my laptop, yay !

---

### Post by AusIV4 on 2006-12-12
> **PriceChild said:**
> There are Dapper packages about.

However Dapper is not officially supported by Beryl.

I decided to upgrade my laptop to Edgy. Upgrading my server to Edgy was a nightmare, and I decided to revert to Dapper. My laptop, however, doesn't use RAID or LVM, and could probably benefit more from the upgrade.

---

