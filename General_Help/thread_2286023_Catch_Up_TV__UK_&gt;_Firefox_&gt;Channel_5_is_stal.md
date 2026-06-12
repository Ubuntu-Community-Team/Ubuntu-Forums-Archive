---
title: "Catch Up TV  UK &gt; Firefox &gt;Channel 5 is stalling"
date: 2015-07-09
forum: General Help
---

### Post by amoun on 2015-07-09
Trusty > Firefox/Chromium/Opera

Since 1st July or then about I have been unable to watch catch-up on channel 5, channel 4 is ok.

Channel five is asking for update to min Adobe FlashPlayer 15.

Previously the same problem occurred on  channels 4 and 5, a continuous waiting icon, that was sorted by the following. 

[INDENT]

Ubuntu user Michael Blennerhassett maintains a PPA for Ubuntu 13.10 only that contains the required HAL package, along with a patch from (the always awesome) Arch Linux folks that fixes several issues that result from using the older HAL package in Saucy.

To add the PPA open a new Terminal window and enter the following commands carefully:[/INDENT]
```

sudo add-apt-repository ppa:mjblenner/ppa-hal

sudo apt-get update && sudo apt-get install hal
```

Redoing the above made no difference to channel5


I have also checked out [https://wiki.ubuntu.com/Chromium/Getting-Partner-Flash](https://wiki.ubuntu.com/Chromium/Getting-Partner-Flash) and I'm upto date there

I'm about to investigate [http://ubuntuforums.org/showthread.php?t=2284778](http://ubuntuforums.org/showthread.php?t=2284778)  and will post that here:

but if anyone else has this problem, sorted or not, please add to this post.

---

### Post by dino99 on 2015-07-09
maybe go to the channel 5 support's url to know about possible change(s) on their side

---

### Post by Vladlenin5000 on 2015-07-09
+1

... Or simply use Google Chrome which has up-to-date Flash.

---

### Post by amoun on 2015-07-09
**Thanks dino99**

I've done that and they explained that they have moved servers from [https://www.brightcove.com](https://www.brightcove.com) to primetime so i'll get on the case. 

primetime may be a streaming branch of adobe [https://www.adobe.com/marketing-cloud/primetime-tv-platform.html?promoid=KOUEV](https://www.adobe.com/marketing-cloud/primetime-tv-platform.html?promoid=KOUEV)

not having much luck there

**Hi  Vladlenin5000**

I tried chromium, which I understood was the same as google chrome, but maybe Ill try the google version

Thanks foks

---

### Post by Vladlenin5000 on 2015-07-09
No, Chromium is the open source project (Google) Chrome is based on. Among the Google specific code added is the up-to-date Flash (Chromium has none by default).

---

### Post by ajgreeny on 2015-07-09
No not working for me either.  The flash window just shows the rotating icon that shows normally when buffering, but it never actually plays anything.

Channel 5 updated their player on July 6th, but it is not easy to see exactly what is needed, other than the latest version of Adobe Flash Player, which a fully updated chromium should have if you've installed pepperflashplugin-nonfree.

I have done all that, and I have hal installed from the ppa (needed for Channel 4 catchup service, 4-All).

Channel 5 do mention Linux but only to say that Demand-5 "may" work but they do not support it; surprise, surprise!

---

### Post by amoun on 2015-07-09
Starting from scratch with a new install of chromium

bbc.co.uk/iplayer : ok

itv.co.uk/itvplayer/ : warning [https://support.google.com/chrome/answer/6213033](https://support.google.com/chrome/answer/6213033) of lack of future support

>> Following the instructions there didn't do anything so I presume we are past version 45 as there is no option as instructed?
however content load but slow pos due to my setup eeepc 900.

>> the above link ends with
"After the release of Chrome version 45, you&#8217;ll need to use an alternate web browser to load content that requires a NPAPI plugin."

**EDIT 1 July 10th 00:13**

After all this,
Firefox is ok on all but channel 5 still, asking for Adobe update to 15 or above
Chromium just spins away on both channel 5 and 4 
This dual failure is reminiscent of the DRM problem

---

### Post by fitzd34 on 2015-07-13
> **amoun said:**
> This dual failure is reminiscent of the DRM problem

More like penalizing you for not buying a Microsoft license to watch videos on your computer, how convenient.

"To view this page ensure that Adobe Flash Player version 15.0.0 or greater is installed"

[http://www.channel5.com](http://www.channel5.com)

"Sorry, your computer does not have the latest Flash Player installed. Please go to step 2. ( Your version 11.2.202.481 Latest Version 18.0.0.203 )"

[https://helpx.adobe.com/flash-player.html](https://helpx.adobe.com/flash-player.html)

---

### Post by Bucky Ball on 2015-07-13
@amoun: You do have pepperflashplugin-nonfree installed in Chromium?

---

### Post by speartip on 2015-07-13
No joy using Firefox.
But TVcatchup - Channel 5, working absolutely fine with the official Google Chrome, & Hal from #1 installed, on Ubuntu 14.04.

---

### Post by monkeybrain20122 on 2015-07-13
I am almost 100% sure that it is DRM. Chrome may have up to date flash but the Linux version of pepper-flash  doesn't do DRM. Why would a government outfit use DRM technology that discriminates against certain platform should be a question to raise with your MP.  

Anyhow, pipelight flash will work in these cases (Windows flash running in wine) Also see [3] below for an alternative using pepper-flash.

[http://pipelight.net/cms/installation.html](http://pipelight.net/cms/installation.html)

After installing pipelight you can switch to pipelight flash with 
```
pipelight-plugin --enable flash
```
 
To disable it
```
pipelight-plugin --disable flash
```

(There is no need to use sudo for these two commands even though the instruction has sudo) You need to restart Firefox for these to kick in.

If after installing pipelight and restarting firefox flash 18 doesn't show up in Tools > Addons > Plugins, then close Firefox and run
```
sudo pipelight-plugin --create-mozilla-plugins

``` (this one does need sudo)


[1]. There maybe a problem if you use freshplayer-plugin because both pepper-flash and pipelight-flash would have the same version (normally Firefox would pick the higher version so flash 11.2 can coexist with either as a fallback) So you need to disable freshplayer to try this

In order to switch between the two you need to set up update-alternatives for pipelight-flash and freshplayer-plugin. See [http://askubuntu.com/questions/418306/will-there-be-future-support-for-the-pepper-version-of-flashplugin-for-firefox](http://askubuntu.com/questions/418306/will-there-be-future-support-for-the-pepper-version-of-flashplugin-for-firefox) and adapt it for freshplayer-plugin.

[2] Hal only works with flash 11.2 (but 11.2 may not work for being too outdated for the site) so if you use freshplayer again you need to disable it.

[3] There is a way to use freshplayer-plugin for DRM videos, which is to extract pepper-flash from a chromeOS iso instead of from Chrome or the pepperflashplugin-nonfree package. You may want to try that if you want experimenting. See 'DRM doesn't work' from [https://github.com/i-rinat/freshplayerplugin/blob/master/doc/known-issues.md](https://github.com/i-rinat/freshplayerplugin/blob/master/doc/known-issues.md)

---

### Post by johnaaronrose on 2015-08-06
I'm using Trusty & have installed pepperflashplugin-nonfree package from Ubuntu repos. Chromium & Chrome both still give 'waiting' icon when I try to play a programme on 4OD. 

I've also tried installing hal etc using mjblenner's ppa. But that didn't help.

PS I don't want to use pipelight as it created issues. So I removed it.

---

### Post by monkeybrain20122 on 2015-08-06
> **johnaaronrose said:**
> 

PS I don't want to use pipelight as it created issues. So I removed it.

Not sure what issues did you encounter. pipelight flash can be easily disabled and only enabled as needed (see above post) unless you also have freshplayerplugin, in which case you have to set up some kind of way to disable the latter when trying to use pipelight flash (may be able to do it by putting a dummy path in freshplayerplugin's .config file that points to a non existent libpepperflashplugin.so if not able to set up update-alternatives)

---

### Post by johnaaronrose on 2015-08-07
> **monkeybrain20122 said:**
> Not sure what issues did you encounter. pipelight flash can be easily disabled and only enabled as needed (see above post) unless you also have freshplayerplugin, in which case you have to set up some kind of way to disable the latter when trying to use pipelight flash (may be able to do it by putting a dummy path in freshplayerplugin's .config file that points to a non existent libpepperflashplugin.so if not able to set up update-alternatives)

Thanks for reply. I've forgotten the issues with pipelight but I think that they were due to Silverlight usage. Anyway, I did the pipelight install again (having already done the hal install) and did "pipelight-plugin --enable flash". Channel 4 On Demand then worked OK on Firefox after I disabled Adblock Edge for channel4 & set Adblock Popup to allow *channel4. I did similar for Channel 5 but it displayed "To view this page ensure that Adobe Flash Player version        15.0.0 or greater is installed." on Firefox. I have the Adobe Flash Plugin already installed. On Google Chrome, both Channel 4 & Channel 5 gave a constantly displaying 'waiting' icon.
 
Any ideas on how to get Channel 5 Demand working?

---

### Post by monkeybrain20122 on 2015-08-07
Check the flash version first to make sure 18 is available for FF (Tools > addons > plugins) if not close firefox and run
```
sudo pipelight-plugin --create-mozilla-plugins
```

Other than this I am afraid I can't help as I am not in the U.K.

---

### Post by johnaaronrose on 2015-08-07
> **monkeybrain20122 said:**
> Check the flash version first to make sure 18 is available for FF (Tools > addons > plugins) if not close firefox and run
```
sudo pipelight-plugin --create-mozilla-plugins
```

Other than this I am afraid I can't help as I am not in the U.K.

Tried above. Took less than a second with no output. Made no difference to Firefox playing channel 5. Adobe Flash Player plugin is at 11.2/ Linux version available from Adobe is 11.2. As I said previously, 'channel 5' wants 15.0.0 or greater. Therfore stuck.

Anybody else have any ideas?

---

### Post by jim_deadlock on 2015-08-07
I have 15.04 + Gnome Shell (don't think this matters) + mjblenner/ppa-hal + flashplugin-installer (not pipelight) ... channel5 on catchuptv is working fine for me in firefox and chrome.

flashplugin-installer does not have the latest flash version, so I've downloaded the Linux .tar.gz file from [https://get.adobe.com/flashplayer/](https://get.adobe.com/flashplayer/) and simply replaced /usr/lib/flashplugin-installer/libflashplayer.so from the .tar.gz file (currently Version 11.2.202.491).

UPDATE: I've just run Ubuntu Gnome 15.04 from a live DVD, all I had to do was enable multiverse and install flashplugin-installer then channel5 on catchuptv.com is working fine on Firefox, so perhaps this suggests you have some other software interfering with your streaming? Firewall or something?

---

### Post by monkeybrain20122 on 2015-08-07
> **johnaaronrose said:**
> Tried above. Took less than a second with no output. Made no difference to Firefox playing channel 5. Adobe Flash Player plugin is at 11.2/ Linux version available from Adobe is 11.2. As I said previously, 'channel 5' wants 15.0.0 or greater. Therfore stuck.

Anybody else have any ideas?

If adobe plugin is 11.2 then pipelight flash is not registered with Firefox for some reasons. pipelight flash should be version 18 so definitely higher than what channel 5 requires. I don't have pipelight flash enabled since I am using freshplayerplugin. But I can test with a new profile when I go home later.

---

### Post by monkeybrain20122 on 2015-08-07
Hi, I have tested and it turned out that pipelight flash was not installed from running those instructions. You need to update pipelight plugins first, so close FF and run these commands
(if you have previously enable flash, start with a clean slate with

```
pipelight-plugin --disable flash
```)


```
sudo pipelight-plugin --update
pipelight-plugin --enable flash
sudo pipelight-plugin --create-mozilla-plugins
```

Open Firefox and you should see a floating box downloadling and installing pipelight-flash which should take maybe half a minute. Then check your flash version in Tools > Addons > plugins. If it is still 11.2 restart Firefox and check again. You should see flash 18.0.0.209

To disable pipeligt flash and revert to system flash  just close FF and run 

```
pipelight-plugin --disable flash
``` (next time to enable just need one command instead of 3 "pipelight-plugin --enable flash" should be good enough)

Now it would work (just tested with channel 5, don't ask me how ;))

---

### Post by monkeybrain20122 on 2015-08-07
> **jim_deadlock said:**
> I have 15.04 + Gnome Shell (don't think this matters) + mjblenner/ppa-hal + flashplugin-installer (not pipelight) ... channel5 on catchuptv is working fine for me in firefox and chrome.

flashplugin-installer does not have the latest flash version, so I've downloaded the Linux .tar.gz file from [https://get.adobe.com/flashplayer/](https://get.adobe.com/flashplayer/) and simply replaced /usr/lib/flashplugin-installer/libflashplayer.so from the .tar.gz file (currently Version 11.2.202.491).

UPDATE: I've just run Ubuntu Gnome 15.04 from a live DVD, all I had to do was enable multiverse and install flashplugin-installer then channel5 on catchuptv.com is working fine on Firefox, so perhaps this suggests you have some other software interfering with your streaming? Firewall or something?

system flash + hal works on catch up TV  (don't need any tar.gz file. flashplugin-installer is fine and up to date for this) but not on channel 5's actual site, which requires flash version >= 15 as others have reported. Since hal only works on system flash Chrome doesn't work either even though its flash version is up to date (but drm disabled) pipelight is the easiest way (there is another using freshplayerplugin with pepper flash extracted from a chrombook iso, but it is harder)

---

### Post by jim_deadlock on 2015-08-08
Channel 5 website works for me with flash v. 11.2.202.491 (I think this was the reason I had to upgrade it from the flashplugin-installer version).

---

### Post by monkeybrain20122 on 2015-08-08
> **jim_deadlock said:**
> Channel 5 website works for me with flash v. 11.2.202.491 (I think this was the reason I had to upgrade it from the flashplugin-installer version).

11.2.202.491 is the flashplugin-installer version.

---

### Post by amoun on 2015-08-10
Thanks everyone for all the ideas, tried them all but no luck until today

**speartip:** Couldn't get Google Chrome with hal to work

> **monkeybrain20122 said:**
> Check the flash version first to make sure 18 is available for FF (Tools > addons > plugins) if not close firefox and run
```
sudo pipelight-plugin --create-mozilla-plugins
```

Other than this I am afraid I can't help as I am not in the U.K.

Ok monkeybrain20122 this was the last bit. After installing pipelight as advised it was this that brought it up on firefox and now I have channel5.

All is not perfect though as it's a bit out of sync, slow, buffering  bit, choppy and it crashes if I choose full screen option. Did all the checks as in [http://pipelight.net/cms/faqs/faq-bad-performance-install-32-bit-graphic-driver-files.html](http://pipelight.net/cms/faqs/faq-bad-performance-install-32-bit-graphic-driver-files.html) and reported ok.

But on invoking full screen the readout of the error is huge, I'm not bothering anyone with that for now.


Still I may choose the Google Chrome idea again as watching without full screen on an eeepc with 8.9" screen is a bit of a mission.

But hey I feel I'm on the right track again and have some updates on Chicago PD, NCIS and PoI :)

Thanks again

**EDIT Thurs 13th 00:14 GMT** Sadly after trying to watch a few episodes, I can't get channel 5 OD streaming to complete a show. I have to restart computer to get any video. The installation of the updated Adobe (18) also seems to slow other sites that use flash, although this may be more to do with Pipelight/Wine underlay.

---

### Post by amoun on 2015-08-15
Well I've uninstalled pipelight. I'm not sure whether it was some of the pipelight interface or the flash 18 that was the problem but the install screwed up all other streaming, couldn't emulate speartip's success, which could be down to lack of computer resources with a 900Mhz Celeron CPU and 1Gb RAM

I'm back to where I was with bbc, itv and (channel 4 thanks to hal) OK.

I tried google chrome plus hal on a friend's computer, thinking my own machine may have residual problems from previous attempts, but it didn't work on that third party machine either.

So I'm left with, getting rid of 14.04 as reports are, in post #17, that 15.04 works as does Windows and Mac

Not much use in having pipelight and disabling it for rest of streaming when Channel5 is unusable

---

