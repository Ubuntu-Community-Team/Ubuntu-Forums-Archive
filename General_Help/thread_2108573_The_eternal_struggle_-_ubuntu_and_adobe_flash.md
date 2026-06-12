---
title: "The eternal struggle - ubuntu and adobe flash"
date: 2013-01-25
forum: General Help
---

### Post by vvd416 on 2013-01-25
I cannot remember how many times I had problems with flash player in different versions of Ubuntu, but before coming to 12.10 I was able to resolve them somehow. But now I am really stuck.

Here is the scenery: freshly installed Xubuntu 12.10 with all updates, the latest versions of Chrome and Firefox and flashplugin reinstalled several times. As you can guess in both browsers the page at [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) shows nothing good, namely "... a plugin is needed to display this content". In Firefox the Add-ons Manager page proudly shows Shockwave Flash 11.2 r202; libflashplayer.so has been also updated from the Adobe site several times.

The only leads are messages in the apport.log similar to the following:

ERROR: apport (pid 22216) Wed Jan 23 23:41:08 2013: called for pid 22214, signal 4, core limit 0
ERROR: apport (pid 22216) Wed Jan 23 23:41:08 2013: executable: /usr/lib/firefox/plugin-container (command line "/usr/lib/firefox/plugin-container /usr/lib/flashplugin-installer/libflashplayer.so -greomni /usr/lib/firefox/omni.ja 22141 true plugin")
ERROR: apport (pid 22216) Wed Jan 23 23:41:08 2013: executable version is blacklisted, ignoring

All attempts to launch Chrome with Pepper flash result in crashes at /sbin/init. For details see [https://bugs.launchpad.net/ubuntu/+bug/1103844](https://bugs.launchpad.net/ubuntu/+bug/1103844)

One additional piece of information: Ubuntu 10.04 running exactly on the same hardware has absolutely no problems with playing flash. 

Question: is there anything I can do in this situation besides posting one more bug report, which nobody will read?

---

### Post by meteorrock on 2013-01-25
To get flash working you first must install it through the firefox browser that comes included with Ubuntu. I got this working with Ubuntu 12.10.
This bug is in the kernel itself, it goes clear back to 2010 and only Linus Torvalds himself can rectify it. He knows about it but has a hatred for flash, he is pushing for HTML 5 to be implemented on all web sites, but it will take time. Just like a Steve Jobs. So he does not fix it :) 

Anyway, 

Get this app here to get flash up. It will use a different flash player but it will work. Adobe flash will not work anymore as it has been discontinued for linux from Adobe. Other flash players for linux will work, like the "Shockwave" flash player that will be installed with the plugin below. 

Its called "flash aid" at this link here. It is a flash plug in that will remove conflicting errors and install flash for you on firefox. [https://addons.mozilla.org/en-us/firefox/addon/flash-aid/](https://addons.mozilla.org/en-us/firefox/addon/flash-aid/)

After downloading that plug in, it will walk you through with a wizard after you install that plug in with firefox.

After you get flash up and going with that app, it will work with other browsers you want to use. But it first has to be implemented on the firefox browser. 

~~~~~~~~~~~~~~
Help develop up in XDA for their android flagship device at this link here. [http://forum.xda-developers.com/forumdisplay.php?f=860](http://forum.xda-developers.com/forumdisplay.php?f=860)

---

### Post by vvd416 on 2013-01-25
Thank you, so it is a kernel bug. That I was thinking as well, and thus it does not make sense to try another distros like Gentoo.

I forgot to mention in my post that I had tried flash-aid already with no positive effect. Anyway I will try it again after purging flash plugins. If something good comes out I will write it down.

---

### Post by mcduck on 2013-01-25
Actually the problem is that you are looking at the page for the Shockwave plugin, which is a completely different thing from Flash (AKA "Shockwave Flash").

There is no Shockwave plugin for Linux, never has been and never will be as neither Adobe nor Macromedia before them has had any intentions to create one.

The test page for the Flash plugin is here: [http://www.adobe.com/products/about-flash.html]("http://www.adobe.com/products/about-flash.html")

And, by the way, I'm quite happily using the latest version of Flash plugin installed through Ubuntu's repositories at this very moment (on Ubuntu 12.04). So unlike what the above post suggest, it should work just fine and the problem is definitely something else than "Linus Torvalds not supporting it in the kernel" ;)

---

### Post by meteorrock on 2013-01-25
> **mcduck said:**
> Actually the problem is that you are looking at the page for the Shockwave plugin, which is a completely different thing from Flash (AKA "Shockwave Flash").

There is no Shockwave plugin for Linux, never has been and never will be as neither Adobe nor Macromedia before them has had any intentions to create one.

The test page for the Flash plugin is here: [http://www.adobe.com/products/about-flash.html]("http://www.adobe.com/products/about-flash.html")

And, by the way, I'm quite happily using the latest version of Flash plugin installed through Ubuntu's repositories at this very moment (on Ubuntu 12.04). So unlike what the above post suggest, it should work just fine and the problem is definitely something else than "Linus Torvalds not supporting it in the kernel" ;)If you say so. Kernel or framework bug , its been around forever.

If its a bug in the framework, fix it then. Go summit that github patch. Two whole years? Comon. You "JUST" have everyone doing these little "kiddie script" GUI hacks for flash on all of the Linux distos. Yes, I checked. 

So what flash does flash-aid use? Its not from adobe. :popcorn:

Here is a thread for putting shockwave flash on linux. Try google next time. [http://www.linuxhomenetworking.com/forums/showthread.php/18706-Installing-Shockwave-Flash-plug-in-for-Mozilla](http://www.linuxhomenetworking.com/forums/showthread.php/18706-Installing-Shockwave-Flash-plug-in-for-Mozilla)

---

### Post by Adam_GUI on 2013-01-25
> **meteorrock said:**
> If you say so. Kernel or framework bug , its been around forever.

If its a bug in the framework, fix it then. Go summit that github patch. Two whole years? Comon. You "JUST" have everyone doing these little "kiddie script" GUI hacks for flash on all of the Linux distos. Yes, I checked. 

So what flash does flash-aid use? Its not from adobe. :popcorn:

You're trolling, right?

The OP was linking to a page for Adobe Shockwave while asking about Adobe Flash.  There's never been a package of Shockwave for Linux. Whither he's linked to that page erroniously or not, we don't know yet.

If the OP wants Shockwave, there's an [Ubuntu Community Guide]("https://help.ubuntu.com/community/Shockwave") for installing Firefox in Wine and using the Windows Flash and Shockwave versions.

As for Chrome PPAPI Flash, I've had no issues running Google-Chrome Stable Version 24.0.1312.52.  It's a nice fallback for flash on sites like Blip.tv or Springboard that like to crash the NNAPI flash player.

---

### Post by meteorrock on 2013-01-25
> **Adam_GUI said:**
> You're trolling, right?

The OP was linking to a page for Adobe Shockwave while asking about Adobe Flash.  There's never been a package of Shockwave for Linux. Whither he's linked to that page erroniously or not, we don't know yet.

If the OP wants Shockwave, there's an [Ubuntu Community Guide]("https://help.ubuntu.com/community/Shockwave") for installing Firefox in Wine and using the Windows Flash and Shockwave versions.

As for Chrome PPAPI Flash, I've had no issues running Google-Chrome Stable Version 24.0.1312.52.  It's a nice fallback for flash on sites like Blip.tv or Springboard that like to crash the NNAPI flash player.

Huh? I am not trolling. The Opera browser has this issue tagged since 2010 through their Opera linux issue tracker. Did a two day long search on how to fix this issue and wanting to work on trying to submit a patch for it. Tickets everywhere and bug issues for it all through the google search on the github. What is this obsession you guys have for Adobe? Is there an open source solution? Does Adobe only make flash? Comon guys, stop trying to think so linear. 

~~~~~~~~~~~~~

Anyho, I just assume if its a bug outside of the kernel it would of been fixed by now. Wouldn't it have been? People would not have let it slide that long if there was a simple fix or solution for it.

I got 3 or more linux distros on the VMware hypervisor, they are all having issues with flash. The only solution I got working is using that flash-aid. Whether it uses an Adobe "shockwave" or another labeled flash player should be irreverent. As long as it works. But I guess that is just how I think. Anyway I am out of this thread. Good luck. 

Got a hack over in the linux mint forums for anyone wanting to help at this link here. [http://forums.linuxmint.com/viewtopic.php?f=42&t=122822](http://forums.linuxmint.com/viewtopic.php?f=42&t=122822)

---

### Post by Adam_GUI on 2013-01-26
> **meteorrock said:**
> Huh? I am not trolling. The Opera browser has this issue tagged since 2010 through their Opera linux issue tracker. Did a two day long search on how to fix this issue and wanting to work on trying to submit a patch for it. Tickets everywhere and bug issues for it all through the google search on the github. What is this obsession you guys have for Adobe? Is there an open source solution? Does Adobe only make flash? Comon guys, stop trying to think so linear. 

~~~~~~~~~~~~~

Anyho, I just assume if its a bug outside of the kernel it would of been fixed by now. Wouldn't it have been? People would not have let it slide that long if there was a simple fix or solution for it.

I got 3 or more linux distros on the VMware hypervisor, they are all having issues with flash. The only solution I got working is using that flash-aid. Whether it uses an Adobe "shockwave" or another labeled flash player should be irreverent. As long as it works. But I guess that is just how I think. Anyway I am out of this thread. Good luck. 

Got a hack over in the linux mint forums for anyone wanting to help at this link here. [http://forums.linuxmint.com/viewtopic.php?f=42&t=122822](http://forums.linuxmint.com/viewtopic.php?f=42&t=122822)

Shockwave is not flash player.  For someone so obsessed over bug reports, you sure don't like to read.

---

### Post by meteorrock on 2013-01-27
> **Adam_GUI said:**
> Shockwave is not flash player.  For someone so obsessed over bug reports, you sure don't like to read.


And you have been reported. Have fun. Nice way to get new members involved here, especially girls. Take that drama to facebook. If you guys actually debugged your builds here there would be no need for this anyway. 

Way to go guys :) Lets ostracize women and girls from NEVER using linux by making some stupid point. Like I said, I do not care. Get it working without having new linux users jump through hoops and using scripts.

---

### Post by Bucky Ball on 2013-01-27
[B][I]Thread closed for moderation.

[/I][/B]Apologies to the original poster. 

@ meteorrock & Adam_GUI: From the forum Code of Conduct, which you both agreed to when joining, FYI.

> 
[LIST=1]
[*]**Trolling, Attacks and Flaming:** These are always forbidden.
[LIST]
[*]Trolling is posting in a way that provokes emotional responses.
[*]Attacks and derogatory terms of any kind are not welcome. This  includes references to other operating systems and the companies that  produce them.
[*]Flames are messages that personally attack or call any people  names or otherwise harass. These, along with any generally condescending  posts will be edited or removed at the moderators discretion.
[*]If a thread is flame-bait (appears to be intended to start an  argument or is likely to cause an argument rather than enhance  discussion, as in trolling), it will be locked or removed without  notice. Individual flame-bait comments in a post may be deleted or  edited at the moderators' discretion.
[*]If the thread turns into an argument, it can be closed to further  comment or removed without notice. Sometimes a moderator may split the  thread or delete certain portions in order to keep the discussion going,  but that is not always possible since we are a staff of volunteers with  limited time and numbers.
[/LIST]
 
[/LIST]


---

### Post by Bucky Ball on 2013-01-27
***Thread Closed***

The correct information is given by mcduck in post #4.

@ meteorrock & Adam_GUI: If you wish to flame each other please do so somewhere else. This does not mean flaming via the forum's PM facility but doing it somewhere not associated with these forums in any way.

Flaming each other on another user's thread is both unfair to the original poster and against forum rules. Doing so on *any* thread or via PM is against forum rules and future indiscretions will attract the appropriate warnings and/or account suspensions. Thankyou.

BB

---

