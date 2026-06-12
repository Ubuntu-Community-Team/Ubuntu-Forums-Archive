---
title: "Hulu stopped working in Ubuntu 08/13/2015"
date: 2015-08-13
forum: General Help
---

### Post by kansasnoob on 2015-08-13
This is odd. It was working yesterday - I think even after updating to Firefox 40 and the latest flash update but this AM only the first ad plays and that's it.

I tried the typical stuff like clearing the Firefox cache and the Adobe cache to no avail. Both Ubuntu's browser and Chromium also fail complaining of "protected content".

I also happened to try it in a badly outdated system that hadn't been booted since April to no avail.

But in one of my systems I have Qupzilla installed and Hulu played fine in Qupzilla one time but failed the same as Firefox after reboot.

I added my preferred workaround in [post #8]("http://ubuntuforums.org/showthread.php?t=2290589&p=13339045#post13339045").  But others have expressed favoritism for [using Pipelight]("http://ubuntuforums.org/showthread.php?t=2290589&page=4&p=13345702#post13345702") or [using the Windows version of Firefox in Wine]("http://community.linuxmint.com/tutorial/view/2028").

---

### Post by kansasnoob on 2015-08-13
It also works fine in Chrome - I downloaded and installed it just to see.

Turns out it only worked for one video then displayed the error shown later on in this thread.

---

### Post by kansasnoob on 2015-08-13
Deleted because it was a rant ............ and also a wrong assumption.

---

### Post by kansasnoob on 2015-08-13
Now Qupzilla is displaying a blank screen after the first ad also ](*,)

And Chrome fails with an error warning:

[ATTACH=CONFIG]263839[/ATTACH]

Both of those browsers were working until I shut down the computers for a few hours and then came back. Next up is giving Bleachbit a whirl.

---

### Post by kansasnoob on 2015-08-13
BTW I've also run through this:

[http://www.hulu.com/help/articles/23184736](http://www.hulu.com/help/articles/23184736)

And this:

[http://www.hulu.com/help/articles/166587](http://www.hulu.com/help/articles/166587)

---

### Post by kansasnoob on 2015-08-15
I fiddled around a bit today off and on. I had some fresh installs of 14.04.3 leftover from iso testing earlier this month so I was able to get a pretty good handle on things. Hulu is just borked! If I start with a freshly installed Ubuntu w/o importing anything (meaning fresh Firefox and Adobe profiles) and open Hulu w/o logging in I can watch free content fine until I change shows or even pause and restart - doing so either lands me in a black screen after the first ad or in a white screen with only sound playing.

The only way of getting around that is to dig thru /home and delete anything and everything Adobe flash or Firefox related. Then I can start all over again from scratch. Sometimes I can even watch non-free content if I log in since I'm subscribed, but only until I interrupt the player for any reason - then it's time to start all over again. I'll try to contact them tomorrow. You basically send them a message and they call you on the phone.

Phone conversations are difficult for me because my hearing is even more impaired than my vision so I cooked up a simple way to reproduce this. Just create a live DVD of Mint 17.2 (I used Mate) and since flash is included you can check it out yourself. A live USB would work as well but only if it's setup w/o persistence!

The only other thing I could think of on my end is my Uverse router so I unplugged for a long time when I was on the tractor today, but when I got back in and powered it back up Hulu is still borked.

And only Hulu is effected! I've had no trouble streaming from any other source.

---

### Post by efflandt on 2015-08-15
From a thread I posted (which you have already seen) [http://ubuntuforums.org/showthread.php?t=2290743](http://ubuntuforums.org/showthread.php?t=2290743) Hulu broke something in Linux, possibly while doing updates on their servers Aug 13. Their Help still shows it compatible with Linux, but apparently NOT at the moment even though it has been working fine for years (and last weekend). It would not even work in Firefox or Google Chrome in 14.04 on my laptop which had never been on Hulu before, so it cannot have anything to do with cached data. Whatever they did might have something to do with adding optional Showtime, but no word yet about exactly what they changed about their content delivery. Someone in that reddit link seemed to even have problems resuming after commercials in Win8.

Google Chrome still works fine for Netflix which was somewhat of an issue when Netflix required MS Silverlight before it supported HTML5.

---

### Post by kansasnoob on 2015-08-15
In Firefox it appears that the following works:

```
sudo add-apt-repository ppa:mjblenner/ppa-hal && sudo apt-get update && sudo apt-get install hal
```

Then [clear the Firefox cache]("http://www.hulu.com/help/articles/189358#firefox4") (same as Mac), also [clear the Adobe flash cache]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html") (click on Delete all sites), and then reboot.

This workaround is still working great after 2 weeks so I've marked this thread "solved" ;)

Please do leave a comment regarding your own results with any and all browsers.

---

### Post by JaseP on 2015-08-16
That's apparently the only work-around...

We've been discussing it in this thread...
[http://ubuntuforums.org/showthread.php?t=2290743&page=2](http://ubuntuforums.org/showthread.php?t=2290743&page=2)

---

### Post by SeijiSensei on 2015-08-16
Another alternative to consider is installing [pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html") and using it to run the Windows version of Flash player.  I've been doing that for a while now, and it generally works fine.  You might need to install a UserAgent add-on like [UAControl]("https://addons.mozilla.org/en-us/firefox/addon/uacontrol/") to spoof your UserAgent string and tell Hulu you're running Windows.

---

### Post by JaseP on 2015-08-16
Please note that from the other thread, Hulu contacted me and is looking into the matter...

---

### Post by kansasnoob on 2015-08-16
Mint has a good tutorial for using the Windows version of Firefox in Wine:

[http://community.linuxmint.com/tutorial/view/2028](http://community.linuxmint.com/tutorial/view/2028)

For me the "hal hack" shown in post #8 is sufficient ATM but it's nice to know there are other alternatives.

---

### Post by kansasnoob on 2015-08-16
I provided details including a link to the "hal hack" included in post #8 to Hulu support and received an obvious boiler plate response:

> Crys W., Aug 16, 11:23 AM:

Hi Erick,

Thank you for that detailed information. This is a known issue we are looking into. I will be coordinating with my advanced technicians to find a resolution for you. I would like to gather some specific information to help expedite the resolution for this error.


What browser and browser version? (you can head to ( [http://supportdetails.com/](http://supportdetails.com/) )- you can supply a screenshot from the results in your response.
What content is affected? (ie kids, Movies, All)


I’m sure we’ll get to the bottom of this soon.

Thanks,
Crys W.
Hulu Support

P.S. If at any time your issue is addressed or you'd like to end this conversation, let us know by replying “ALLSET”

Seems that they didn't really bother reading the info I provided.

---

### Post by blong2 on 2015-08-19
Well, I was mucking with this yesterday and tried installing [hal]("http://ubuntuforums.org/showthread.php?t=2290589&p=13339045#post13339045") as well as re-installing / futzing with Flash player.  Nothing worked (in Chrome, nor Firefox).  Today, I needed to install other audio/video packages in my environment to be productive with something unrelated.  After doing work related stuff, I tried Hulu in Chrome and it still didn't work.  I tried Firefox and success!  I can't guarantee that it'll continue working (I just pressed play on my show, made it through a commercial and it's still going), but I'm hopeful.  I don't know if this matters, but I am a paying Hulu customer and a Linux evangelist.  Needless to say, I'll be annoyed (and perhaps cancel my Hulu membership) if this isn't fixed in all Linux browsers.

---

### Post by kansasnoob on 2015-08-19
> **blong2 said:**
> Well, I was mucking with this yesterday and tried installing [hal]("http://ubuntuforums.org/showthread.php?t=2290589&p=13339045#post13339045") as well as re-installing / futzing with Flash player.  Nothing worked (in Chrome, nor Firefox).  Today, I needed to install other audio/video packages in my environment to be productive with something unrelated.  After doing work related stuff, I tried Hulu in Chrome and it still didn't work.  I tried Firefox and success!  I can't guarantee that it'll continue working (I just pressed play on my show, made it through a commercial and it's still going), but I'm hopeful.  I don't know if this matters, but I am a paying Hulu customer and a Linux evangelist.  Needless to say, I'll be annoyed (and perhaps cancel my Hulu membership) if this isn't fixed in all Linux browsers.

I discussed this a bit with Hulu via email and they said the techs are aware of it. But I'm not holding my breath for a fix to come on their end. It's still working great here in Firefox since I installed hal, cleared both the Firefox and Adobe caches, and rebooted. It'll be interesting to see what happens in another two years when flash dies in Linux once and for all.

---

### Post by monkeybrain20122 on 2015-08-19
> **kansasnoob said:**
> Mint has a good tutorial for using the Windows version of Firefox in Wine:

[http://community.linuxmint.com/tutorial/view/2028](http://community.linuxmint.com/tutorial/view/2028)

For me the "hal hack" shown in post #8 is sufficient ATM but it's nice to know there are other alternatives.

Well then you may as well use pipelight. You don't need running the Windows version of FF, all you need is Windwos' version of flash, which you get with pipelight (it works through a wine wrapper)

---

### Post by adventure man on 2015-08-21
> **kansasnoob said:**
> In Firefox it appears that the following works:

```
sudo add-apt-repository ppa:mjblenner/ppa-hal && sudo apt-get update && sudo apt-get install hal
```

Then [clear the Firefox cache]("http://www.hulu.com/help/articles/189358#firefox4") (same as Mac), also [clear the Adobe flash cache]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html") (click on Delete all sites), and then reboot.

But I need to see how that works for a couple of days before I'm ready to say "solved" ;)

Please do leave a comment regarding your own results with any and all browsers.

This doesn't work for me. Anyone know of any other fix? I have version 39.0 of ff.  With pipelight. Ubuntu 14.10. Any updates on this matter?  thanks

---

### Post by monkeybrain20122 on 2015-08-21
> **adventure man said:**
> This doesn't work for me. Anyone know of any other fix? I have version 39.0 of ff.  With pipelight. Ubuntu 14.10. Any updates on this matter?  thanks

Ubuntu 14.10 has reached end of life. Either upgrade to 15.04 (do a clean install, I don't recommend "upgrade" with the upgrade manager) or downgrade to 14.04

---

### Post by Nhorning on 2015-08-23
> **kansasnoob said:**
> In Firefox it appears that the following works:

```
sudo add-apt-repository ppa:mjblenner/ppa-hal && sudo apt-get update && sudo apt-get install hal
```

Then [clear the Firefox cache]("http://www.hulu.com/help/articles/189358#firefox4") (same as Mac), also [clear the Adobe flash cache]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html") (click on Delete all sites), and then reboot.

But I need to see how that works for a couple of days before I'm ready to say "solved" ;)

Please do leave a comment regarding your own results with any and all browsers.

This worked like a charm for me.  But, I'd like to add that Ubuntu can't expect to eat into the mainstream OS market if they keep breaking popular services like Hulu. If there was going to be a HAL depreciation, there should have been some planning around it so it wasn't necessary to dig through forums and install a PPA to get it working again.

---

### Post by deadflowr on 2015-08-23
> **Nhorning said:**
> This worked like a charm for me.  But, I'd like to add that Ubuntu can't expect to eat into the mainstream OS market if they keep breaking popular services like Hulu. If there was going to be a HAL depreciation, there should have been some planning around it so it wasn't necessary to dig through forums and install a PPA to get it working again.

Hulu broke Hulu.
Nothing about Ubuntu to it.

This affects ALL linux distributions.

There was no warning from Hulu on the changes, and no expectations that hal would ever be needed.

---

### Post by kansasnoob on 2015-08-23
> Ubuntu can't expect to eat into the mainstream OS market if they keep breaking popular services like Hulu

Hulu had worked flawlessly in Ubuntu prior to 08/13/2015 so it was actually Hulu that "broke" things ............................. or more properly they just changed things, perhaps due to the addition of Showtime? I suspect there will be more challenges regarding flash content all too soon.

---

### Post by kansasnoob on 2015-08-23
> **deadflowr said:**
> Hulu broke Hulu.
Nothing about Ubuntu to it.

This affects ALL linux distributions.

There was no warning from Hulu on the changes, and no expectations that hal would ever be needed.

But hal has always been needed to stream Amazon Instant Video and Ubuntu still decided to drop hal from the repos, so I think it's fair to say that hal was dropped from the repos prematurely :D

---

### Post by grahammechanical on 2015-08-24
I have not been following this thread but seeing the word "hulu" reminded me of a blog post I read yesterday on Planet Ubuntu. It has the title "Making Hulu videos play in Ubuntu,"

[http://nhaines.livejournal.com/68407.html](http://nhaines.livejournal.com/68407.html)

Regards

---

### Post by SeijiSensei on 2015-08-24
> **kansasnoob said:**
> But hal has always been needed to stream Amazon Instant Video and Ubuntu still decided to drop hal from the repos, so I think it's fair to say that hal was dropped from the repos prematurely :D

I believe that decision was made upstream by the Debian developers.

---

### Post by kansasnoob on 2015-08-24
> **SeijiSensei said:**
> I believe that decision was made upstream by the Debian developers.

Actually the GNOME devs started the ball rolling:

[https://bugzilla.gnome.org/show_bug.cgi?id=593938](https://bugzilla.gnome.org/show_bug.cgi?id=593938)

Presumably because hal is (and has been for quite a while) in maintenance mode:

[http://www.freedesktop.org/wiki/Software/hal/](http://www.freedesktop.org/wiki/Software/hal/)

The problem is that it's still needed to view some DRM protected content. GNOME habitually makes decisions like that - take the old inhibit-applet as an example. A simple click would prevent the activation of the screensaver, but they never replaced it in gnome-shell because apps like Totem now inhibit the screensaver on their own. But not Adobe flash - so there have been poorly maintained efforts at replacing that functionality.

It's an ongoing flaw in some corners of Linux development thinking - getting the cart in front of the horse ;)

Although it goes far beyond Linux alone - consider the recent calls for killing flash, mostly focusing on convincing end users to remove it from their machines. And in most instances the same web pages where you read these *kill_flash_now* diatribes contain content dependent on flash :o

---

### Post by erfahren on 2015-08-26
[**Mint's fix**]("http://community.linuxmint.com/tutorial/view/2028") is the one working for me  - found it in an earlier post - *install the ***main Wine package*** and the open the Windows executables ([**Firefox**]("https://www.mozilla.org/en-US/firefox/all/") and [**win7 flash**]("https://get.adobe.com/flashplayer/otherversions/")) with Wine

---

### Post by monkeybrain20122 on 2015-08-26
> **erfahren said:**
> [**Mint's fix**]("http://community.linuxmint.com/tutorial/view/2028") is the one working for me  - found it in an earlier post - *install the ***main Wine package*** and the open the Windows executables ([**Firefox**]("https://www.mozilla.org/en-US/firefox/all/") and [**win7 flash**]("https://get.adobe.com/flashplayer/otherversions/")) with Wine

This is just overkill. You DON'T need the Windows version of Firefox. All you need is the Windows version of flash and that you get by installing pipelight and enabling flash. I don't know why Mint would go that route (judging from the comments' dates it seems to be a recent thread) Maybe piplelight doesn't work on Mint?

---

### Post by kansasnoob on 2015-08-26
> **monkeybrain20122 said:**
> This is just overkill. You DON'T need the Windows version of Firefox. All you need is the Windows version of flash and that you get by installing pipelight and enabling flash. I don't know why Mint would go that route (judging from the comments' dates it seems to be a recent thread) Maybe piplelight doesn't work on Mint?

Is there any truth to Mint's concerns about webkit:

>  Pipelight is like a wrapper which makes your browser use Windows plugins. So with pipelight, you can run Firefox with the Windows Flash plugin... and IT WORKS! :) It's quite messy though... and I don't recommend you doing that. [COLOR="#FF0000"]**With pipelight you start including Windows layers beneath something you use every day.. not only that but it can mess up Webkit as well (that's used among other things by your login screen, your screensaver, other applications)**[/COLOR].

Rather than installing pipelight and having your OS use a Window version of Flash, we recommend installing a Windows version of Firefox. That way, your Linux system stays clean, it uses its own Linux version of Flash and Linux plugins, and in and only in that Windows version of Firefox is the Windows version of Flash used.

I really don't know and just adding hal solved things for me ........................ and I tend to practice the policy "if it ain't broke don't fix it" :D

---

### Post by monkeybrain20122 on 2015-08-26
> **kansasnoob said:**
> Is there any truth to Mint's concerns about webkit:


Pipelight plugins can be disabled/set to "ask to enable" in Firefox like any other plugiins, and they can also be disabled/enabled with pipelight  commands, so I don't see how "With pipelight you start including Windows layers beneath something you use every day.." You can just disable the plugin when you don't use it, or you can use it with a different Firefox proflle if that bothers you. I have no issue with webkit (i had silverlight plugin for Netflix and unity3d plugin for testing) I find running Firefox is wine kind of unwieldy and ugly, that was basically the approach of the Netflix-desktop app (now deprecated?) by the same devs of  pipelight.

---

### Post by erfahren on 2015-08-26
I tried pipelight and actually had it set up on this particular computer (my friend's tv computer) for netflix awhile back. I couldn't get it to work.

(Edit: I might not have enabled the Flash plugin properly with pipelight, but the Win Ffx with Wine is working well on her old Dell 4600 now. It was the quickest fix for me.)
--
[pipelight]("http://pipelight.net/cms/installation.html") works on it as well. your brief  [pipelight setup guide for flash]("http://ubuntuforums.org/showthread.php?t=2290589&page=4&p=13345702#post13345702") is appreciated, *monkeybrain20122*.

---

### Post by kansasnoob on 2015-08-27
Maybe I should post [this]("http://ubuntuforums.org/showthread.php?t=2290743&page=3&p=13339638#post13339638") in my OP???????

@ monkeybrain20122, do you know of a really good set of instructions for installing/using pipelight?

---

### Post by monkeybrain20122 on 2015-08-27
> **kansasnoob said:**
> Maybe I should post [this]("http://ubuntuforums.org/showthread.php?t=2290743&page=3&p=13339638#post13339638") in my PM???????

@ monkeybrain20122, do you know of a really good set of instructions for installing/using pipelight?

To install pipelight just follow [http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html)

To enable plugins ( can choose from flash, unity3d or silverlight and some other stuffs [http://pipelight.net/cms/installation.html](http://pipelight.net/cms/installation.html))

Close Firefox and run
```
pipelight-plugin --enable pluginname
```

To disable, close FF and run
```
pipelight-plugin --disable pluginname
```

Link uses sudo for these but I prefer without, that way the plugins are enabled only for current Firefox profile.
When you restart Firefox and try to access a site where the plugin is needed (e.g somewhere that needs flash if that was what you enabled), you should see a wine box hovering about downloading and installing the plugin. This should take a moment (I can't remember whether you have to restart FF after that)

For trouble shootings:

If after enabling plugin and it doesn't show up in Firefox (Tools > Addons > Plugins) Close Firefox and run 
```
sudo pipelight-plugin --create-mozilla-plugins
```

If after you enabled plugin (say, flash) and restarted Firefox the hovering wine box kind of appears and then disappears without downloading and installing flash. Close Firefox, disable flash with 
```

pipelight-plugin --disable flash 
```

then run

```
sudo pipelight-plugin --update
pipelight-plugin --enable flash
sudo pipelight-plugin --create-mozilla-plugins


```

Edited: If you want to default to flash 11.2 and only use pipelight flash when needed, then you have to disable it with the pipelight-plugin --disable command when you are done (and always restart Firefox after disabling or enabling plugins for it to take effect) Choosing flash version with Firefox's Tools > Addons > plugins doesn't work, both flash versions will show up but they always have the same settings (always activated, ask to activated, disabled so you cannot just disable one) Firefox automatically picks the higher version, i.e pipelight.

---

### Post by kansasnoob on 2015-08-27
So maybe when 2017 rolls around and Linux flash dies for good pipelight will be the logical way to go - period. Of course I know some people will just say the sooner flash dies the better, but as long as some desired content requires it we'll keep figuring out a way to do it :D

I'm going to be rebuilding my iso-testing test suite in the next week or two so I think I'll give pipelight a go just to see how it all works when I'm done doing that.

---

### Post by galdor2 on 2015-08-28
I'm as NOOB as they come.  Just installed Ubuntu last week and this problem with Hulu really sucked for me.  I'm not that familiar with anything.  But after trying the "Hal" hack - it worked for me.  Now I can watch my Hulu.  I'm so glad that I finally installed Ubuntu and said the he** with microsoft and windows.  Thanks to all for the help with Hulu.  :mrgreen:

---

### Post by galdor2 on 2015-09-09
I also want to report that on another machine, I installed Pale Moon and removed Firefox.  I'm happy to report that the HAL hack also works with Pale Moon!  Thank you all !!!

---

### Post by adventure man on 2015-09-12
Just an update guys...
I managed to resolve this by going into ubuntu software center, finding the hardware abstraction layer (hal) download and installing it from there; which worked on my laptop. On my desktop, I downloaded "zombie hal" through software center, installed it and voila resolved the issue there.  I also upgraded all computers to Vivid Vervet 15.04. Not sure why hal installation didn't work through terminal for me ](*,)
cheers :KS

---

