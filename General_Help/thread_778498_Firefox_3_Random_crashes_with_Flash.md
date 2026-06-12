---
title: "Firefox 3 Random crashes with Flash"
date: 2008-05-02
forum: General Help
---

### Post by Naatan on 2008-05-02
Hi, I am getting the most random crashes from playing flash video's or well.. flash in general.

The crash is non-reproducible.. to give you an example.. I'm watching vids on youtube or break and I can watch about 5 vids and at the 6 it just crashes upon loading (note these numbers can be anything.. it can be the first.. the 7th.. the 11th.. whatever).

It has nothing to do with the video cause when I start firefox again it plays fine.

I ran firefox in console and got the following

```
(firefox:8020): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8020): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8020): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8020): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
debugger.onModuleDeactivate Attempt to deactive context that is not active http://media1.break.com/RealTime/mostviewed/daily/mostviewed3.html
debugger.onModuleDeactivate Attempt to deactive context that is not active http://media1.break.com/RealTime/mostviewed/daily/mostviewed4.html
debugger.onModuleDeactivate Attempt to deactive context that is not active http://www.break.com/2008-mtv-movie-awards/knocked-up-by-a-zombie_1.html
debugger.onModuleDeactivate Attempt to deactive context that is not active http://www.break.com/2008-mtv-movie-awards/knocked-up-by-a-zombie_1.html
debugger.onModuleDeactivate Attempt to deactive context that is not active http://media1.break.com/RealTime/mostviewed/daily/mostviewed4.html

(firefox:8020): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8020): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8020): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8020): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
debugger.onModuleDeactivate Attempt to deactive context that is not active http://my.break.com/Content/view.aspx?ContentID=496109
**Segmentation fault**

```

All the lines except the one in bold are shown whenever I watch a flash video, but they don't cause a crash.. it's only the bold line that it seems to crash on.

Btw. By crash I mean it just "exits".. no message.. nothing.

Anyone familiar with this?

---

### Post by czechman86 on 2008-05-02
i was having the same problems. other uses have reported to me that its just junk flash. there are a number of alternatives or you can just uninstall as i did. i find myself to be happier being flash free than with flash. it was always my favorite part of ppc linux.

here is my thread on the subject. some solutions are featured.
[http://ubuntuforums.org/showthread.php?t=772963](http://ubuntuforums.org/showthread.php?t=772963)

good luck!

EDIT: FredB recommend to me that I try swfdec in place of flash. it works well with youtube.

---

### Post by ironclaw on 2008-05-07
I have the same problem on Firefox 3 Beta 5 (8.04, AMD64) with the proprietary Adobe Flash plugin. I have tried both Swfdec and Gnash previously, but I find that they sometimes run significantly slower, and sometimes do not support some Flash content.

After the crash it seems that a restart of Firefox is needed to have Flash working again.

---

### Post by insllvn on 2008-05-10
I started having this problem after I installed libflashsupport to fix some compatibility problems between flash and pulseaudio. I found a fix, but it is far from ideal.

1) uninstall flashplugin-nonfree

sudo apt-get purge flashplugin-nonfree

2) install nspluginwrapper

     [http://packages.debian.org/nspluginwrapper](http://packages.debian.org/nspluginwrapper)
     Use "Debian unstable" as Ubuntu is based off that code.

3) reinstall flash

     sudo apt-get install flashplugin-nonfree

This didn't stop flash from crashing, just from taking Firefox with it. The problem is that occasionally the binary blob that is being loaded into nspluginwrapper will go zombie when flash crashes, and you wind up having to restart Firefox anyhow. YMMV, hope this helps you out, personally I went back as I was restarting Firefox every time anyway, crash recovery would kick in and it was just faster to relaunch.

---

### Post by LeBurt on 2008-05-11
I've had the same problem since Hardy. Personally, I'd rather wait for an official fix than try to work around the problem. Like the song says: "well I got a girlfriend and things to get done..."

Is it just me or is this (imho very serious) problem taking an unusually long time to fix? I don't mean to sound impatient but browsing sites with flash content is something you do every hour, not every other week...

Anybody have an estimate of when?

---

### Post by Caraibes on 2008-05-11
seriously guys, use swfdec (or Gnash...)...

Never ever had a crash in FF3 (don't use Adobe Flash... swfdec instead...)

---

### Post by mardawi on 2008-05-11
Someone suggested somewhere that using FlashBlock firefox plugin reduces the crashes since you only play flashes that you want on the page.

I use it to make firefox run faster when opening multiple pages that have a lot of flash on them.

I know that disabling Flash is not a solution, but it helps!

---

### Post by rello on 2008-05-11
I was having the same problems, i.e. computer freezes up while Firefox 3 beta 5 was playing Flash content.  I 'solved' it by going back to a Firefox-2 and have been surfing the web with much more stability ever since...

Here is how: $ sudo apt-get install firefox-2

---

### Post by tosoth on 2008-05-12
I solved it by setting ALSA everywhere in System/Preferences/Sound  and adding
```
pulseaudio --kill
```
to System/Preferences/Sessions to kill pulseaudio daemon. (I didn't want to uninstall pulseaudio. Maybe it will be fixed).

I can watch youtube movies and open every flash I want and firefox doesn't crash anymore.

---

### Post by Skerit on 2008-05-12
IMHO, I believe adding the beta of Firefox 3 and pulseaudio was a terrible idea *for now* but quite clever later on (things will run smooth in small year, and this IS an LTS)

Anyway, my firefox crashes from time to time too. So does pulseaudio. Sometimes the audio is just gone, without a single message. Fun!

---

### Post by LeBurt on 2008-05-12
So, in essence, lots of workarounds but no word yet of an official fix. Can we even say that the problem is definitely a) Firefox; b) Flash; c) PulseAudio; or d) all of the above? 

What are the developers saying about this? Has anyone even read a post where someone exclaims Eureka! I found the problem to be this or that, I know how to fix it, next release is Monday the 19, etc.?

---

### Post by koskos on 2008-06-18
I recommend Opera 9.5 - on Linux it works with flash far better than Firefox 2 or 3.

I know a lot of people would be keen to blame the Adobe binary, but even if it is at fault the truth is that Firefox 3 mishandles its incorrect behaviour and crashes along with it.

---

### Post by pangloss on 2008-06-19
> **insllvn said:**
> I started having this problem after I installed libflashsupport to fix some compatibility problems between flash and pulseaudio.

I also only started having problems with Firefox sporadically crashing after installing libflashsupport recently. Haven't tried your workaround yet, but just wanted to add my data point.

---

### Post by Dubbayoo on 2008-06-19
I  had this problem so bad I considered giving up browsing. I solved it by uninstalling the Adobe Flash and using the free one. I tried gnash but Flash applets wouldn't run automatically w/o clicking each one, annoying.

---

### Post by _Stevie_ on 2008-06-19
opera crashes here too. so this isnt an option. dunno if its a flash issue, though.

---

### Post by KillaW0lf04 on 2008-06-29
Hey guys, got the exact same problem. Any update on a fix? This is starting to get very annoying :/

---

### Post by ivantis on 2008-06-29
I had this problem a while ago (Breezy badger). I later found out that the installation CD was really scratched up, and some other things would not work either.
I suggest reinstalling, or re-burning the CD at a slower speed.

---

### Post by _Stevie_ on 2008-06-30
hmm could be the problem yeah. but i also installed flash 10 beta.
this doesnt come from the cd.

---

### Post by ExquisiteDeadGuy on 2008-07-03
I'm also getting this problem (8.04 AMD64) here's the error I get in syslog when it happens if it will help the developers track it down:

kernel: [459872.567880] npviewer.bin[17503]: segfault at 4 rip f6e15d54 rsp ff8e7a50 error 4


Thanks

---

### Post by dodle on 2008-07-03
Not sure if this will work; but if you have manually installed any fonts on your system, delete them and delete the ~/.fonts folder.

It's worth a try, eh?

---

### Post by grege on 2008-07-08
This fault is an utter pain and getting worse. I am at the point of ditching Ubuntu and installing Debian Lenny. It must be fixed NOW.

Blaming Adobe is a cop out. If you install Flash 10 beta it still happens. If you load Seamonkey from Synaptic and do a bit of manual fiddling you can browse the Internet without crashes. I have it setup with Flash 10, Acroread, Java and VLC for video and it is rock solid.

This is not a trivial thing, it is a show stopper - to the developers - FIX IT please.

Perhaps an easy way to ditch Pulse Audio would be a good start.

:(

---

### Post by _Stevie_ on 2008-07-09
fully agreed. i'm losing interesst in ubuntu atm, since I can't do sh'*§)§t !

---

### Post by ezsit on 2008-07-09
> This fault is an utter pain and getting worse. I am at the point of ditching Ubuntu and installing Debian Lenny. It must be fixed NOW.

Blaming Adobe is a cop out. If you install Flash 10 beta it still happens. If you load Seamonkey from Synaptic and do a bit of manual fiddling you can browse the Internet without crashes. I have it setup with Flash 10, Acroread, Java and VLC for video and it is rock solid.

This is not a trivial thing, it is a show stopper - to the developers - FIX IT please.

Sounds like you already fixed your problem by using Seamonkey. I've gone that route back in the Breezy days since it is far better than Firefox. What I don't get is your insistence that this be fixed right now. You already solved your problem.

Flash and Firefox problems is a show stopper? Why? Is all you do surf flash sites? Windows will work fine for that task. This is a trivial thing since using Firefox 2.0.0.x or Seamonkey will easily fix the problem. If you don't think this is a fix, then you haven't tried the solution.

And to this person:
> fully agreed. i'm losing interesst in ubuntu atm, since I can't do sh'*§)§t !

If all your interest in Ubuntu revolves around flash and firefox, then jump ship now because you don't have the patience for Linux.

---

### Post by _Stevie_ on 2008-07-09
i'm using linux for 3/4 year now. this problem arose only since hardy.
and for your information:
there are so many sites with hidden flash stuff that you cant control it all. i will install an anti-flash plugin. maybe this helps a bit.

---

### Post by jesse0 on 2008-07-11
> If all your interest in Ubuntu revolves around flash and firefox, then jump ship now because you don't have the patience for Linux.

Please, nobody listen to this guy. People like this give Linux users a bad name, this is something Nick Burns would say. (SNL, Your Company's Computer Guy) Your computer works for you, not vice-versa.

Regarding the Flash crashing problem. I've been having this problem since I upgraded to Hardy, both on FF 3.0 beta 5 and 3.0 final. I've also had it with both Flash 9 and 10 beta, from Adobe. 

In every case except one, I've been able to work around by going to Tools > Clear Private Data (Ctrl+Shift+Del) and erasing Cache and Offline Content.

The only site this doesn't work on is xbox.com after logging in. That site just crashes whenever flash is enabled.

Jesse.

---

### Post by _Stevie_ on 2008-07-11
> **jesse0 said:**
> Please, nobody listen to this guy. People like this give Linux users a bad name, this is something Nick Burns would say. (SNL, Your Company's Computer Guy) Your computer works for you, not vice-versa.


so true jesse0. i use a computer not for the sake of the computer itself, but for work, entertainment, etc...

---

### Post by zefew on 2008-07-13
> **jesse0 said:**
> 
Regarding the Flash crashing problem. I've been having this problem since I upgraded to Hardy, both on FF 3.0 beta 5 and 3.0 final. I've also had it with both Flash 9 and 10 beta, from Adobe. 


This happens on Gutsy too, btw. 
I upgraded to Firefox3 and the situation became much worse.
When it was FF2, all I had to do to recover was to kill the flash subprocess, but now FF3 becomes a zombie process even after closing the window.

---

### Post by Master Chief on 2008-07-13
Some people here reported to use SeaMonkey (the Mozilla Firefox sibling), which is currently at version 1.1.10, without too much pain, your millage may vary. Here's the link:

[http://www.seamonkey-project.org/releases/](http://www.seamonkey-project.org/releases/)

P.s. You should have received yet another MF3 update by now, or after waking up ;)

---

### Post by ezsit on 2008-07-17
Me:
> If all your interest in Ubuntu revolves around flash and firefox, then jump ship now because you don't have the patience for Linux.

jesse0:
> Please, nobody listen to this guy. People like this give Linux users a bad name, this is something Nick Burns would say. 

Was something I said untrue? "If all your interest in Ubuntu revolves around flash and firefox, then jump ship now because you don't have the patience for Linux." Let me know if this is not wise advice to someone solely interested in flash and firefox working correctly to browse websites. 

Here is the quote I responded to, just to remind readers that the poster indicated that he couldn't do sh&t without flash and firefox working correctly:

_Stevie_:
> fully agreed. i'm losing interesst in ubuntu atm, since I can't do sh'*§)§t !

If I were simply interested in such behavior and this would constitute a deal-breaker for me, I would use Windows because a majority of the websites out there work under Windows just fine.

If I were simply interested in flash and firefox working correctly I would not necessarily have the patience or fortitude to install Windows by myself, let alone Linux. All web surfers are not necessarily cut out to install, maintain, and troubleshoot operating systems problems, whether the OS be Linux or Windows or  OSX.

So, I ask, what did I say that was untrue or inaccurate? Please, enlighten me if you can.

---

### Post by insllvn on 2008-08-22
So, as a general update, I have found neither method of installing Flash 9 (standard or with 32-bit wrapper) secure, but the current release candidate available on the Adobe site for Flash 10 has been working like a charm. It is available as an RPM, but you can use alien to convert it to DEB. I also found it necessary to copy flashplayer.so from its default install directory, /usr/lib/flash-plugin/libflashplayer.so to ~/.mozilla/plugins .

Commands are, once you download the file

sudo apt-get install alien

sudo alien {flash installer RPM}

sudo dpkg -i flash-plugin_10.0.0.569-1_i386.deb

cp /usr/lib/flash-plugin/libflashplayer.so ~/.mozilla/plugins

I will continue to update with my Flash 10 experiences, although for now i am very pleased, and believe I can even detect a slight increase in video quality, I have noticed that in full screen I have some audio sync issues that seem to effect only HULU at the moment.

---

### Post by insllvn on 2008-08-22
> **insllvn said:**
> sudo alien {flash installer RPM}

Read my post over and felth this bit was unclear, {flash installer RPM} is intended to denote the file you get from Adobe's sight, and is not the name of the file. I deleted it after conversion, and can't remember what it was called.

---

### Post by mb_webguy on 2008-08-22
I've had no problem since I installed the Flash 10 plugin from the backports repository...

---

### Post by bizghetto2 on 2008-08-30
Hi,

   I'm extremely new to linux, I just installed it 2 months ago and have gone from one problem to the next... this flash crashing thing has already made me angry and upset and now I'm starting to think I should just give up and go back to windows. I have ubuntu 8.04 Hardy and use the latest version of flashplayer. I've searched over and over again through these forums and have found 8 billion solutions to the same problem. I've also seen posts where two or three people say the solution worked perfectly and then 5 more saying its a terrible idea and made things worse. 

What do I do?

---

### Post by ExquisiteDeadGuy on 2008-08-30
> **bizghetto2 said:**
> Hi,

   I'm extremely new to linux, I just installed it 2 months ago and have gone from one problem to the next... this flash crashing thing has already made me angry and upset and now I'm starting to think I should just give up and go back to windows. I have ubuntu 8.04 Hardy and use the latest version of flashplayer. I've searched over and over again through these forums and have found 8 billion solutions to the same problem. I've also seen posts where two or three people say the solution worked perfectly and then 5 more saying its a terrible idea and made things worse. 

What do I do?

A few things to try:

In any Flash object, right-click and hit Settings, then make sure "Enable hardware acceleration" is unchecked. I did this and crashes became less frequent.

You can also install the NoScript and AdBlock plus extensions, this reduces the number of Flash ads your browser tries to display hence reduces the opportnities for flash to crash.

If that doesn't work, you can try installing Ubuntu Gutsy (the second most recent version), I never had any Flash crash problems until I upgraded to Hardy.

If you have the 64-bit version installed you could also try installing the 32-bit version instead.

You could also try Opera instead of Firefox, I've heard it's more stable: [https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

Good luck.

---

### Post by neilmw on 2008-09-18
> **tosoth said:**
> I solved it by setting ALSA everywhere in System/Preferences/Sound  and adding
```
pulseaudio --kill
```
to System/Preferences/Sessions to kill pulseaudio daemon. (I didn't want to uninstall pulseaudio. Maybe it will be fixed).

I can watch youtube movies and open every flash I want and firefox doesn't crash anymore.

That seems to have fixed it for me, thanks Tosoth.

Firefox was crashing frequently when playing flash content, quite reproducible too. After a clean start of FF, generally it'd crash on loading the second video/anim.

Neil

---

### Post by kgsbu2 on 2008-09-20
Both Firefox and Opera were crashing about he same, so that ruled out Firefox. Changed sound to Alsa as suggested, its been 3 days without either browser crashing.

Thanks.

---

### Post by Disident on 2008-09-25
It's interesting that when I open a video on YouTube in one tab and quickly go to some other tab in Firefox (3.0.2) and wait until video starts than switch back to video tab, it didn't crash.

also found this link, I'm going to try it now:
[http://grumpymole.blogspot.com/2006/10/ubuntu-firefox-flash-crash-this-fix.html](http://grumpymole.blogspot.com/2006/10/ubuntu-firefox-flash-crash-this-fix.html)

cheers and hope we're gonna work this thing out because it's really annoying.

---

### Post by jspiers on 2008-10-17
Hi guys. I had the same problem, lots of FF crashes with Flash version 9, needed to upgrade to version 10 but it hasn't shown up as an automatic upgrade. I'm not a hardcore hacker or anything and I like to let the synaptic package manager do my upgrades, but the problem is that flashplugin-nonfree version 10 is not in the regular repository. Luckily I found another thread on ubuntuforums where someone said to use the "backports" repository. Once you tell synaptic to use the backports repository, you can install version 10 automatically (no hacking necessary):

Open "System > Administration > Synaptic Package Manager"
Go to "Settings > Repositories"
Click on "Updates" tab
Check the "Unsupported updates (hardy-backports)" box
Now "Reload" the package information from the repositories
"flashplugin-nonfree" version 10 should now appear.

I hope this helps someone. Long live ubuntuforums!

---

