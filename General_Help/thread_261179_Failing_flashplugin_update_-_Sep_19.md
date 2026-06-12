---
title: "Failing flashplugin update - Sep 19"
date: 2006-09-19
forum: General Help
---

### Post by kpkeerthi on 2006-09-19
```

Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_7.0.68~ubuntu1~dapper1_i386.deb) ...
Setting up flashplugin-nonfree (7.0.68~ubuntu1~dapper1) ...
Downloading...  done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.

```

Anyone else having this problem? Multiple attempts to reinstall the package  fails with same error. Can someone help me fix this? Thanks.

---

### Post by glennric on 2006-09-19
I seem to be having the same problem.  Although flash still seems to be working.  The annoying thing is that anytime I try to install anything via apt-get it trys to reinstall and configure the flashplugin.

---

### Post by Jessehk on 2006-09-19
Same problem here. Maybe the download site is down?

---

### Post by glennric on 2006-09-19
> **Jessehk said:**
> Same problem here. Maybe the download site is down?

I don't think the site is down as it seems to download.  It seems to be a problem with the post-installation script.

---

### Post by moreinfo on 2006-09-19
I have a similar problem,

Not sure how to copy it out of terminal to show you though.

E: flashplugin-nonfree: subprocess post-installation script returned error exit status 1

It just didn't update.
Can't find anything wrong yet though.

---

### Post by Luis Marks on 2006-09-19
Same problem here.

---

### Post by swp6499 on 2006-09-19
i have the same problem...help???

---

### Post by kpkeerthi on 2006-09-19
Hmm... pretty disappointing that many have this problem. Lets hope the devs address this issue.

---

### Post by compuguy1088 on 2006-09-20
Yep, I just noticed this as well, and it has the same error, I hope they fix it as well...

---

### Post by Paul41 on 2006-09-20
I am having the same problem. Initially the problem was that I just couldn't update, but then I made some changes to Firefox and need to reinstall the plug in.  It won't let me reinstall either so no I just don't have the flash player.

---

### Post by youspeakmylanguage on 2006-09-20
Same problem here. :mad:

Ubuntu 6.06 LTS, GNOME, Firefox, x86 PC (former Wintel).

---

### Post by JoseStefan on 2006-09-20
same problem:

[http://paste.ubuntu-nl.org/24056](http://paste.ubuntu-nl.org/24056)

I filed bug [https://launchpad.net/bugs/61354](https://launchpad.net/bugs/61354)
and linked to this thread.

---

### Post by web250 on 2006-09-20
I also have this problem

---

### Post by SpanishFranks on 2006-09-20
Yep, same probs here. I presume from the amount of people replying to this thread that every 6.06 user trying to grab flashplugin-nonfree will have this problem

---

### Post by JoseStefan on 2006-09-20
Temporary Fixes:

A) Don't install the update.

B) If flash is still working. Just leave it alone for the time being. Until they fix the package.

C) If you accidently decided to remove the package and now cant install it at all. Leaving you without flash. Try one of the following

* sudo apt-get install flashplugin-nonfree/dapper
 (to install the version initially released with dapper)

* sudo apt-get install flashplugin-nonfree=VERSION
 (VERSION should be available from the repositories
 or in your apt-cache)

---

My Bug was a duplicate of:
[https://launchpad.net/bugs/61349](https://launchpad.net/bugs/61349)
(guess we were writing at the same time, numbers are close)

---

### Post by ThrobbingBrain66 on 2006-09-20
i had (have) the same problem, so I downloaded flash from adobe's site and installed it.  it shows in synaptic and firefox as the latest version, but I still get the same error as everyone else. weird...

---

### Post by binapower on 2006-09-20
Same problem here and here's how I solved.

There's a message saying that the post-instalation script failed. I just edited this script and had the aptitude upgrade and everything worked just fine.

The file I edited is at...
/var/lib/dpkg/info/flashplugin-nonfree.postinst

change the line 35, for this one
update-rc.d flashplugin-nonfree defaults >/dev/null

after that "aptitude upgrade" should work

--

Edson Vinicius Schmitt

---

### Post by JoseStefan on 2006-09-20
I would like to point out that the broken package is in:
 dapper-backports

The only other version of flashplugin-nonfree in the repos is the one from dapper's release day, located on repository:
 dapper

SOLUTION:
Removing the package, and installing with "/dapper" like stated on my previous thread would be the Cleanest solution.

OR you can attempt to 'fix' the backport and install it, like stated by other users.

**EDIT:**
This is an alternate way of doing what binapower said,
After the dapper-backports update fails do:

```

sudo sed -e 's/multiuser/defaults/' -i /var/lib/dpkg/info/flashplugin-nonfree.postinst
sudo dpkg --configure -a

```

---

### Post by DC@DR on 2006-09-20
Damn, I got it work finally, thanks to binapower and JoseStefan. You guys rock! :). Just a bit annoyed about the issue since it seems to happen to alot of people...Hasn't the upgrade package been tested properly before rolled out?? :(

---

### Post by jeremy on 2006-09-20
Thank you Binapower for the fix!

---

### Post by zakame on 2006-09-20
I have reported this to the Launchpad as [https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/61349]("https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/61349") .   It looks like it used Edgy's version of `update-rc.d' (despite the backport,) hence the minor borkage.

---

### Post by ahaslam on 2006-09-20
I'll have to try out that fix later if an official fix isn't released in the meantime. I'm a bit disappointed with the updates at the moment, things often go wrong here :(

Cheers.

---

### Post by Polygon on 2006-09-20
yep, same problem

---

### Post by tribunal on 2006-09-20
And here
Real mass problem :(
Next time I will wait 2-3 days before updating anything

---

### Post by missmoondog on 2006-09-20
yep, just came across the same error right now also. :(

---

### Post by Ramses de Norre on 2006-09-20
Thanks for the fix dude ;)

---

### Post by TheRingmaster on 2006-09-20
What is the absolute best way to fix this (most official way) so when there is another update i'll be ready to go.

---

### Post by deweese on 2006-09-20
The flash update is causing an error on two different computers I have the exact same way so I know it is a problem with the software.  It needs fixing.

---

### Post by MJSOnline on 2006-09-20
Which repositorsy is it in?  Is there a 2nd repository that we can use that works? M

---

### Post by TheRingmaster on 2006-09-20
> **MJSOnline said:**
> Which repositorsy is it in?  Is there a 2nd repository that we can use that works? M
If you read earlier in this thread it says ubuntu-backports

---

### Post by Ramses de Norre on 2006-09-20
I think the fix opposed in this thread wont harm new updates at all.

---

### Post by MJSOnline on 2006-09-20
> **Ramses de Norre said:**
> I think the fix opposed in this thread wont harm new updates at all.

How do you mean? M

---

### Post by Ramses de Norre on 2006-09-20
Well someone asked for the best fix so it wont harm future upgrades of the package. And I'm pretty sure the fix from this thread wont afect upgrades in any way.
You just change one option in a command that seems to give trouble..

---

### Post by MJSOnline on 2006-09-20
> **Ramses de Norre said:**
> Well someone asked for the best fix so it wont harm future upgrades of the package. And I'm pretty sure the fix from this thread wont afect upgrades in any way.
You just change one option in a command that seems to give trouble..
I see. So if I wait now until the new update is ready, by keeping my eye on this site and my update icon, I shouldnt need to istall flash yet? M

---

### Post by PiTT on 2006-09-20
same problem here...

---

### Post by 89c51 on 2006-09-20
it gave me an error (exiting with -1 or something) during the instalation but seems to work fine

---

### Post by MJSOnline on 2006-09-20
> **89c51 said:**
> it gave me an error (exiting with -1 or something) during the instalation but seems to work fine

What?  Are you sure?  See if it works at [wwe]("http://www.wwe.com") for me. Thanks. M

---

### Post by maddbaron on 2006-09-20
adept says installed but yahoo tv and wwe dont work. I am using opera everything works in opera even though firefox is my preferred. I dont get it? anyway to use wine to install flash player 9?

---

### Post by MJSOnline on 2006-09-20
> **maddbaron said:**
> adept says installed but yahoo tv and wwe dont work. I am using opera everything works in opera even though firefox is my preferred. I dont get it? anyway to use wine to install flash player 9?

Hm, very very odd. I do hope they fix it soon. M

---

### Post by missmoondog on 2006-09-20
> **MJSOnline said:**
> What?  Are you sure?  See if it works at [wwe]("http://www.wwe.com") for me. Thanks. M


"it gave me an error (exiting with -1 or something) during the instalation but seems to work fine"

i get the same exact error and yes, that site still works.

---

### Post by maddbaron on 2006-09-20
this latest update screwed up my firefox! i cant open gmail now....whenever i try it crashes the browser...ok whenever i try to go to anything with flash script it crashes....this update messed me up..anyway to rollback to the previous one?

---

### Post by PriceChild on 2006-09-20
> **maddbaron said:**
> this latest update screwed up my firefox! i cant open gmail now....whenever i try it crashes the browser...ok whenever i try to go to anything with flash script it crashes....this update messed me up..anyway to rollback to the previous one?

Sorry, but you've got a different problem. Works fine for me :)

btw gmail doesn't use "flash script".... i don't quite know what that is?

You may be thinking of javasript?

---

### Post by raffytaffy on 2006-09-20
i went to the website and grabbed the flash player from them directly. i depend on it..and cant be bothered trying to figure out what went wrong:P hope it gets fixed soon. ```
http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux
```

---

### Post by maddbaron on 2006-09-20
> **PriceChild said:**
> Sorry, but you've got a different problem. Works fine for me :)

btw gmail doesn't use "flash script".... i don't quite know what that is?

You may be thinking of javasript?


yeah the new flash install conflicts with my flashblock and noscript extensions so i had to whitelist youtube and mail.google.com and that stopped the crashing. something in gmail was crashing it before i enabled it in flashblock so it uses some form of flash.

now i need to get yahoo tv and wwe to work, they keep saying i need the newest flash or flash 8....

---

### Post by Jucato on 2006-09-20
Bug report here: [https://launchpad.net/products/dapper-backports/+bug/61404](https://launchpad.net/products/dapper-backports/+bug/61404) (with 8 duplicates)

Most "official" workaround is what JoseStefan already mentioned:

```
sudo apt-get install flashplugin-nonfree/dapper
```

Got it from jdong (John Dong in the bug report).

---

### Post by 89c51 on 2006-09-20
> **MJSOnline said:**
> What?  Are you sure?  See if it works at [wwe]("http://www.wwe.com") for me. Thanks. M

yes i tested it with many sites (including wwe) and works

---

### Post by JoseStefan on 2006-09-20
It is the cleanest, and will remove the apt issue.
But it won't make flash work :(

It seems macromedia/adobe has removed the needed files from their server. Which makes the pkg on the 'dapper' repo useless.

This command will fail: (which is needed by the install script)
sudo update-flashplugin

I believe this calls for a 'dapper-updates' version. As anyone with a fresh install of Ubuntu 6.06.1 LTS will not be able to install flashplugin-nonfree.

---

### Post by wwuster on 2006-09-20
I also have the problem.

What is going wrong with the testing of updates lately? I was hoping that Ubuntu would not let this happen so that it could win over windows users.

William

---

### Post by PriceChild on 2006-09-20
> **wwuster said:**
> I also have the problem.

What is going wrong with the testing of updates lately? I was hoping that Ubuntu would not let this happen so that it could win over windows users.

William

As posted earlier... its not actually ubuntu's fault, its that macromedia made an update, we linked to it, then they removed it.
I think :)

---

### Post by EyeBun2 on 2006-09-20
Count me in too. I received the same error as post #1.

---

### Post by wwuster on 2006-09-20
> **PriceChild said:**
> As posted earlier... its not actually ubuntu's fault, its that macromedia made an update, we linked to it, then they removed it.
I think :)

Yes but the install or postinstall script should check for this and say "It is macromedia's fault" instead of just failing.

---

### Post by petchgoodguy on 2006-09-20
i have the same problem in post#1 thx in advance :(

---

### Post by hyperactivething on 2006-09-20
Worked like a charm.

Many thanks :D

---

### Post by ajgreeny on 2006-09-20
If you get a problem with flash missing from your system after this cock-up, you can force the version back to the original *7.0.63.3ubuntu3* using synaptic and then wait for the problem to be sorted  by Adobe, or whoever it is went a bit wrong.

---

### Post by rwabel on 2006-09-20
works again now with the fix! thanks a lot

---

### Post by pestie on 2006-09-20
Nobody else seems to have mentioned this, so I will. The new flashplayer-nonfree package claims it conflicts with xfs (the X font server, not the filesystem). It claims a conflict with xfs < 1:1.0.1-5, but the version in Dapper is 1:1.0.1-0ubuntu2. I actually use XFS for remote font serving, so I'd really hate for it to be forcibly uninstalled with no alternative. Of course, the same could be said for Flash, too. In any case, I've contacted the flashplugin-nonfree package maintainer about this.

---

### Post by mycelo on 2006-09-20
Same here.
Yet another broken update. :mad:

mycelo

---

### Post by PathSpace on 2006-09-20
Is the alleged "fix" to do this:

```
sudo apt-get install flashplugin-nonfree/dapper
```

Because I did that and now my flash is completely broken.  ](*,)

---

### Post by anodizer on 2006-09-20
> **PathSpace said:**
> Is the alleged "fix" to do this:

```
sudo apt-get install flashplugin-nonfree/dapper
```

Because I did that and now my flash is completely broken.  ](*,)

This isn't a fix, there is still a flash upgrade and practically you can't use synaptic.

---

### Post by maniacmusician on 2006-09-20
didn't someone say this was from backports?

the ubunutu devs can't be held responsible for what you download from backports, you enable that repository at your own risk. 

thanks to everyone who posted a fix or at least a solution.

---

### Post by avelldiroll on 2006-09-21
Pibcak

---

### Post by Limulus on 2006-09-21
Looks like there's a working package in the archives, but its not downloading via Synaptic just yet.  Gdebi will install it just fine though :)

[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.68~ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.68~ubuntu2_i386.deb)

Be sure to click the Terminal arrow so you can agree to the EULA.  It installed great on my system and [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) confirms that its the latest Linux version (7.0.68.0 :)

---

### Post by everdred on 2006-09-21
> **Limulus said:**
> Looks like there's a working package in the archives, but its not downloading via Synaptic just yet.  Gdebi will install it just fine though :)

[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.68~ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.68~ubuntu2_i386.deb)

Be sure to click the Terminal arrow so you can agree to the EULA.  It installed great on my system and [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) confirms that its the latest Linux version (7.0.68.0 :)
Thanks, Limulus!

---

### Post by ahaslam on 2006-09-21
> **Limulus said:**
> Looks like there's a working package in the archives, but its not downloading via Synaptic just yet.  Gdebi will install it just fine though :)

[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.68~ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.68~ubuntu2_i386.deb)

Be sure to click the Terminal arrow so you can agree to the EULA.  It installed great on my system and [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) confirms that its the latest Linux version (7.0.68.0 :)

Thanks, works great, sorts out the Synaptic prob ;)

Tony.

---

### Post by missmoondog on 2006-09-21
doesn't work for me. all i can do is force the previous version and that is only working in epiphany. can't get it to work in firefox or konqeror.

---

### Post by Limulus on 2006-09-21
> **missmoondog said:**
> doesn't work for me. all i can do is force the previous version and that is only working in epiphany. can't get it to work in firefox or konqeror.

~ubuntu2 that I linked isn't working for you?  Maybe try completely uninstalling the current version first?

---

### Post by anodizer on 2006-09-21
> **missmoondog said:**
> doesn't work for me. all i can do is force the previous version and that is only working in epiphany. can't get it to work in firefox or konqeror.

Install it from the terminal with "sudo dpkg -i".

---

### Post by Average Joe on 2006-09-21
Man, I thought I was going bananas! I was playing around I little with the flash plugin stuff, and I couldn't get it right anymore. I look on this forum and it turns out it is a general problem!

Now I just commented out the backport repositories in sources.list and reinstalled the flashplugin again. Problem solved.\\:D/

---

### Post by finferflu on 2006-09-21
Thanks a lot Limulus! I had the same issue, and you've solved it :D

---

### Post by Riverside on 2006-09-21
> **Average Joe said:**
> Now I just commented out the backport repositories in sources.list and reinstalled the flashplugin again. Problem solved.\\:D/
Except that this is a security update.  From SuSE's recent Security Announcement:

[INDENT]1) Problem Description and Brief Discussion

   Multiple input validation errors have been identified in the Macromedia
   Flash Player that could lead to the potential execution of arbitrary
   code.

   These vulnerabilities could be accessed through content delivered
   from a remote location via the user's web browser, email client,
   or other applications that include or reference the Flash
   Player. (CVE-2006-3311, CVE-2006-3587, CVE-2006-3588)

   These updates also include changes to prevent circumvention of the
   "allowScriptAccess" option. (CVE-2006-4640)
[/INDENT]
The Ubuntu upgrade process for this package still isn't working correctly, three days after the update was first released.

(I *know* that workarounds are possible as posted in this thread, however these should not be needed if Ubuntu hopes to position itself as a credible desktop alternative for mainstream deployment)

---

### Post by Average Joe on 2006-09-22
Thanks Riverside, I didn't know it was a security issue. In that case I will try Limulus' solution and install the plugin from:
[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.68~ubuntu2_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.68~ubuntu2_i386.deb")

Actually I don't like installing stuff from outside the repositories because of security and compatibility issues :).

But I think I will make an exeption this time. I hope the problem will be addressed by Ubuntu soon, though.

---

### Post by Riverside on 2006-09-22
> **Average Joe said:**
> But I think I will make an exeption this time. I hope the problem will be addressed by Ubuntu soon, though.
It still hasn't been, unfortunately.

---

### Post by missmoondog on 2006-09-22
> **anodizer said:**
> Install it from the terminal with "sudo dpkg -i".

yep, tried that. same thing.

---

### Post by missmoondog on 2006-09-22
> **Limulus said:**
> ~ubuntu2 that I linked isn't working for you?  Maybe try completely uninstalling the current version first?

i've uninstalled the current one so many times, it isn't funny anymore.

---

### Post by missmoondog on 2006-09-22
just tried installing the update through synaptic on another machine of mine. thought maybe it was fixed by now. NOT!!

---

### Post by Ramses de Norre on 2006-09-22
What error do you get with the new package from this thread?

---

### Post by Tuxman on 2006-09-22
I can't get it to work, I downloaded this:[http://archive.ubuntu.com/ubuntu/poo...untu2_i386.deb](http://archive.ubuntu.com/ubuntu/poo...untu2_i386.deb)

At the end it says > Downloading... ++++FAILED.
automatic installation failed due to network problems or upstream changes

I have tried different mirrors. And my internet is working perfect.

---

### Post by Average Joe on 2006-09-22
Tuxman, I hope you are not trying to download the exact link you posted. That one is broken, because it literly contains the dots (..). You could Limulus link instead, that I repeated in post #71. That one works.

I just tried it. Downloading is no problem, but when trying to install it I get:

```
(Reading database ... 102346 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 7.0.63.3ubuntu3 (using flashplugin-nonfree_7.0.68~ubuntu2_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (7.0.68~ubuntu2) ...
Downloading...  done.
installation failed
```

However, flash still works fine for me with Firefox. And after enabling the backport repositories, and updating the packages, it says there is nothing to update. So despite the error, everything fine, and I seem to have the latest packages.

Beats me, but I don't consider it a problem any longer.

---

### Post by missmoondog on 2006-09-22
that's the same situation i'm in on one of my pc's. flash only works in epiphany, for me though.

---

### Post by Limulus on 2006-09-22
> **Average Joe said:**
> Thanks Riverside, I didn't know it was a security issue. In that case I will try Limulus' solution and install the plugin from:
[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.68~ubuntu2_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.68~ubuntu2_i386.deb")

Actually I don't like installing stuff from outside the repositories because of security and compatibility issues :).

But I think I will make an exeption this time. I hope the problem will be addressed by Ubuntu soon, though.

;)  Actually, if you check the URL its to archive.ubuntu.com which *is* the official Ubuntu repositories, it just hadn't been indexed yet :)

However I see that ~ubuntu2~dapper1 is now available in Synaptic!  So if you've been having trouble with ~ubuntu2 try this newer version.

---

### Post by Limulus on 2006-09-22
> **Average Joe said:**
>  However, flash still works fine for me with Firefox. And after enabling the backport repositories, and updating the packages, it says there is nothing to update. So despite the error, everything fine, and I seem to have the latest packages. Beats me, but I don't consider it a problem any longer.

Could you check the installed version on [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) (under "Adobe Flash Player" mouseover "About")  if it says 7,0,68,0 then you're fine.  If its an older version then something went wrong :/

If you have an older version, uninstall flashplugin-nonfree (mark for "complete removal") and then install the new one from backports (~ubuntu2~dapper1)

Note that it has to download a file from Adobe's website which is not the most reliable of websites.  If it fails, uninstall and reinstall flashplugin-nonfree (it took me a couple tries just now with ~ubuntu2~dapper1)

---

### Post by Limulus on 2006-09-22
> **Limulus said:**
> If it fails, uninstall and reinstall flashplugin-nonfree (it took me a couple tries just now with ~ubuntu2~dapper1)

Ah, actually, if it fails to download, just run the following command from Terminal:

```
sudo update-flashplugin
```

If it works, you should see:

```
Downloading...  done.
```

And then if you type "about: plugins" (but no space and no quotes) in the address bar in Firefox and press enter you should see this entry:

```
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r68

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

---

### Post by Jucato on 2006-09-22
Just to confirm what Limulus said:

A fixed flashplugin-nonfree update has already been uploaded to dapper-backports. Mirrors/servers might take some time to update, but it's already on the main server. Just make sure that you will be installing/upgrading to flashplugin-nonfree 7.0.68~ubuntu2~dapper1. (The bugged one was ~ubuntu1~dapper1).

---

### Post by encompass on 2006-09-22
I don't think the devs have anything to do with it.  What extra sourse does everyone have?  do you all use automatix?

---

### Post by Jucato on 2006-09-22
> **encompass said:**
> I don't think the devs have anything to do with it.  What extra sourse does everyone have?  do you all use automatix?

The bugged update came from dapper-backports. See the bug report I linked to for the details.

---

### Post by OffHand on 2006-09-23
The most recent update fixed the flashplugin-nonfree issue  :)

---

### Post by Statik on 2006-09-23
Fixed the update issue, but the version reported is 7.0.25.0  

I wish there was a version 8.

Statik

---

### Post by Jucato on 2006-09-23
Are you sure about the version being reported? Mine is 7.0.68.0. This fixed update is available now in dapper-backports.

There's no Flash 8 because Adobe (or Macromedia) didn't release one for Linux.

---

### Post by Tuxman on 2006-09-23
Could someone tell me exactly how I am going to install Macormedia Flash in the right way? From start to end. It is very much appreciated, Thanks!

---

### Post by jfba on 2006-09-23
You shoud read item no 2 in this thread :

[http://www.ubuntuforums.org/showthread.php?t=262313&highlight=flash+plugin](http://www.ubuntuforums.org/showthread.php?t=262313&highlight=flash+plugin)

---

### Post by Tuxman on 2006-09-23
Hmm. I stop at this step:
~/Desktop$ sudo linux32 ./install_flash_player_7_linux/flashplayer-installer
sudo: linux32: command not found

---

### Post by jfba on 2006-09-23
you can omit linux32

---

### Post by Limulus on 2006-09-24
> **encompass said:**
> What extra sourse does everyone have?  do you all use automatix?

For my sources see [http://members.shaw.ca/Limulus/ubuntu.html#Synaptic](http://members.shaw.ca/Limulus/ubuntu.html#Synaptic)

I do not use Automatix.

---

### Post by Limulus on 2006-09-24
> **Statik said:**
> Fixed the update issue, but the version reported is 7.0.25.0

???  Are you using Dapper?

According to [http://packages.ubuntu.com/flashplugin-nonfree](http://packages.ubuntu.com/flashplugin-nonfree)

Warty, Hoary and Breezy use 7.0.25
Dapper uses 7.0.63 (Dapper-backports upgrades that to 7.0.68 )

If you haven't upgraded to Dapper, you should! :)

Just run the Update Manager (from the menu or sudo update-manager) and click the upgrade button. It will take a while but is pretty painless :)

---

### Post by Limulus on 2006-09-24
> **Jucato said:**
> There's no Flash 8 because Adobe (or Macromedia) didn't release one for Linux.

And they're not going to either :/

The idea was that they would jump from 7 to 9...  but 9 for Linux won't be out until 2007 (hopefully there will be a beta this year)

Amusingly, you can get Flash 8/9 content running in Linux... with wine :)
See [http://members.shaw.ca/Limulus/ubuntu.html#Internet](http://members.shaw.ca/Limulus/ubuntu.html#Internet) for details

---

### Post by Limulus on 2006-09-24
> **Tuxman said:**
> Could someone tell me exactly how I am going to install Macormedia Flash in the right way? From start to end. It is very much appreciated, Thanks!

0. be sure you have Dapper backports in your sources.list file.  If not or if you're unsure, press alt-F2 to get the Run application dialogue box and run:

```
gksudo gedit /etc/apt/sources.list
```

(enter your password if asked)

If you don't have the following line, add it:

```
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main universe multiverse restricted
```

(you can get more info on repositories on my site: [http://members.shaw.ca/Limulus/ubuntu.html#Synaptic](http://members.shaw.ca/Limulus/ubuntu.html#Synaptic))

save and exit.

1. run the Synaptic Package Manager (its under System -> Administration)

(enter your password if asked)

Press the reload button.

Find the package "flashplugin-nonfree"

Right-click it and select "mark for installation"

Press the apply button.

2. When it finishes, follow [http://ubuntuforums.org/showpost.php?p=1532213&postcount=82](http://ubuntuforums.org/showpost.php?p=1532213&postcount=82)

---

### Post by Tuxman on 2006-09-24
Thanks for the help so far. But when I write "sudo update-flashplugin" this message returns: Downloading... ++++ FAILED.
automatic installation failed due to network problems or upstream changes

---

### Post by Limulus on 2006-09-24
> **Tuxman said:**
> Thanks for the help so far. But when I write "sudo update-flashplugin" this message returns: Downloading... ++++ FAILED.
automatic installation failed due to network problems or upstream changes

Hmm... ok, let's try this: go into Synaptic and mark flashplugin-nonfree for complete removal.  Press Apply.  When its done, try repeating the installation instructions I posted.

Also, if the Adobe servers are begain flaky (and I find they often are) maybe wait a few min and try sudo update-flashplugin again.

---

### Post by tommcd on 2006-09-24
I've been following this thread, as I had the same problem. I just installed the new version via synaptic, and it worked fine! Flash still works too!! Just reload the packages first, or do 'sudo aptitude update' and install via synaptic.

---

### Post by maddbaron on 2006-09-24
well i have two issues, flash works for me but doesnt stay on after i use an external media player. also it doesnt work on sites like wwe.com i have the newest version(dont know how I used automatix and i guess that worked) so now i can view youtube in both opera and firefox but not after using an external player. anyway to fix that? Also I downloaded a .flv file and tried to play in democracy player got video but no sound, could the plugin be causing this?

---

### Post by missmoondog on 2006-09-25
this is really pretty sad. 10 pages on just a simple flashplayer update! :(

---

### Post by Tuxman on 2006-09-25
I still can't get it to work. I get the same error-message when I try to update. Anyway, here is my "about:Plugins" in Firefox. Do you se something interesting that could help?

I splitted it up in two pictures.

---

### Post by Jucato on 2006-09-25
It seems that you have 2 flash plugins, a libflash-mozplugin and the flashplugin-nonfree (shown as libflashplugin.so in your screenshot). I'm not sure if they're conflicting with one another. the flashplugin-nonfree (libflashplugin.so) seems to be the correct version. You could try removing the libflash-mozplugin. I think that's outdated anyway.

---

### Post by Limulus on 2006-09-26
> **Jucato said:**
> It seems that you have 2 flash plugins, a libflash-mozplugin and the flashplugin-nonfree (shown as libflashplugin.so in your screenshot). I'm not sure if they're conflicting with one another. the flashplugin-nonfree (libflashplugin.so) seems to be the correct version. You could try removing the libflash-mozplugin. I think that's outdated anyway.

Yowsers!  Uninstall libflash-mozplugin as fast as you can! =D

From [http://gplflash.sourceforge.net/](http://gplflash.sourceforge.net/)

"The original GPLFlash project, which was meant to bring to GNU/Linux the ability to play Macromedia Flash movies, stalled when Macromedia released a 32-bit binary Flash Player for Linux. Because of that, and because of a lack of development help, the last significant update to GPLFlash was in June 2000. But in the past year there has been a surge in developer interest in the GPLFlash project, and now it's back, with greater stability and fewer bugs. It doesn't support much above flash version 4, and though a gplflash2 has been worked on, it has now been ditched in favour of gnash."

Just out of curiosity, how did that end up on your system, if you know? :)

---

### Post by Tuxman on 2006-09-26
Ok, I will try to uninstall it when I come home. Sudo apt-get remove libflash-mozplugin right? I hope that is reason it Flash won't work.

I don't know how it ended up on my system.

---

### Post by Limulus on 2006-09-26
> **maddbaron said:**
> well i have two issues, flash works for me but doesnt stay on after i use an external media player. also it doesnt work on sites like wwe.com i have the newest version(dont know how I used automatix and i guess that worked) so now i can view youtube in both opera and firefox but not after using an external player. anyway to fix that? Also I downloaded a .flv file and tried to play in democracy player got video but no sound, could the plugin be causing this?

Grr... while Automatix has apparently fixed some of its more egregious faults, this is one of the reasons I still don't like it; it doesn't teach you as it does its job.  Did it tell you in advance what it was going to do to your system, other than a vague promise of working flash?  Another bad thing is that it still can't automatically UNDO the changes it made to your system!

Your best bet is to go complain in the Automatix thread and get them to help you: [http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

Sorry.

---

### Post by Limulus on 2006-09-26
> **Tuxman said:**
> Ok, I will try to uninstall it when I come home. Sudo apt-get remove libflash-mozplugin right?

Yes (note: lowercase s in sudo; remember, the CLI is case sensitive :)

Alternately, use the Synaptic Package manager for GUI goodness :-)

> I hope that is reason it Flash won't work.

With any luck ^_-;

Check the about plugins page and if it doesn't work immediately you can try closing Firefox and then reopening it.

---

### Post by Limulus on 2006-09-26
> **maddbaron said:**
> also it doesnt work on sites like wwe.com i have the newest version

Sadly, the "newest version" for Linux is still 7 while Win and Mac both have 9 :/

I tested wwe.com with the Windows version of Flash 9 in the Windows version of Firefox running under Wine and it worked.

I have some instructions on [http://members.shaw.ca/Limulus/ubuntu.html#Internet](http://members.shaw.ca/Limulus/ubuntu.html#Internet) in case you'd like to view Flash 9 (and Shockwave) content.

---

### Post by Tuxman on 2006-09-26
YES! I removed the libflash-mozplugin and I can play movies at YouTube etc. It seems as I still can't update the other flashplugin(same error message), but it doesn't matter now^^. 

Thanks for all your help : -))).

---

### Post by drewsimon on 2006-10-13
Thanks! That fix worked for me! :)

---

### Post by missmoondog on 2006-10-14
> **Limulus said:**
> Yowsers!  Uninstall libflash-mozplugin as fast as you can! =D

From [http://gplflash.sourceforge.net/](http://gplflash.sourceforge.net/)

"The original GPLFlash project, which was meant to bring to GNU/Linux the ability to play Macromedia Flash movies, stalled when Macromedia released a 32-bit binary Flash Player for Linux. Because of that, and because of a lack of development help, the last significant update to GPLFlash was in June 2000. But in the past year there has been a surge in developer interest in the GPLFlash project, and now it's back, with greater stability and fewer bugs. It doesn't support much above flash version 4, and though a gplflash2 has been worked on, it has now been ditched in favour of gnash."

Just out of curiosity, how did that end up on your system, if you know? :)


why do you say yowser like that for having the libflash-mozplugin on their system? it was on all 7 of mine when i used kubuntu. it never caused an issue with my flashplayer. the only thing that ever did, was this last crappy, untested, updated, non working flashplayer.

---

### Post by Limulus on 2006-10-14
> **missmoondog said:**
> why do you say yowser like that for having the libflash-mozplugin on their system? it was on all 7 of mine when i used kubuntu. it never caused an issue with my flashplayer. the only thing that ever did, was this last crappy, untested, updated, non working flashplayer.

Ubuntu is definitely not Kubuntu.  Maybe it works fine in KDE with Konqueror, but the problem was in Gnome with Firefox. libflash-mozplugin is rather out of date anyway and there is really no good reason for the average person to have it installed.

Is the latter still not working for you?  They corrected the package problem a while back and it should work (as most people, including myself) have reported.

---

### Post by missmoondog on 2006-10-14
yes, it's working awesome for me now that i've moved to zenwalk. even with a great a place as this forum is, i couldn't take the screwed up updates that came out when they did. have to much work on my systems to risk losing it because the pacakage managers, or whatever they're called, don't properly test stuff anymore.

i have had a bear of time getting flash installed on zenwalk up until yesterday. don't know why i've never seen it posted before, but installing the flashplayer-installer is as simple as dragging and dropping it into a command line!

no longer have a trace of k/ubuntu on any of my 7 machines anymore.
zenwalk 3.0 blows k/ubuntu away!! imo

---

