---
title: "Firefox freezes and turns grey in Gutsy"
date: 2007-10-24
forum: General Help
---

### Post by PartisanEntity on 2007-10-24
Has anyone else experienced this behaviour in Firefox? Sometimes it will freeze and turn grey, I then have to wait for a few seconds for it to resume again.

Is this a FF or Compiz-Fusion issue?

For example, when I first start the computer and launch FF for the first time, then if I visit ubuntuforums.org and click on User CP, FF will freeze and turn grey, then resume again after a couple seconds. Once it has done it's thing it will not freeze again if I click on User CP again.

---

### Post by venator260 on 2007-10-24
I get that on most of the first visits of my browsing session to the Ubuntu Forums.

---

### Post by thomashauk on 2007-10-24
I've had it turn grey without freezing. Lucky I was only reading text!

---

### Post by n3tfury on 2007-10-24
fwiw, the grey is for any program. like a "no response" indicator of sorts.  i've had this happen a couple of times loading a horribly flashy and busy page.

---

### Post by professor fate on 2007-10-24
Yes, yes, yes.  This has happened to me several times today.

---

### Post by RAV TUX on 2007-10-24
> **PartisanEntity said:**
> Has anyone else experienced this behaviour in Firefox? Sometimes it will freeze and turn grey, I then have to wait for a few seconds for it to resume again.

Is this a FF or Compiz-Fusion issue?

For example, when I first start the computer and launch FF for the first time, then if I visit ubuntuforums.org and click on User CP, FF will freeze and turn grey, then resume again after a couple seconds. Once it has done it's thing it will not freeze again if I click on User CP again.It has also happen to me on Firefox only here at Ubuntuforums.org(this could be because this is where I first come)...I don't have Compiz-Fusion installed.

(Note this was on the old Firefox Version 2.0.0.6 I have since updated to Firefox 2.0.0.8...and it hasn't happen yet.)

---

### Post by Billy_McBong on 2007-10-24
[COLOR="Blue"]happens alot, usually just locks up and doesn't resume :(
this happened in feisty too[/COLOR]

---

### Post by Crashmaxx on 2007-10-24
Interesting that you are getting this on UbuntuForums.org or all places. What are the neat nav effects at the top using? I thought they were flash but I don't think that's true.

Anyway, I only have this issue on some myspace pages. No surprise there.

---

### Post by SunnyRabbiera on 2007-10-24
mainly happens with compiz myself but I think i know the reasons.

---

### Post by coldguy on 2007-10-24
It never happened to me until just now when I installed gutsy on an older computer with better gfx card than my new one, to see if i could enable visual effects. It turned gray @ youtube. I have Extra visual effects enabled. Why??!!

---

### Post by coldguy on 2007-10-24
Its not just Firefox, Its happening in other apps. It just happened while I had synaptic searching for a package. Luckily it came back after 10 secs.

---

### Post by FuturePilot on 2007-10-24
It's never happened to me on these forums. Usually it happens upon leaving a page with Flash content, but that's a bug with the Flash plugin, not Firefox.

---

### Post by Crashmaxx on 2007-10-24
If you don't like, just open gconf-editor and change /apps/compiz/general/allscreens/options/ping_delay to something larger.

Beryl had an option to turn off the "Dim unresponsive windows" feature. But when they merged with Compiz it seems to have slipped through the cracks. The ping delay is how long to wait before calling something 'unresponsive'. The max is 30000, compare to the default 5000. Changing that should make it happen a lot less.

Also, its nothing 'wrong' with Compiz, the window goes unresponsive regardless. This feature just lets you know its locked up. Which I think is great because it sucks to have it sit there and wonder has it locked up or what.

---

### Post by bashveank on 2007-10-24
Happens to me whenever I visit a flash video site. Here's the weird part: I can open any number of videos, kill/restart Firefox, and they all work, but if I open another it crashes.

> 
Beryl had an option to turn off the "Dim unresponsive windows" feature. But when they merged with Compiz it seems to have slipped through the cracks

It's called "Fading Windows"

---

### Post by stryderjzw on 2007-10-24
My firefox seems to crash when I open more than 2 windows.  :confused:

---

### Post by RAV TUX on 2007-10-24
> **stryderjzw said:**
> My firefox seems to crash when I open more than 2 windows.  :confused:

Try [Opera 9.50]("http://www.opera.com/products/desktop/next/")

---

### Post by TR82 on 2007-10-24
Weird. I had the Firefox problem on Feisty too. But I'm now on Gutsy and it's my Opera browser which keeps "fading to grey" then coming alive again after a few seconds, especially on youtube/video sites or even on forums such as this. But on Monday night Opera kept doing it repeatedly so I forced a quit ... and suddenly found I had 12 workspaces instead of four & was unable to access Advanced Desktop Effects Settings (honestly, all I did was force a quit of Opera) .... result ? Opera removed and back to Firefox. And all's well *touch wood*

---

### Post by RAV TUX on 2007-10-24
> **TR82 said:**
> Weird. I had the Firefox problem on Feisty too. But I'm now on Gutsy and it's my Opera browser which keeps "fading to grey" then coming alive again after a few seconds, especially on youtube/video sites or even on forums such as this. But on Monday night Opera kept doing it repeatedly so I forced a quit ... and suddenly found I had 12 workspaces instead of four & was unable to access Advanced Desktop Effects Settings (honestly, all I did was force a quit of Opera) .... result ? Opera removed and back to Firefox. And all's well *touch wood*

I have never experienced such a problem on Opera. I just have come to expect it in Firefox.

What version of Opera did you use?

I use Opera 9.50

Also note that since I started using the latest Firefox 2.0.0.8 I have not had any issues in Firefox either, it is still not as reliable as Opera.

Firefox still hangs on opening pages especially ubuntuforums.org, where in Opera ubuntuforums.org opens instantly, consistently without fail.

---

### Post by Mr. Ksoft on 2007-10-25
This happens here too, but I'd just assumed it was being slow (since I'm running Ubuntu on an old Pentium 2, while still having full extra Compiz effects on).  Only happens when I visit this forum, but then again I haven't tried much else.

---

### Post by popch on 2007-10-25
It happens to me, too, for several applications.

It is usually a sign for an application not responding to (something?) within reasonable time. Most if not all of the applications are accessing the network when doing this.

The conclusion appears to be that a response to some request is slow in coming.

---

### Post by Polygon on 2007-10-25
it does it (the dimming of unresponding windows) for any application that is just waiting for something to be completed honestly. Ive had it happen to me with synaptic when i search for something, and its searching but the gui looks locked up while its completing the search

---

### Post by PartisanEntity on 2007-10-25
Could this have something to do with Gnash? Is it possible to remove Gnash somehow and try out other plug-ins? (I don't see Gnash in the Add ons menu)

> **RAV TUX said:**
> (Note this was on the old Firefox Version 2.0.0.6 I have since updated to Firefox 2.0.0.8...and it hasn't happen yet.)

Unfortunately it is happening with me even though I have Firefox 2.0.0.8.

---

### Post by Johan_K on 2007-10-25
I have the same problem to.  It has nothing to do with gnash. I guess it has something to do with flash and compiz and  nvidia..........

I have tried to reinstall flash without any effect.

---

### Post by PartisanEntity on 2007-10-25
> **Johan_K said:**
> I have the same problem to.  It has nothing to do with gnash. I guess it has something to do with flash and compiz and  nvidia..........

I have tried to reinstall flash without any effect.

The reason I mentioned Gnash is because it doesn't seem to be working properly anyway, youtube videos don't load for me, I just see the black box with the circle thing in the middle and nothing else.

So I thought I would get rid of Gnash and just install the normal flash plugin?

---

### Post by EdThaSlayer on 2007-10-25
Sometimes with me, the bars surrounding the window dissapears(so I can't quit the program with the nice X button), and I have to restart the whole xserver with ctrl-alt-delete.

---

### Post by mahiyar on 2007-10-25
This version of firefox whatever its called is more buggy than any other. As discussed above when a window turns grey I start praying because 50 per cent of time the FF will hang and I will have to restart FF again. Might have to do with flash, gnash or java plug in, dont know, but if this continues I will certainly give opera a try. And currently I'am even able to use FF normally in grey windows -- see pic for that.

---

### Post by Billisnice on 2007-10-25
the graying out is driving me nuts.  It seems to do it when i use flash with two windows open...Please e-mail if anyone have the solution...

thanks

[email]billisnice@gmail.com[/email]

---

### Post by waldorsockbat on 2007-10-25
Happens to me also.When I open fire fox it is the worst but it still does that periodically through surfing.I never had that until I installed 64bit gusty beta.I have gone back to 32 bit gusty and fire fox is still doing it. I am going to install opera,fire fox was great when it first came out but now its a crappy browser imho.

---

### Post by ridetheteapot on 2007-10-25
im using fiesty and have just gotten used to restarting firefox every once in awhile when i'm watching a few videos on youtube.

its definalty not cool.

does anyones firefox not have this problem?

ps i use beryl (0.3.0) too (not compizfusion cause i think it just runs way worse then beryl, but its probably just the config)

---

### Post by BigSilly on 2007-10-26
I don't think it's a bug, or an issue with Firefox. I'm using both Ubuntu 7.10 and Mandriva 2008 with Compiz Fusion and it does this when it hangs on something. It doesn't look like a bug to me anyway. It seems to be a "feature". I'm OK with it anyway.

---

### Post by Choad on 2007-10-26
> **PartisanEntity said:**
> Has anyone else experienced this behaviour in Firefox? Sometimes it will freeze and turn grey, I then have to wait for a few seconds for it to resume again.

Is this a FF or Compiz-Fusion issue?

For example, when I first start the computer and launch FF for the first time, then if I visit ubuntuforums.org and click on User CP, FF will freeze and turn grey, then resume again after a couple seconds. Once it has done it's thing it will not freeze again if I click on User CP again.
i cba to read the thread, but i know the reason for this

firefox's javascript engine is not multi-threaded. so whenever a javascript heavy page is loading, it locks up the whole app. you know what the REALLY bad news is? this isn't even fixed in firefox 3. LAME

it is one of my biggest gripes with ubuntu as a whole. firefox being a laggy mo fo

---

### Post by jenhsun on 2007-10-26
I guess it might be the problem about this new version of gnome 2.20.1. The way it handles the application.

---

### Post by Choad on 2007-10-26
> **jenhsun said:**
> I guess it might be the problem about this new version of gnome 2.20.1. The way it handles the application.
nope. read my above post. it's been like this since forever, it's just that compiz now "highlights" this fact so you notice it more

---

### Post by jenhsun on 2007-10-26
> **Choad said:**
> nope. read my above post. it's been like this since forever, it's just that compiz now "highlights" this fact so you notice it more

How do you explain popch and Polygon's problems and symptoms?
Mine is Gnome Nautilus. When doing some massive IO, I have to manual power off the system because the logout doesn't work, keyboard doesn't work (freeze).

Have you ever try multi-language input? You will know what I am talking about.

---

### Post by Choad on 2007-10-26
> **jenhsun said:**
> How do you explain popch and Polygon's problems and symptoms?
Mine is Gnome Nautilus. When doing some massive IO, I have to manual power off the system because the logout doesn't work, keyboard doesn't work (freeze).

Have you ever try multi-language input? You will know what I am talking about.
oh sorry, i thought we were just talking about firefox. i didn't read the rest of the thread :p

---

### Post by jenhsun on 2007-10-26
> **Choad said:**
> i cba to read the thread, but i know the reason for this

firefox's javascript engine is not multi-threaded. so whenever a javascript heavy page is loading, it locks up the whole app. you know what the REALLY bad news is? this isn't even fixed in firefox 3. LAME

it is one of my biggest gripes with ubuntu as a whole. firefox being a laggy mo fo

To test your theroy on javascript and threading on ubuntuforum is easy. Turn off the function in firefox and give some trying. I think we need people's feedback.

---

### Post by jenhsun on 2007-10-26
There is one that I worried about.
Do we have two different Linux Kernel version between Fesity and Gutsy? Since we have two different Gnome, how about the Kernel? I think it's difficult to trace the bug about the version difference.

---

### Post by popch on 2007-10-26
> **jenhsun said:**
> How do you explain popch and Polygon's problems and symptoms?.

I think my 'problems' are covered by Choad's explanation. 

There are just several parts to the 'problem'.

The window becoming grey. That's just eye candy, as someone here already has observed. Any window not answering the mouse or something within a reasonable time is greyed out. That's new in Gutsy, but it is just visuals.

The window failing to respond to 'mouse or something'. I am not sure how the OS decides if a window is failing to respond. I am, however, quite sure, that there are reasons for some 'windows' (applications) to do so. I assumed that this was the case when an application was waiting for some response from the network more than some arbitrarily predefined length of time. That would account both for Firefox and Synaptics. In the case of Firefox, I also find Choad's explanation plausible that rendering a page with much javascript processing could have that effect.

In none of the cases I could observe I had even the slightest reason to assume that some kernel issue or some other complicated cause was involved.

Just (a) an application fails to respond within some time limit and (b) the GUI highlights that by greying out the window.

---

### Post by jenhsun on 2007-10-26
> **popch said:**
> I think my 'problems' are covered by Choad's explanation. 

There are just several parts to the 'problem'.

The window becoming grey. That's just eye candy, as someone here already has observed. Any window not answering the mouse or something within a reasonable time is greyed out. That's new in Gutsy, but it is just visuals.

The window failing to respond to 'mouse or something'. I am not sure how the OS decides if a window is failing to respond. I am, however, quite sure, that there are reasons for some 'windows' (applications) to do so. I assumed that this was the case when an application was waiting for some response from the network more than some arbitrarily predefined length of time. That would account both for Firefox and Synaptics. In the case of Firefox, I also find Choad's explanation plausible that rendering a page with much javascript processing could have that effect.

In none of the cases I could observe I had even the slightest reason to assume that some kernel issue or some other complicated cause was involved.

Just (a) an application fails to respond within some time limit and (b) the GUI highlights that by greying out the window.

Choad's explanation of course very true in Application level. There is no argue about. But when I got so many problems and feedbacks (include myself), the new version of Gnome and Linux kernel make my doubts. That's the same feeling when people do Windows upgrading from XP to Vista....

Honestly, I never see so many performance problems in this forum because of Gutsy.

---

### Post by daynah on 2007-10-26
Get Opera. :D

For real. Check the memory usage of firefox in System Monitor. Firefox has memory leaks and, like Windows, should be shut down and started up again once a day for optimum performance. If you don't want this to happen, get Opera. Or Konqueror. Or something good.

If someone hasn't answered the problem in the COMMUNITY section of the forum after four pages, take it as proof that we here ar ejust here bumming around, probably trying to amuse ourselves at work. For better support next time, put your topic in a more appropriate forum.

---

### Post by jenhsun on 2007-10-26
> **daynah said:**
> 
If someone hasn't answered the problem in the COMMUNITY section of the forum after four pages, take it as proof that we here ar ejust here bumming around, probably trying to amuse ourselves at work. For better support next time, put your topic in a more appropriate forum.

That's why we have launchpad.net.

---

### Post by derekr44 on 2007-10-26
I tested this by loading some pretty busy pages...

Firefox 2.0.0.8 - locks up
Swiftfox 2.0.0.7 - locks up
Opera 9.50 - no locks

---

### Post by jenhsun on 2007-10-26
> **derekr44 said:**
> I tested this by loading some pretty busy pages...

Firefox 2.0.0.8 - locks up
Swiftfox 2.0.0.7 - locks up
Opera 9.50 - no locks

Could you give me your busy pages url? I would like to try. I think that would be cool to kill my app.

---

### Post by derekr44 on 2007-10-26
I specifically tried YouTube, going back and forth between different videos seemed to push it.  I originally thought that perhaps my streaming media codecs were the problem.  But then I saw it lock up on more "standard" pages.

---

### Post by LagoGuy on 2007-10-26
I also had a problem with Firefox crashing when attempting to open the 3rd window after upgrading to Gutsy. Two windows would work fine, but both Firefox windows turn gray when attempting to open the 3rd window.

Some testing suggested the problem to be the Google toolbar because the problem disappeared the moment I disabled the toolbar. After working with the Google Toolbar team, we discovered that the problem lies with the Firefox build that comes with Gutsy. The solution is to install the official Mozilla build of Firefox. I did that and my problem is fixed, i.e. I can open multiple Firefox windows with the Google Toolbar enabled.

I used Ubuntuzilla to change my Firefox over to the official build. It makes the process a breeze. I read on the Ubuntuzilla site that you shouldn't uninstall the Ubuntu edition of Firefox because that will break several Gnome packages that rely on the Gecko rendering engine. Just use the Ubuntuzilla script to install the Mozilla version without touching the Ubuntu version.

I hope this helps! :)

---

### Post by jenhsun on 2007-10-26
> **derekr44 said:**
> I specifically tried YouTube, going back and forth between different videos seemed to push it.  I originally thought that perhaps my streaming media codecs were the problem.  But then I saw it lock up on more "standard" pages.

No, I don't have that problem.
If you try youtube and get this kind of lock up problem, I think it might be your flash plugin between firefox. By the way, network streaming is an issue too.
You can try to disable your firefox ipv6 and give a try.

Here is how I improve my network collected from this forums:

1. Disable IpV6 in Firefox
About:config , find ipv6 and disable it
find network.http.pipelining.maxrequests and set to 10

2. In /etc/hosts comment out all reference to ipv6

3. Add the following to /etc/sysctl.conf (524288 could be too large, try 262144 or 131072 in place of 524288 if you don't notice an improvement. 524288 worked best for me though.):

    # Tweaks for faster broadband...
    net.core.rmem_default = 524288
    net.core.rmem_max = 524288
    net.core.wmem_default = 524288
    net.core.wmem_max = 524288
    net.ipv4.tcp_wmem = 4096 87380 524288
    net.ipv4.tcp_rmem = 4096 87380 524288
    net.ipv4.tcp_mem = 524288 524288 524288
    net.ipv4.tcp_rfc1337 = 1
    net.ipv4.ip_no_pmtu_disc = 0
    net.ipv4.tcp_sack = 1
    net.ipv4.tcp_fack = 1
    net.ipv4.tcp_window_scaling = 1
    net.ipv4.tcp_timestamps = 1
    net.ipv4.tcp_ecn = 0
    net.ipv4.route.flush = 1

    Then to have the settings take effect immediately, run:

    sudo sysctl -p

    Source:
    [http://ubuntuforums.org/showthread.php?t=251509](http://ubuntuforums.org/showthread.php?t=251509)

Or another one based on different speed

#net.core.rmem_default = 4194304
# default values seems to work fine with my system
net.core.rmem_max = 4194304
#net.core.wmem_default = 4194304
# default values seems to work fine with my system
net.core.wmem_max = 4194304
net.ipv4.tcp_wmem = 4096 87380 4194304
net.ipv4.tcp_rmem = 4096 87380 4194304
#net.ipv4.tcp_mem = 256960 256960 4194304
# this should be uncommented only if it's not working well
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

# don't cache ssthresh from previous connection
net.ipv4.tcp_no_metrics_save = 1
net.ipv4.tcp_moderate_rcvbuf = 1
# recommended to increase this for 1000 BT or higher
net.core.netdev_max_backlog = 2500
net.ipv4.tcp_congestion_control=cubic


4. Gksudo gedit /etc/modprobe.d/aliases
Find the line: alias net-pf-10 ipv6 and to:  alias net-pf-10 off

5. Try OpenDNS

---

### Post by vexorian on 2007-10-26
> **Mr. Ksoft said:**
> This happens here too, but I'd just assumed it was being slow (since I'm running Ubuntu on an old Pentium 2, while still having full extra Compiz effects on).  Only happens when I visit this forum, but then again I haven't tried much else.
Like seriously, my pentium 4 itself doesn't perform too well when compiz is enabled, using it on a pentium 2 sounds like something I would never recommend to do.

---

### Post by jenhsun on 2007-10-26
> **LagoGuy said:**
> I also had a problem with Firefox crashing when attempting to open the 3rd window after upgrading to Gutsy. Two windows would work fine, but both Firefox windows turn gray when attempting to open the 3rd window.

Some testing suggested the problem to be the Google toolbar because the problem disappeared the moment I disabled the toolbar. After working with the Google Toolbar team, we discovered that the problem lies with the Firefox build that comes with Gutsy. The solution is to install the official Mozilla build of Firefox. I did that and my problem is fixed, i.e. I can open multiple Firefox windows with the Google Toolbar enabled.

I used Ubuntuzilla to change my Firefox over to the official build. It makes the process a breeze. I read on the Ubuntuzilla site that you shouldn't uninstall the Ubuntu edition of Firefox because that will break several Gnome packages that rely on the Gecko rendering engine. Just use the Ubuntuzilla script to install the Mozilla version without touching the Ubuntu version.

I hope this helps! :)

New to me, great information.

---

### Post by mahiyar on 2007-10-26
jenshun -- can you try this site [http://www.nseindia.com](http://www.nseindia.com) Thanks in advance

---

### Post by jenhsun on 2007-10-26
> **mahiyar said:**
> jenshun -- can you try this site [http://www.nseindia.com](http://www.nseindia.com) Thanks in advance

Page is fine, the Applet is great.
Everything is fine...except I don't like J2EE architecture....ha..

---

### Post by mahiyar on 2007-10-26
I installed opera but then seeing the huge mountain to climb by way of installing plug-ins like java, flash etc I gave up. Then I used ubuntuzilla to install the original build as suggested by Lagoguy, seems to have solved the problem. Will answer definitively after further use.

---

### Post by jenhsun on 2007-10-26
> **mahiyar said:**
> I installed opera but then seeing the huge mountain to climb by way of installing plug-ins like java, flash etc I gave up. Then I used ubuntuzilla to install the original build as suggested by Lagoguy, seems to have solved the problem. Will answer definitively after further use.

Great, another Automatix liked addin software.
The more this kind of patching come-in, the more embarrassing moments ubuntu dev team will have. 
But thanks anyway.

---

### Post by maranellored on 2007-10-26
i have the same problem too.
i'm on Gutsy x86-64 version. I didnt bother with a clean install but only an upgrade from Feisty.

Firefox and Epiphany, the ones that i have freeze when i try opening a site that has flash content :(

Help please :( 
thanks in advance

---

### Post by jenhsun on 2007-10-26
> **maranellored said:**
> i have the same problem too.
i'm on Gutsy x86-64 version. I didnt bother with a clean install but only an upgrade from Feisty.

Firefox and Epiphany, the ones that i have freeze when i try opening a site that has flash content :(

Help please :( 
thanks in advance

Just download x86_64 iso and make a clean install.
Oh, sorry, backup your files first.
Here is the other thread talked about it, believe me.
[http://ubuntuforums.org/showthread.php?t=589555](http://ubuntuforums.org/showthread.php?t=589555)

---

### Post by newman on 2007-10-26
I'm having similar problems. I had Gutsy Beta installed and I did all the upgrades and it seemed to be working fine. For some reason I decided it was time to do a clean install with Gutsy final, and now I have lots of issues. Firefox freezes, and I even have more screen tearing in videos. I'm not even running desktop 3D effects. This is garbage!

---

### Post by jenhsun on 2007-10-27
> **newman said:**
> I'm having similar problems. I had Gutsy Beta installed and I did all the upgrades and it seemed to be working fine. For some reason I decided it was time to do a clean install with Gutsy final, and now I have lots of issues. Firefox freezes, and I even have more screen tearing in videos. I'm not even running desktop 3D effects. This is garbage!

Gutsy Beta?? Do you want to try the newest final one?
By the way, currently we have issue on this buggy Gutsy. You can stay on Fesity for one or two months, then download a newest iso for a clean installation could be better.
The downloadable iso version change sometimes, you can take a look at the updating date.

---

### Post by newman on 2007-10-27
Actually it wasn't Beta, it was the 7.10 RC.

---

### Post by jenhsun on 2007-10-27
> **newman said:**
> Actually it wasn't Beta, it was the 7.10 RC.

Ok then. If I were you, I will stick on Fesity for a little while.
And wait for this new kernel.
[http://kerneltrap.org/mailarchive/linux-kernel/2007/10/24/352404](http://kerneltrap.org/mailarchive/linux-kernel/2007/10/24/352404)

---

### Post by Johan_K on 2007-10-27
Opera 9.50 locks to, for example when i open up the same site in a new window. It feels a little more stable then FF but i think it depends on how Opera handles windows.

---

### Post by mahiyar on 2007-10-27
Installing FF from Ubuntuzilla seems to have solved my problem, at least there are no lock ups on my frequently visited site.

---

### Post by xyz on 2007-10-27
> **mahiyar said:**
> Installing FF from Ubuntuzilla seems to have solved my problem, at least there are no lock ups on my frequently visited site.

Yes that seems to have helped me too...so far!

---

### Post by mcook2 on 2007-10-27
I upgraded Feisty to Gutsy on AMD X64 with NVidia 6100 and 3GB RAM, and using I am happily using Custom Visual Effects with Compiz-Fusion.  My Flash was installed using Kilz' script a couple of months back, and of course I just upgraded to Firefox 2.0.0.8.  

So far, running Firefox in safe mode as mentioned above seems to make the "gray screen slowdown" problem go away for me.

I'm not sure why folks are recommending reinstalling off the CD. It seems a bit extreme, no?

---

### Post by undine on 2007-10-28
It happens to me when streaming embedded video in either Firefox or Epiphany. It doesn't matter if I use totem-mozilla, or mozilla-mplayer.

---

### Post by RAV TUX on 2007-10-28
> **mahiyar said:**
> Installing FF from Ubuntuzilla seems to have solved my problem, at least there are no lock ups on my frequently visited site.


Slightly OT: Awesome avatar! ;)

---

### Post by PartisanEntity on 2007-10-28
Quick observation, I removed GNASH and installed the Adobe Flash plugin, so far I have not had any freezes.

---

### Post by jenhsun on 2007-10-28
> **PartisanEntity said:**
> Quick observation, I removed GNASH and installed the Adobe Flash plugin, so far I have not had any freezes.

Interesting news. I think we better have more feedback about it.

---

### Post by mahiyar on 2007-10-28
News Flash -- My ubuntuzilla installed firefox again turned grey and hung, so i guess was not the original distro problem. I am turning to PartisanEntry suggest and have removed gnash.

---

### Post by Wiebelhaus on 2007-10-28
The "turning grey" is the equivalent to Winblows "Not Responding" , Gnash is causing it as well as flash video corruption , interesting thing in my case is that on the same computer upgrading the processor to 2.6 w/ HT it stopped but with the original 1.6 without HT factory processor it would do it constantly also anything flash would cause horrible system slowdowns.

---

### Post by 3zero2 on 2007-10-28
my gutsy had been running fine since release. just from yesterday firefox started to act strangely like not responding and sending CPU to 100%. 

most of the times i can manage to close it but there have been occasions where I had to resort to the reset button as not even gnome was answering my clicks.

---

### Post by MichaelBKK on 2007-10-29
I've seen this problem quite a lot today.  It seems to happen when clicking Javascript-driven links (especially pop-ups).

I don't have Gnash installed, so it's not that.  I'm looking at what java components I have, to see if there might be some conflicting versions.

---

### Post by MichaelBKK on 2007-10-29
After a rather disastrous day of trying to get anything done, I'm now convinced my problem has to do with Javascript.  Every time Firefox hangs (which is a lot) it's immediately after clicking something that executes JS.  BUT, it's not every JS click that does it.  It seems to have to do with concurrent executions.  If I click something in one tab that is JS, it proceeds to work okay, but if I switch to another tab and click another JS link, it hangs.

This only started today, after installing the Ubuntuzilla update.

---

### Post by edantes on 2007-10-31
After suffering with this off and on since installing 7.10, I switched to SwiftFox:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#SwiftFox](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#SwiftFox)

No freezes for a couple of hours, what a relief.  They are still in version 2.0.0.7, but preparing 2.0.0.9.  It installs seamlessly sharing all of Firefox configuration.  As a bonus, it really feels faster.

---

### Post by PartisanEntity on 2007-10-31
Make sure to try removing the gnash plugin for Firefox and replacing it with the adobe version. This solved the issue of hanging for me.

---

### Post by fatamos on 2007-10-31
I'd love to get FireFox working again...
I'm just starting out on Linux... could someone give me a pointer on how I would remove Gnash and install the Abode version as implied by Partisan.

Thanks in advance.

---

### Post by PartisanEntity on 2007-10-31
Open up Synaptic, search for gnash, remove it, and then search for 'flash' or 'adobe', find the adobe flash plugin and install it. That's it. Remember to restart Firefox.

---

### Post by fatamos on 2007-10-31
Nice and simple :)
I did try searching for Flash last night in Synaptic... but couldn't find it. I'll try again tonight.

---

### Post by mahiyar on 2007-10-31
Removing gnash too does not help, firefox greyed out and froze on me today again, though I think the frquency of feezing has reduced.

---

### Post by jenhsun on 2007-10-31
> **mahiyar said:**
> Removing gnash too does not help, firefox greyed out and froze on me today again, though I think the frquency of feezing has reduced.

Sorry to ask, what type of cpu you have? 32 or 64?
Some people got trouble in 64 because of AMD, not only flash but the java plugins too.
So they turn to firefox32. 
But some people like mine firefox 64 works just perfect ( only install nonfree-flash, the nsiwrapper will automatic wrap for you).
And one more thing is, check your symbolic link in your /etc/alternatives, /usr/lib/firefox and any. Make sure your link is correct.

---

### Post by mahiyar on 2007-10-31
My cpu is plain 32 one.  Checked firefox flash plugin and firefox java plugin in the /etc/alternatives directory they are all correct. Even now as I' am replying my firefox is grey (grey but working) :(

---

### Post by edantes on 2007-10-31
> **edantes said:**
> After suffering with this off and on since installing 7.10, I switched to SwiftFox:
.
 
Disavowing my own post, SwiftFox 2.0.0.7 also froze eventually.  There were two YouTube windows open, if anyone is keeping tabs.  Still working better than stock Ubuntuk FIrefox  2.0.0.8, but bug is still there, somewhere.

---

### Post by 3zero2 on 2007-11-01
i have moved back to windows. couldn't stand firefox greying oput on me all the time. it's the only application i use. as a bonus my fonts look nicer too!

---

### Post by acconrad on 2007-11-01
I can't play a single flash video without Swiftfox OR Firefox freezing.  I don't have GNASH installed, I even erased my profiles and started a new one with only the following extensions:


download statusbar, fasterfox, faviconizetab, foxytunes, gspace, greasemonkey, noscript

any ideas?  i'm running a dell latitude d800 laptop (1.6Ghz, 1GB ram, nvidia geforcefxGo 58xx graphics card)

---

### Post by CoolDreamZ on 2007-11-01
This problem happened for me when I installed the Google toolbar. I removed it and it stopped happening. It looks like a bug in Firefox to me. Non of my other applications freeze and I don't use GNASH.

---

### Post by FG123 on 2007-11-01
Firefox seems fine for me. The only time it seems to grey out is for one particular site I visit; if I'm downloading something in the background and I visit the site at the same time, the browser takes a while to respond due to low available bandwidth and hence goes grey for a few seconds. Other than that, the only other time was when I installed Flash and it had to download the plugin.

Apart from those two cases, it's flawless. Don't use Gnash; I don't care if it's open source, it's absolute rubbish.

---

### Post by PartisanEntity on 2007-11-01
I would like to recommend that some of you test Firefox without the desktop effects switchedoff too. I had a noticeable improvement in Firefox after replacing gnash with the adobe flash player, but I also turned off the desktop effects around the same time. Since then Firefox hasn't hung or greyed out on me.

---

### Post by nynoah on 2007-11-02
I just loaded the newest version of opera at this link.  I took me a little while to find it..........but it is a 64bit version of opera and it is the BOMB.......

Follow the link and download it.  My computer stopped freezing like it was when I was using firefox.  Plus it is SUPER fast.  This release is only a few days old and seems to work great.  All my plugins work without having to configure anything.  SO far........LOL

Download the Deb file and have fun.

[ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/](ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/)

---

### Post by Velociraptor on 2007-11-03
I found a fix in [another thread]("http://ubuntuforums.org/showthread.php?t=584954&page=2") , which worked for me. :)

> 
I found that I had an old copy of npwrapper.libflashplayer.so in /usr/lib/firefox/plugins. I deleted this file and the problem seems to have been solved.

I think if I had done a fresh install of gutsy, rather than an upgrade, I wouldn't have had this problem.

---

### Post by giuliastro on 2007-11-04
[LIST]
[*]I don't have gnash
[*]I don't have npwrapper.libflashplayer.so
[*]I tried disabling compiz
[*]I tried disabling all firefox plugins
[/LIST]

The problem is still there, **firefox** is very very unstable in Gutsy. Actually it doesn't seem a flash problem more like a javascript problem. **Epiphany** seems to soffer of the same problem.

I think this is a major issue.

---

### Post by fineas on 2007-11-04
Same problem in Opera 9.24

---

### Post by bionnaki on 2007-11-04
I had this problem with firefox. It only would happen on the main page of ubuntuforums - no other website, really. I installed this plugin: [https://addons.mozilla.org/en-US/firefox/addon/4922](https://addons.mozilla.org/en-US/firefox/addon/4922) - basically, it blacklists javascript on whatever page you want. I block ubuntuforums and I dont have this problem anymore.

so, I think the problem is whatever javascript ubuntuforums uses - maybe firefox cant handle it, or maybe the javascript is real buggy. either way, I block it and I dont have a problem anymore.

---

### Post by bionnaki on 2007-11-04
I also blocked google-analytics.com in my hosts file because loading ubuntuforums connects with them and it also seems to take awhile...

sudo nano /etc/hosts

add 
0.0.0.0 [www.google-analytics.com](www.google-analytics.com)
to the top of the file

and reboot (or not)

---

### Post by giuliastro on 2007-11-05
Opera 9.5 doesn't seem to solve my problems. Actually they get a lot worse, 9.5 beta seems quite buggy too.

---

### Post by Colonel Kilkenny on 2007-11-05
> **giuliastro said:**
> Opera 9.5 doesn't seem to solve my problems. Actually they get a lot worse, 9.5 beta seems quite buggy too.

Maybe you should start applications from terminal and see what is the output when crash occurs. I think you have a problem with your system / OS, not in applications.

---

### Post by smartbei on 2007-11-05
This happens to me with and without Compiz, though it seems to happen more often when Compiz is on.

To BigSilly: Of course the graying of the window isn't a bug - The fact that the window needed graying in the first place is the bug!

---

### Post by caver1 on 2007-11-05
I was having the window turn grey and freezing in more than FF. It also 
grayed and froze the desktop,Streamtuner and a couple of others.
I finally tried lowering my screen refresh rate. It seems to have worked. No freezes the last couple of days.    :)
caver1

---

### Post by bnsrinivas on 2007-11-05
Same Thing and Same dam old bug.Ever since I laid my hand on Gutsy release candidate and 7.10 final I'am having this problem.Even some times My screen freezes and I'am left with no option but to restart.


PLEASE PEOPLE(community guys) IF ALL OF US WANT TO BEAT MICROSOFT THEN SUCH THINGS HAS TO BE SORTED OUT QUICKLY

**OR ELSE**
 
PEOPLE MIGHT THINK that UBUNTU IS A OS FILLED WITH BUGS(||ar to VISTA)

---

### Post by popch on 2007-11-05
> **bnsrinivas said:**
> IF ALL OF US WANT TO BEAT MICROSOFT 

I don't want no such thing. What do you do with a beaten smallest softest thing?

---

### Post by juzzblack on 2007-11-06
If you're having trouble with other apps becoming unresponsive when playing other media besides Youtube on Firefox (such as playing video or flash files in Totem or music files in Rhythmbox) I think it may be some sort of multimedia codec problem. Especially if you have 'jackd' installed. Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=599939](http://ubuntuforums.org/showthread.php?t=599939)

It may be related and of some use to peoples problems here.

---

### Post by kopinux on 2007-11-06
my observation is when its loading something and lags, a large pdf, flash. it will return back to normal after the objects has been loaded.

---

### Post by professor fate on 2007-11-06
I'm still having a heck of time with this.  Sometimes FF will turn gray for a few seconds and come back to life, and other times it's a full on freeze and I have to get into the system monitor and kill FF.  I understand that some people un-installed gnash and it resolved the problem.  I never installed it though.  I wish I could find some sort of pattern.  Sometimes it happens watching the news or Youtube, and other times it can happen just opening email.  

I'm also having issues with Mplayer and streaming audio.  That's another issue probably not related to this though.

---

### Post by caver1 on 2007-11-06
Update.
Since I lowered my refresh rate no lockups,but when I went into Synaptic it turned gray for about 3 seconds and came back to life.
caver1

---

### Post by professor fate on 2007-11-06
Did you have your refresh rate higher than normal to begin with?

---

### Post by PartisanEntity on 2007-11-07
> **professor fate said:**
> I'm still having a heck of time with this.  Sometimes FF will turn gray for a few seconds and come back to life, and other times it's a full on freeze and I have to get into the system monitor and kill FF.  I understand that some people un-installed gnash and it resolved the problem.  I never installed it though.  I wish I could find some sort of pattern.  Sometimes it happens watching the news or Youtube, and other times it can happen just opening email.  

I'm also having issues with Mplayer and streaming audio.  That's another issue probably not related to this though.

Do you have Compiz turned on? Try turning it off and see it if helps.

---

### Post by nrune on 2007-11-07
I have been having issues with ff and freezing and out right crashing.  I installed oprea, fell in love and probably won't go back.

---

### Post by marinos on 2007-11-07
IMO it's definitely a javascript problem, probably exarcebated by
other factors too.  My standard practice since time immemorial
is whenever I visit a news site (e.g., Digg) to open up in advance 
some 10 ~ 20 new tabs with the fresh news (by clicking the
middle-button, aka wheel, on the article's URL on the first Digg
page) and then, when done checking unread news, i'll start 
reading the contents of each tab.  

This has been going on forever without any problem (even under
FF in Windows XP until last May when I converted), until recently 
upon upgrading to Gutsy.  Then the CPU load will most of the time 
shoot through the roof while the new tabs are being loaded and all 
too often the entire Ff will grey-out as witnessed by other users, 
and after some time it normally manages to recover.
Note that I have the CPU monitor permanently running on 
the tray, so I know when it gets high.  This poblem was never 
manifested under Feisty (with Beryl.)

It _is_ a major issue, given that most of us, users, spend the
major part of computer use browsing.  Unless they fix it ASAP 
it's going to give Ubuntu a bad name.  

In the mean time, even though the all-new FF 2.0.0.9 has been 
out for almost a week now, it's still not visible in Synaptic.  
Let's all hope that the reason is the Ubuntu people are giving it 
a thorough check before making t available to us, as to make 
sure that this greying-out problem is resolved

---

### Post by nieknl on 2007-11-07
jep problem here to. switched to opera in despair liking it so far though, still miss certain addons but il figure that out. 

My ff would crash and lock every couple of minutes .. Mostly when having lot of active windows open with: java applets.. id vote for the javascript problem to. But specifically with FF as running the same sites with java on (slightly more of a hassle in opera but no biggie)i have no problems what so ever.

---

### Post by xpod on 2007-11-07
Weird.......i had the same kinda issues with Firefox too but i actually began using using Opera full time about 6 weeks ago now and it had never been a problem....till now
Cant ever recall Opera having greyed out like so but after just upgrading to  9.50 it`s only went and done it too....sods law eh.

[ATTACH]49400[/ATTACH]
I was trying to connect to Windows live mail from speed dial and had to restart Opera just to get it going again.
I then got some error kind of error about newsgroups(?)which, i had just been subscribing to so mabey my particular problem was just a self inflicted coincidence:)

---

### Post by professor fate on 2007-11-07
> **PartisanEntity said:**
> Do you have Compiz turned on? Try turning it off and see it if helps.

I can try that.  It would be a bummer if that were the cause though.  Scale has become my third arm; the best feature in an OS since peanut butter and chocolate got together.

---

### Post by DemiG0D on 2007-11-07
I have the same problem, Firefox keeps giving me the grey screen and hangs up on me.  It happens every time I open a new firefox window or tab, and it happens for random websites (sometimes it'll work fine, and other times it'll hang up). And no, it is not because they are java intense, websites like google will hang up on me, especially on a search.  I've searched up and down for anything remotely useful.  It occurs enough that I've been thinking about reinstalling windows :/ 

I'm going to give opera a shot first.  Hopefully something useful will come up for ff that fixes the issue.

---

### Post by lbelloq on 2007-11-08
In my case it happens randomly. At first I  thought it had something to do with the Adobe Flash Player (it happened when browsing YouTube), but it started to happen with other pages in a random basis. Sometimes, even if the window is greyed, I can still use Firefox normally; sometimes it crashes my system.

---

### Post by caver1 on 2007-11-08
> **professor fate said:**
> Did you have your refresh rate higher than normal to begin with?

Not any higher than I did in Fiesty with no problems but it was a little high.
I just posted this to show that there are other things that caused this.
Give it a try won't hurt. First thing I thought of was Video causes.
Haven't had it happen again since.   :)
caver1

---

### Post by mahiyar on 2007-11-08
Taking out compiz-fusion also does not help.

---

### Post by BobCFC on 2007-11-08
I've been getting the grey outs too.  Seems like a threading issue because it doesn't affect other applications.  Also happens to nautilus sometimes when I access a new drive for the first time.. such as an external usb.

Sorry if this has been suggested before... have you tried the new Flock browser?  It's built on firefox.  I've been using for a few days now no pauses so far. (It's better anyway lol)


Also using compiz fusion, 64bit gutsy and nvidia 100.14.19 proprietary drivers from the website

---

### Post by bruce89 on 2007-11-08
[Epiphany]("apt:epiphany-browser"), despite it using Gecko too, I've had no issues with it.

---

### Post by thirdlibrea on 2007-11-09
I experienced this stall many many times after a fresh install of Gutsy -- not just with Firefox but with most anything (even using terminal).

I followed many of the tweaks on this thread, but it seems that disabling ipv6 support did the trick. See #4 below.

I have not experienced the random stalls/freezes since then. Thanks to all

> **jenhsun said:**
> No, I don't have that problem.
If you try youtube and get this kind of lock up problem, I think it might be your flash plugin between firefox. By the way, network streaming is an issue too.
You can try to disable your firefox ipv6 and give a try.

Here is how I improve my network collected from this forums:

1. Disable IpV6 in Firefox
About:config , find ipv6 and disable it
find network.http.pipelining.maxrequests and set to 10

2. In /etc/hosts comment out all reference to ipv6

3. Add the following to /etc/sysctl.conf (524288 could be too large, try 262144 or 131072 in place of 524288 if you don't notice an improvement. 524288 worked best for me though.):

    # Tweaks for faster broadband...
    net.core.rmem_default = 524288
    net.core.rmem_max = 524288
    net.core.wmem_default = 524288
    net.core.wmem_max = 524288
    net.ipv4.tcp_wmem = 4096 87380 524288
    net.ipv4.tcp_rmem = 4096 87380 524288
    net.ipv4.tcp_mem = 524288 524288 524288
    net.ipv4.tcp_rfc1337 = 1
    net.ipv4.ip_no_pmtu_disc = 0
    net.ipv4.tcp_sack = 1
    net.ipv4.tcp_fack = 1
    net.ipv4.tcp_window_scaling = 1
    net.ipv4.tcp_timestamps = 1
    net.ipv4.tcp_ecn = 0
    net.ipv4.route.flush = 1

    Then to have the settings take effect immediately, run:

    sudo sysctl -p

    Source:
    [http://ubuntuforums.org/showthread.php?t=251509](http://ubuntuforums.org/showthread.php?t=251509)

Or another one based on different speed

#net.core.rmem_default = 4194304
# default values seems to work fine with my system
net.core.rmem_max = 4194304
#net.core.wmem_default = 4194304
# default values seems to work fine with my system
net.core.wmem_max = 4194304
net.ipv4.tcp_wmem = 4096 87380 4194304
net.ipv4.tcp_rmem = 4096 87380 4194304
#net.ipv4.tcp_mem = 256960 256960 4194304
# this should be uncommented only if it's not working well
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

# don't cache ssthresh from previous connection
net.ipv4.tcp_no_metrics_save = 1
net.ipv4.tcp_moderate_rcvbuf = 1
# recommended to increase this for 1000 BT or higher
net.core.netdev_max_backlog = 2500
net.ipv4.tcp_congestion_control=cubic


4. Gksudo gedit /etc/modprobe.d/aliases
Find the line: alias net-pf-10 ipv6 and to:  alias net-pf-10 off

5. Try OpenDNS

---

### Post by lbelloq on 2007-11-10
I tried disabling Desktop effects, and narrowed a bit the problem. It ALWAYS happens when a Flash control is loaded on a web page, most frequently in Youtube. Sometimes can take hours with the browser OK, or a few seconds, but always crashes if a Flash applet/video/etc is loaded. No Flash loaded=stable browser.
BTW, I'm using flashplugin-nonfree.

---

### Post by K.Mandla on 2007-11-10
Shifted to General Help. :)

---

### Post by jflaker on 2007-11-10
> **lbelloq said:**
> In my case it happens randomly. At first I  thought it had something to do with the Adobe Flash Player (it happened when browsing YouTube), but it started to happen with other pages in a random basis. Sometimes, even if the window is greyed, I can still use Firefox normally; sometimes it crashes my system.

May be a note to show the F Fox team....but it seems to happen to me IF it hit a link while the page is still loading.......If I wait for the page, I've been able to bypass any freezing.

---

### Post by mahiyar on 2007-11-11
Good News. This problem seems to have gone away with version FF version 2.0.0.9. However thats not the current version in repos.

---

### Post by giuliastro on 2007-11-12
I really hope it is solved with 2.0.0.9 version of Firefox. If it is I consider this one of the biggest bugs in Firefox ever. On the other hand I am waiting for 2.0.0.9 to hit Ubuntu's repos since as somebody stated browsing is one of the main activities people do with an OS. This could (and did) prevent people from coming to the Linux and Ubuntu wonderful world, too bad it happened right on Gutsy release.

---

### Post by Johan_K on 2007-11-13
> **giuliastro said:**
> I really hope it is solved with 2.0.0.9 version of Firefox. If it is I consider this one of the biggest bugs in Firefox ever. On the other hand I am waiting for 2.0.0.9 to hit Ubuntu's repos since as somebody stated browsing is one of the main activities people do with an OS. This could (and did) prevent people from coming to the Linux and Ubuntu wonderful world, too bad it happened right on Gutsy release.

Yes, I can confirm that 2.0.0.9 fixes the problem:guitar::guitar:

---

### Post by bishop9226 on 2007-11-13
i love how you guys try to blame this on firefox.  ITS A GUTSY PROBLEM. ANY GOOD OS TAKES CARE OF ITS COMPATIBILITY ISSUES BEFORE RELEASE!!!!  I *NEVER* had this problem in feisty but now i have it in gutsy, so therefore it is a GUTSY PROBLEM.  im using gutsy on my laptop now and dont have the hangup issue but on my amd gutsy box i am freezing as soon as i open up a firefox browser.

you cant win over anyone if you dont address the issues, you cant just tell people "wait for the new firefox"

---

### Post by marinos on 2007-11-14
to bishop9226:

It is natural that people blame FF given that browsing is the major
activity of most users on a daily basis, so the FF grey-outs are
manifested all too often..  I'll agree with you though that FF is not
the culprit (e..g., right now I'm using the synaptic-installed FF 2.0.0.8 
on Feisty without  any problems whatsoever), as grey-outs are manifested 
in other applications as well.  E.g., I'e had Nautilus windows grey-out quite
often in Gutsy, although for much shorter duration.  Another irritation
was that whenever Gutsy Nautilus would visit a FAT32 folder it would 
pause for some time, as if it were trying to decide what to do with it :)
In general, the Gutsy experience has been rather crippling for 
a substantial percentage of the users that upgraded to it.  It simply 
makes no sense trying to put up with such chores and keeping one's 
fingers crossed all the time lest some ******* application locks up, 
esp. as under Feisty (at least for me) the problems were pretty much zero. 
  It seems Gutsy was inadequatelly tested before release.  What's the point 
in having new goodies if stability takes a hike?  Personally, I've reverted back 
to (fully updated) Feisty until these Gutsy issues are resolved.

---

### Post by mahiyar on 2007-11-14
As an end user I am least bothered whose problem it is, as long as it gets solved.

---

### Post by giuliastro on 2007-11-19
Anyway I can confirm Firefox 2.0.0.9 is NOT the solution to this problem, as I tested it but still Firefox seems to have the same problem.

---

### Post by pjssilva on 2007-11-19
I may have found a workaround :-) :

1) Install pulseaudio-esound-compat and libpulse0.

2) Install the libflashsupport package from this site:

[http://blog.paulbetts.org/index.php/2007/06/08/native-pulseaudio-with-flash-9-fix-video-crashes](http://blog.paulbetts.org/index.php/2007/06/08/native-pulseaudio-with-flash-9-fix-video-crashes)

3) Logout and login again.

Can more people test this?

Obs: I have not checked the source code of the paulbetts package, use it at your own risk.
Obs2: The workaround may not need the libpulse0 package above...

---

### Post by m.brinkers on 2007-11-20
I experience(d?) this problem of greying out as well. At first I thought it was caused by the flash player but I now suspect the Firefox Google addon. I have had no grey-outs since I disabled the Google addon. Could you try to disable the Google addon and see whether it helps?

It seems that others have reported similar problems like this related to the Google addon

---

### Post by pjssilva on 2007-11-20
If I turn off google addons and uninstall pulseaudio packages cited above, I still get freezes while playing flash video. 

The fix using pulseaudio still seems to work flawlessly here.

---

### Post by mahiyar on 2007-11-20
The greying screen effect will not come on every site it mostly comes on flash which has a streaming media content like stock ticker etc.

---

### Post by pjalegria on 2007-11-20
I think the problem is Compiz...

---

### Post by pjssilva on 2007-11-20
A follow up to my workaround based on pulseaudio. It works, however pulseaudio does not play well with some applications I need: most notably ekiga and gizmo.  I have them uninstalled all pulseaudio packages and reverted back to pure alsa. In the mean time.

 I have decided to install the esound package and for some weird reason I haven't had problems with flash video anymore. 

I am not sure if the reason is the esound package or if the process of installing and uninstalling many pulseaudio packages together with the fiddling to make them work with different audio applications left some change in my sound system that solved, by now, my problems with flash video.

If I have problems with flash video again, I'll document them here.

---

### Post by BobCFC on 2007-11-22
Scrub what I said earlier the problem happens in Flock too now.  (A new browser based on firefox)

It's like the pause you get when you wake up a hard disk, an i/o stall, but it only seems to affect one thread other applications are fine.   

I think I read that multiple instances of Firefox still use one process that is why when you close one crashed window all of your Firefoxes die at the same time.

As I said before nautilus is another culprit.

---

### Post by justinclark on 2007-11-23
Ive been having this issue as well with all my web browsers.  ANyone find a fix yet?

---

### Post by hidey on 2007-11-23
Yeah, I've get the grey-out with pretty much any page with flash on it (usually comes back around, but it takes a while). Funny thing I noticed was that after installing the Adobe plugin (through Synaptic) and opening up FF, flash pages worked just fine...until I closed FF and started it up again, which gets me back to square one.

I have non of the other gray outs reported here so I think it's a flash thing.

---

### Post by m.brinkers on 2007-11-23
Since I uninstalled the Google addon I haven't had a grey-out again. Flash is working flawlessly.

---

### Post by hidey on 2007-11-24
Okay, mine seems to work now. The trick was to delete "npwrapper.libflashplayer.so" from absolutely everywhere. I found one from /home/username/.mozilla/plugins/ as well as from all the lib directories (/usr/lib/mozilla/plugins/ and /usr/lib/firefox/plugins) someone mentioned already.

---

### Post by mahiyar on 2007-11-24
I feel it could be a combination of factors. Even Opera quits suddenly on me, without greying out etc. However in my case the problem has been mitigated to a huge extent by installing FF 2.0.09 same might not be the case with others.

---

### Post by RgnKjnVA on 2007-11-25
I'm running 2.0.0.8 and FF freezes/grays out even if there is NO page loaded. It happens so frequently while browsing that FF is unusable. I've installed Opera. Although I'm not thrilled with some usability aspects of 'the O' I have to admit it hasn't grayed out at all in two days. Guess I'll have to get used to a new browser until a fix for FF is found.  This sucks.

Update: Installed 2.0.0.9 but got faded window within a few minutes of browsing, 3 tabs open including this forum.

Update 2: Just got recurring faded window and general slowness in Opera 9.24 *sigh* again with 3 tabs though I didn't have the forum open this time but had a news site open instead along with myspace and an NFL team forum. Definitely fewer fade outs but still occurs in Opera. =o /

---

### Post by BigHairyTroll on 2007-11-26
Hey I have it as well.
Actually I have to use my Windows computer to post this as my Ubuntu one is still trying to find its way!Besides once it started freezing, other programs do as well - so maybe it isn't Firefox after all?
Thanks

---

### Post by BigHairyTroll on 2007-11-26
Actually, to qualify a little further my previous post, I just installed Samba and set up my stuff as a file server with automatic reconnection to Windows shares for auto backup at night.
Could this have an effect?
(Network activity is very low between these comp-uters - or it should be at least - how do I monitor that?)

Thanks

---

### Post by m.brinkers on 2007-11-26
> **BigHairyTroll said:**
> Actually, to qualify a little further my previous post, I just installed Samba and set up my stuff as a file server with automatic reconnection to Windows shares for auto backup at night.
Could this have an effect?
(Network activity is very low between these comp-uters - or it should be at least - how do I monitor that?)

Thanks

Does your Ubuntu crash when you copy a lot of file over the SMB share?

---

### Post by giuliastro on 2007-11-26
How long does your Firefox stay in this "freeze" state? When it happens to me the browser freezer for a couple minutes and then works again. It happens quite often, started when I upgraded to Gutsy. I never had these problems in Dapper, Edgy or Feisty.

---

### Post by brjoon1021 on 2007-11-26
Oh yeah... I am so glad to find this thread. I have been trying to figure out what is going on. It is Firefox, it turns grey and locks up, but will not always lock everything up. If it helps at all, Swiftfox 2.0.9 does it too. I added and removed Fasterfox plugin on both, same problem persists.

---

### Post by sX_ on 2007-11-26
After gutsy installation I had the same problem. But I started FF in safe mode and freezing disappeared. So i think the reason is one addons(i have googlebar, tiny meny and russian hotkeys bugfix).

---

### Post by m.brinkers on 2007-11-26
> **sX_ said:**
> After gutsy installation I had the same problem. But I started FF in safe mode and freezing disappeared. So i think the reason is one addons(i have googlebar, tiny meny and russian hotkeys bugfix).

Disabling the Google addon fixed the freezing for me.

---

### Post by Ubuntu Warrior on 2007-11-26
We are having the same problems in Gutsy - never experienced grey screening in Feisty, Edgy or Dapper (any previous version for that matter).The problems occur when we have network congestion i.e. our file server is not serving Samba sessions fast enough. We share our home drives for Ubuntu Linux desktops via NFS to the network server (which is also the master browser) and when congestion kicks in it seems to affect the users NFS connections so much that they cannot use FF, OOo, etc. App config files are on these nfs shares (/home/user drives). Today we experienced grey-screening problems and rebooting the network server sorted the issues out. Causing major disruption to our userbase - may have to consider moving /home directories back to local disks off the network.

---

### Post by cresny on 2007-11-26
After reprucing the gray-out repeatedly on a particular page sequence, I disabled the Google toolbar and was able to get through, and has been working fine since.

Is anyone experiencing gray-outs WITHOUT the Google toolbar? I suspect this is something the toolbaruses that is broken in Gutsy, not the toolbar itself.

---

### Post by RgnKjnVA on 2007-11-26
What are you guys calling the Google Toolbar? Is it an extension you've added? If you mean the search bar (Google by default) situated to the right of the url bar in the default toolbar configuration, I remove that item from my toolbar but experience the problem.

---

### Post by Johan_K on 2007-11-27
I updated to FF 2.0.0.10 through the Ubuntu update but Firefox still freezes. But when i run FF a "original" version who i have downloaded from the Firefox site everything works fine.:confused:

---

### Post by blanc11 on 2007-11-27
I have experienced the same problem without any add-ons. I mainly get it when navigating away from a page with flash in it. This is really strange and its getting annoying.

---

### Post by Znort_Ubern00b on 2007-11-27
I get this problem too...i am using feisty...only started happening recently...could almost say since i installed compiz. don't know if it happens when not running compiz as can't remember when it has done it, only since i installed compiz...

---

### Post by brjoon1021 on 2007-11-27
I am having the problem without a google toolbar with both Firefox and Swiftfox. There are at least two threads of over 10 pages in length about this problem. Doesn't anyone other than the people with the problems read the threads around here? Isn't there any way to let the people who make this stuff know that it is borked? My browsers crash every couple of minutes. We all have different hardware, different things enabled, etc... either Gutsy has a big problem or the ubuntu FF (but I doubt this because Swiftfox crashes too) !

If you have been around here long enough to know where to send bugs, please send this one. Just do a Forum search for "Firefox crashes" and you will find another thread (at least) about this same problem. Someone other than us with the problem needs to know about it. Windows 98 is a better experience than this !

---

### Post by PartisanEntity on 2007-11-27
> **brjoon1021 said:**
> I am having the problem without a google toolbar with both Firefox and Swiftfox. There are at least two threads of over 10 pages in length about this problem. Doesn't anyone other than the people with the problems read the threads around here? Isn't there any way to let the people who make this stuff know that it is borked? My browsers crash every couple of minutes. We all have different hardware, different things enabled, etc... either Gutsy has a big problem or the ubuntu FF (but I doubt this because Swiftfox crashes too) !

If you have been around here long enough to know where to send bugs, please send this one. Just do a Forum search for "Firefox crashes" and you will find another thread (at least) about this same problem. Someone other than us with the problem needs to know about it. Windows 98 is a better experience than this !

The proper way to let the 'people who make this stuff' know is to head over to [https://launchpad.net/](https://launchpad.net/) sign up, search to make sure your bug has not already been reported and to report it.

If it has already been reported then add any info you feel might help.

The 'people who make this stuff' don't have time to search thousands of threads or websites looking for bugs. An organised and centralised method of reporting bugs is in place at the site I mentioned.

---

### Post by rax_m on 2007-11-27
I haven't read the rest of this forum, but I noticed that firefox sometimes turns grey but is STILL responsive. 
This is almost always reproducible if you switch themes while firefox is open. 

However, I have also had it turn grey and be unresponsive.. but that tends to happen when I try and change pages in the middle of a video (like youtube) loading.

---

### Post by rax_m on 2007-11-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/172419](https://bugs.launchpad.net/ubuntu/+bug/172419) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have posted a bug report at launchpad.net 
If you feel your issue is related please add to it. 

Cheers
Rax

---

### Post by Dreamy1 on 2007-11-27
I think it could be a JavaScript causing problems (some webpages may have faulty JavaScripts) or it could be Firefox hogging the CPU, whatever the heck it is, I have switched to Opera.

---

### Post by brjoon1021 on 2007-11-27
rax-m,

the bug you reported sounds like what is happening to me. From here what do we do ? How do we know when it has been fixed ?

---

### Post by brjoon1021 on 2007-11-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/172419](https://bugs.launchpad.net/ubuntu/+bug/172419) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have been getting the crashes with: Firefox 2.0.6 and 2.0.9 and 2.0.10 and Swiftfox 2.0.9.

I only have Tab Mix Plus, Fasterfox (crashes with and without this extension) added on to FF. The crashes seem to happen when multiple tabs are open, but I can't say that it has not happened with only one tab open. [www.yahoo.com](www.yahoo.com) will crash both browsers  almost every time.

---

### Post by aerorahul on 2007-11-27
The problem is with Gnash, the inherent Flash player for Firefox supplied in Gutsy. Remove Gnash and Firefox will not freeze, ever. Use Adobe Flash player 9 instead.

---

### Post by RgnKjnVA on 2007-11-27
it's already been established that people that aren't running Gnash, like me, can still experience the problem. 

However, I switched from Compiz to Metacity and have been browsing in Firefox for over an hour now without a single unresponsive event. Can others try this and report results?

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)
If you want to stop Compiz and start the old window manager (metacity or kwin), just press Alt+F2 and put in the following for Ubuntu "metacity --replace"

---

### Post by rax_m on 2007-11-28
brjoon .. I guess the best thing would be to subscribe to the bug on launchpad so that you can see what updates occur. That way if the dev asks any questions one of us can respond. 
BTW I have the following addons running : 
Noscript, Adblock plus, Hit a hint, Flashgot and the ubufox (which seems to be new with gutsy). 

RgnKjnVA  - I have compiz running too.. I will disable and check if it changes anything. 

I must admit I don't have this issue all the time, it just seems to pop up randomly.. i may go for hours without any issues.

---

### Post by brjoon1021 on 2007-11-28
In the meantime, I installed Opera which I despise in Linux because it won't do ANYTHING multimedia without a lot of  messing around. No Mplayer, No VLC or Real Plugin. This is not working for me.

So, I want to uninstall everything Flash related that is currently installed via synaptic or apt. What should I remove? I see an Adobe Flash Player and a Macromedia Flash Plugin (I may have those companies reversed, but you get the idea). I think that if I uninstall those and reinstall Swiftfox which begins with the vanilla version of Firefox, I can then reinstall the vanilla version of Flash player plugin when promped to by youtube or Yahoo.com

My theory at this point is that the Ubuntu Firefox is messed up or the Ubuntu Flash apps are messed up. As I see FF and the Flash apps in Ubuntu's repo, it looks like they are modified versions ?  I am running the very same revisions of FF and Flash and Swiftfox on other distros with never a problem. I am typing this from PCLOS because Ubuntu's FF crashes every couple of minutes.

Let me know if you think that there might be any merit in my theory before I proceed and possible make things worse, please. Especially, if you know the best way for me to go about this. I added the Swiftfox repo to synaptic so installing it is easy. I also have medibuntu and multiverse enabled.

B.

---

### Post by Johan_K on 2007-11-30
I have downloaded the original Firefox from firefox.org.  I have no grey outs and system freezes at all. 

I have lost confidence in Unbutu and i am gonna switch to Fedora. I have been an Ubuntu user for the last 2 years. But this is enough.......

---

### Post by brjoon1021 on 2007-11-30
I completely uninstalled the Ubuntu Firefox and the Ubuntu Flash packages. I then installed swiftfox and the browser will not even stay open long enough to finish typing in [www.yahoo.com](www.yahoo.com) before it dies. I have had it too.

I am to the point that I am tired of trying to use Linux. One way or the other it consistently pisses me off. Whether I am using PCLInuxOS, Sabayon, Ubuntu, Vector, Mandriva, OpenSuSe, you name it. Each time I boot into Windows XP I am reminded that it is better than any of the Linuxes that I have. This is a really strong reminder right here. The one browser supplied with the OS crashes all of the damn time. Opera, the only sort of full featured alternative sucks beyond the telling of it in Linux as it will play NOTHING AT ALL from a website. So, I guess it is time to wipe the two remaining Linux partitions that remain from the nearly 30 that I was multibooting about 6 months ago and stick to Windows until Linux gets better.

---

### Post by Johan_K on 2007-12-01
OK, i found this:

[http://groups.google.com/group/FFToolbar-Group-Bugs/browse_thread/thread/03c694a05d2752f9](http://groups.google.com/group/FFToolbar-Group-Bugs/browse_thread/thread/03c694a05d2752f9)

"I had exactly the same symptoms with Firefox after upgrading to Ubuntu
Gutsy Gibbon, i.e. Firefox would crash when attempting to open the 3rd
window.

It also pointed to the Google toolbar because the problem disappeared
the moment I disabled the toolbar. After working with the Google
Toolbar team, we discovered that the problem lies with the Firefox
build that comes with Ubuntu Gutsy Gibbon. The solution is to install
the official Mozilla build of Firefox. I did that and my problem is
fixed, i.e. I can open multiple Firefox windows with the Google
Toolbar enabled.

I used Ubuntuzilla to change my Firefox over to the official build. It
makes the process a breeze. I read on the Ubuntuzilla site that you
shouldn't uninstall the Ubuntu edition of Firefox because that will
break several Gnome packages that rely on the Gecko rendering engine.
Just use the Ubuntuzilla script to install the Mozilla version without
touching the Ubuntu version.

I hope this helps!

LagoGuy

It helps to install Firefox from Ubuntuzilla. Why do the Ubuntu team not fixing the bug????

---

### Post by mahiyar on 2007-12-01
There is basically no major difference between FF from repos and the original version, except that in the original version releases can be installed earlier if from Ubuntuzilla. I have FF installed from Ubuntuzilla, though the problem is less in frequency, but yet not completely gone.

---

### Post by brjoon1021 on 2007-12-01
I deleted Ubuntu and installed Mint in its place because I could not take this anymore. It does the exact same thing. PCLOS runs like a charm with the same versions of FF. Geez.

---

### Post by konradsa on 2007-12-02
Ok, I think I found a workaround in another forum that works for me. Could anybody confirm this please?

The problem seems to be related to Compiz. When I push Alt + F2 and type in "metacity --replace", my troubles seem to go away.

Can anybody confirm that?

---

### Post by BobCFC on 2007-12-02
I agree think we are too hung up on Firefox here, myself and others have seen the same thing with the nautilus file manager, so it is something more fundamental.   Tracker perhaps?  Something that changed between gutsy and feisty.

edit:  anyone running kde have the grey-out problem?

---

### Post by Caffeine_Junky on 2007-12-02
i'm not using Ubuntu at the moment, but from my experience  the "greying out/freeze" that occures in Gutsy can be a "ping_delay" issue related to Compiz-Fusion..

Open **Gconf-Editor** (if it is not in your **Applications Menu**  under **System Tools**, you can add it to your menu by right-clicking **Applications** then  **Edit Menu's** and have a look for it in the **Menu editor**, it is in there somewhere, ..It has a [COLOR="Red"]RED[/COLOR] icon, ..so just click on the Categories in the Left Column & eventually you will see it appear in the Right Column..

Ok, open the Gconf-Editor, then go to:
apps > compiz > general > allscreens > options /ping_delay , and change the value to something **higher**. (eg: 6000, 7000, 8000 etc)

To see the range in which you have to work,  Highlight **ping_delay** and look in the description window at the bottom..

cheers

(Configuration Editor Screenshot)

---

### Post by konradsa on 2007-12-02
> i'm not using Ubuntu at the moment, but from my experience the "greying out/freeze" that occures in Gutsy can be a "ping_delay" issue related to Compiz-Fusion..

Ok. this kind of confirms my observation voiced above that it could be related to compiz, since the problem seem to not exist using metacity. I think we are pinpointing the problem now.

Do you have any idea what value we should try for "ping_delay"? Higher or lower?

---

### Post by Caffeine_Junky on 2007-12-02
> **konradsa said:**
> Ok. this kind of confirms my observation voiced above that it could be related to compiz, since the problem seem to not exist using metacity. I think we are pinpointing the problem now.

Do you have any idea what value we should try for "ping_delay"? Higher or lower?

The value will have to be set **Higher** in order to give applications more time to respond..

I would just increase the value by 1000 at a time, and see if that resolves the issue.  If not, increase it again

---

### Post by brjoon1021 on 2007-12-02
I switched to Mint. The exact same thing is happening. It uses Meta City does it not ?

---

### Post by brjoon1021 on 2007-12-02
After loving the fact that Mint was doing the exact same thing and no one at that forum had heard about it I  decided to reinstall Ubuntu but to take things REALLY slow and see how far I can go from the vanilla installation before things break again.

Well... I installed Gutsy. I did not let Envy or whatever it is install Flash or Acrobat. I did not install any proprietary drivers for the video card. I have not installed ANY Firefox add-ons at all.
1. the browser is rock solid. I can't make it crash. My previous installation, the one I bitched about at length on these forums crashed within a minute of opening FF, most of the time and a visit to these forums and especially yahoo.com would lock the sytem up almost immediately every time.

2. I then read about the ubuntuzilla project. Which allows for ubuntu to have the latest Mozilla release of firefox. That sounded good to me. I ran that script and I now have the mozilla foundation's latest release, 2.0.11. It is rock solid.

3. I am nearly scared to death to install Acrobat and/or Flash as those are the only differences that I have not been able to rule out as the culprit involved with the crashes. I need Flash, who doesn't ? I think that I might install the released version from Adobe or macromedia rather than the customized  (?) ubuntu app in  synaptic. I will let you know how that goes if I work up the nerve. Having a working OS that does not crash every time I surf is a tough thing to put in jeopardy again, for the 5th time or so (I kept reinstalling Ubuntu and Mint twice).

---

### Post by Tobba25 on 2007-12-03
Excuse me, but...

WHAT THE BUCK can we do about this gnarly stupid bug!?

I cant live on like this, not being able to SURF!??? I have to restart Firefox

ALL
THE 
TIME
!!!

Seriously, Im about to install Vista. With a good n slow virus scanner from mcaffee, cause that will be even more usable than this idiocratic sjittt!!

---

### Post by RgnKjnVA on 2007-12-03
I'm starting to get used to Opera although it doesn't do a few things that I like in FF. Mostly, I like having my RSS feeds available in a toolbar in FF. Other than that I'm finding I don't miss FF as much as I thought I would.

As a workaround, use the instructions above to set ping_delay to 30000. It will still lock up but it seems to help quite a bit. I really had to load FF up with about 8 tabs and run a YouTube video to lock it up at that setting.

I feel your frustration. I'm a first-time Ubuntu user eyeing this issue as a benchmark test of the common assertion from the U community that big problems get fixed fast in an open src OS. I would think this ranks as a pretty big issue and should be getting some serious attention. I guess we don't really hear that people are working on it so that adds to the feeling of frustration.

---

### Post by konradsa on 2007-12-03
Has anybody tried to the use ALT F2 + "metacity --replace" command to see if that fixes the problem?

---

### Post by RgnKjnVA on 2007-12-03
Yes it does. That was mentioned about a page back. 

I believe our options thus far appear to be:

1) Uninstall Google Toolbar -  I don't have it installed but have this problem

2) Install Firefox build versus Ubuntu build - I tried this as well but I still have the problem

3) Increase ping_delay in GConf-Editor (see post #170) - seems to decrease frequency of the problem if it is set very high but once it locked up it locked hard and I had to reboot

4) Don't run Compiz - Alt+F2 "metacity --replace". Only problem I had with this is that the Metacity win mgr is fairly bobo (technical term) and I don't just mean that it doesn't have wiggly windows.

5) Use a different browser - Opera appears to be FAR less likely to experience the issue.

6) Wait patiently for fix

7) Retreat to Windows to suckle the bloated teat of Micro$oft

---

### Post by TabletUbuntu on 2007-12-04
Hi All,

I was plagued with this problem since upgrading to gutsy.  In particular, this happened at exactly the same point on my bank's website when I tried to complete a transaction.  Based on info I read in this thread, I uninstalled google toolbar and I have not had this problem since (I even tried to reinstall it, and the problem came back). 

BTW, I am running Compiz and had not tried any other fixes.  I can confirm that, at least in my case, the problem had something to do with google toolbar.

Hope this helps someone else!

---

### Post by raiwo on 2007-12-04
hmm.. been using my sisters latop compaq presario 2100, celeron 2Ghz & 512Mb memory using ubuntu 7.10. Firefox does often that freezing & graying but also cpu usage is really high, something like 90-100% all the time! Firefox version is 2.0.0.10. I am going to try flash blocking if that would help because turning copmiz off didn't help... Any other ways to get firefox more responsive & lower cpu usage?

---

### Post by Tobba25 on 2007-12-04
At this very moment I am trying once again to use Firefox. Im am writing this message in Firefox...

But its gotten really bad. I am usually xnvcviewer'ing into another laptop thats got win xp, 128 mb ram and 700 mhz. Im on a fast connection, so its allright, but not very usable.

I dont want to install xp on my own machine, because I live Everything about ubuntu - except how it deals with Firefox.

I CAN NOT UNDERSTAND why this problem is not at the very top priority. There should have been fixes for this long ago. I think this is very, very serious.

Are there any officials, maybe moderators, that can enlighten us on what the process of fixing this is going?

---

### Post by BobCFC on 2007-12-04
I have never ever used Google toolbar so it is not that.

I do not think it is the Ubuntu build of Firefox because I use the new Flock browser which is based on firefox underneath and it still happens.

The worst culprit is browsing similar videos in YouTube, quickly clicking between them. 


Running *metacity --replace* is the same as turning off desktop effects for one session.

If you want to turn it off permanently goto System->Prefs->Appearance  and under visual effects  set it to none.   This will remain when you reboot.

---

### Post by konradsa on 2007-12-04
> **BobCFC said:**
> 
Running *metacity --replace* is the same as turning off desktop effects for one session.

If you want to turn it off permanently goto System->Prefs->Appearance  and under visual effects  set it to none.   This will remain when you reboot.

That's not correct. I had my desktop effects set to none (not supported on my laptop), and Compiz was still running and causing problems. Only after issuing the *metacity --replace* command the problems stop.

@Tobba25: Have you tried ALT + F2 and *metacity --replace*? You would lose desktop effects temporarily, but at least you would not need to reinstall XP and could wait for a fix.

---

### Post by TabletUbuntu on 2007-12-04
> **BobCFC said:**
> I have never ever used Google toolbar so it is not that.

I do not think it is the Ubuntu build of Firefox because I use the new Flock browser which is based on firefox underneath and it still happens.

The worst culprit is browsing similar videos in YouTube, quickly clicking between them. 


Running *metacity --replace* is the same as turning off desktop effects for one session.

If you want to turn it off permanently goto System->Prefs->Appearance  and under visual effects  set it to none.   This will remain when you reboot.

Well, it may not be the cause, but it somehow triggers the problem.  I install it, problem is there.  Uninstall it, it's gone.  I can now rapidly switch between videos on Youtube (as a test, I installed google toolbar again and youtube did freeze firefox).  

You shouldn't dismiss it so quickly- clearly google toolbar triggers the problem on my setup.

---

### Post by brjoon1021 on 2007-12-05
I found a solution for me.
 
I installed ubuntuzilla (google for it) which is the standard release of Firefox from Mozilla. I stayed clear of Flash from synaptic or anything that came with ubuntu to handle Flash content. Previously, I had installed Flash from synatpic. This time, I installed Flash from the prompt that you get from the firefox browser when you have navigated to a website that needs Flash. Just to make sure that this was not the version of Flash somehow coming through synaptic / Ubuntu, I have checked synaptic and it does not show Flash or the flash plugin installed. 
Let me stress that I have installed & gotten frustrated by the crashes and then reinstalled Gutsy and Mint at least 6 times over the last two weeks. All of the installs crashed like crazy when surfing with Firefox, especially [www.yahoo.com]("http://www.yahoo.com/"), for some reason would crash the system every sngle time. But this time, by avoiding the ubuntu branded andcustomized FF and Flash and Flash plugin, I am rock solid. The **[COLOR=red]ONLY[/COLOR]** software or hardware changes have been the FF and the Flash. I suppose it is worth it for you to try. 
 
As an aside, I have never used or had the google toolbar, never used or had a proprietary video driver. I uninstalled, reinstalled, compiz. Always crashed anyway.

---

### Post by bkline on 2007-12-07
> **brjoon1021 said:**
> I found a solution for me.
 
I installed ubuntuzilla (google for it) which is the standard release of Firefox from Mozilla. I stayed clear of Flash from synaptic or anything that came with ubuntu to handle Flash content. Previously, I had installed Flash from synatpic. This time, I installed Flash from the prompt that you get from the firefox browser when you have navigated to a website that needs Flash.

Sounds like evidence that the problem is with Ubuntu.

Can you provide more details on the process you followed to install "Flash from the prompt that you get from the firefox browser ..."?  I followed your steps but then ended up with an "installation failed" message, which then took me to Adobe's site for "manual installation" with three options for Linux: a tar file, an RPM file, and a YUM file.  Which one did you pick?  Or did you not get the failure message pushing you into the manual installation path?

Thanks.

Hope this gets fixed this soon -- from the length of this thread it looks like a pretty widespread problem.

Bob

---

### Post by Alex Dinamo on 2007-12-07
I think that it was a terrible idea to put compiz as a default. I have had a terrible time with Gutsy so far, not only this constan  Firefox crashes: amarok also brings THE WHOLE X down whenever seems like it, for instance..

Now I am saving money for a Mac, seriously. If by the time I get the money I still have problems with Ubuntu.. that's it... sorry...Meanwhile I may try to use Gutsy without compiz.

Alex

---

### Post by Alex Dinamo on 2007-12-07
BTW... I just found a way to disable the whole XGL + compiz contraption.. just do this:

```
 touch ~/.config/xserver-xgl/disable
```

Create the necessary directories if they do not exist.

My processor has never been so relaxed since I installed Gutsy. Let's see if this fixes my slew of problems with this release...

---

### Post by RgnKjnVA on 2007-12-07
bkline, I tried the rpm and got all kinds of missing dependencies (I thought that's what RPM was supposed to handle). I then installed from the tar.gz. Not only did it not fix Firefox but now I can't stream video in Opera *sigh!*

---

### Post by WileyCoyote on 2007-12-07
> **Alex Dinamo said:**
> BTW... I just found a way to disable the whole XGL + compiz contraption.. just do this:

```
 touch ~/.config/xserver-xgl/disable
```

Create the necessary directories if they do not exist.

My processor has never been so relaxed since I installed Gutsy. Let's see if this fixes my slew of problems with this release...
Thank you, a hundred times thank you.

I can't say with 100% confidence that its solved ALL of my almost constant Firefox "graying" problems, but about 10 minutes of heavy use on troubled sites seems to indicate things are MUCH better after following the above procedure.  I haven't seen gray once, my hourglassing is FAR faster/shorter, and I'm not getting scripts stalling out anymore either (that seems to happen if you fiddle around too much while in gray mode).

x64 Gutsy install, with an Athalon 64 FX-60 Dual Core.  Fairly wimpy video card an AGP GeForce FX with 128Mb that was great for its time, but way past it now), but I don't really push it.  Nothing too strange.  Nothing that prepared me for the disaster that simple web browsing has been lately on Ubuntu.

Anyway, pre-"touch",  YouTube and eBay were the big problems.  Both seem to be infinitely better now, after this, plus logging out and back in.  I DO have yet to do a full reboot, but it doesn't seem necessary.

This solution should be passed around a bit more for confirmation, but I for one am overjoyed.

Question?  What exactly are the other implications of this?  Compiz is clearly still running in some sense because its on my process list and I have at least the standard slate of desktop effects (well, at least the "Desktop Wall" effect, since I had most everything else turned off already, and the Wall is useful).  What was sacrificed by the above?  Whatever it was, its worth it, but I am curious.

---

### Post by RgnKjnVA on 2007-12-08
I don't have an xserver-xgl dir is that a problem?

---

### Post by Swervo on 2007-12-10
I'm running into the same problem it would seem.   I've updated to Gutsy, and everything is working flawlessly except for Firefox.   Yahoo Mail and Hotmail seem to be the biggest culprits, every single attempt to view an email results in at least one, if not multiple, 30-45 second lockups in Firefox.   It always comes back eventually, but it really does make web browsing useless.   I've since installed Galeon which runs flawlessly (with the Gecko engine, no less), but I miss my Firefox.

I tried touching ~/.config/xserver-xgl/disable, but that doesn't seem to have fixed it (nor does it seem to have disabled compositing, compiz-fusion is still running quite fancily).   I don't have the Google toolbar, a removal and reinstall of Firefox didn't fix it, and running metacity --replace doesn't fix the problem, it just makes the window not turn grey...it still locks up for 30-45 seconds.   I tried swapping out for Opera, but at least in the official packages list, there is no 64-bit version and I can't install it.

This is a bit frustrating as Firefox is probably my single most-used app, yet it's the only one that's just plain not working right.   Here's hoping a fix shows up soon, or at least a fix that works for me.

---

### Post by Swervo on 2007-12-10
I should have noted in the post before that there is no noticeable increase in CPU or memory usage, everything else functions normally and top shows nothing special when Firefox locks up.

---

### Post by Alex Dinamo on 2007-12-10
Guys, if you did the "touch" procedure:

```
 touch ~/.config/xserver-xgl/disable
```

... to disable compiz and XGL and you still have it running around, then something is wrong. Compiz should NOT be running anymore...

Did you reboot after doing the procedure, right? I believe I forgot to mention that...

Since I did it, my system seems way better, more stable and performant... my Firefox runs better of course, and my Amarok hasn't made X break... either XGL or compiz or both were not working OK, at least with my ATI card. And that is a shame, because it means Ubuntu developers didn't think a lot on ATI users or didn't test enough. Believe me guys: Gutsy has been one of my most frustrating distro releases in some time. And I have used *quite* some distros in my life...

Stability and performance are of utmost importance for an OS. If you think that visual trickery and those kinds of  bells & whistles are first, then maybe you should switch to Vista. Good luck to you.

Alex

---

### Post by justinclark on 2007-12-10
Im having these issues as well.  Seriously should I just install Feisty?  Is there major differences from Feisty to Gutsy other that browsing on Gutsy sucks?

---

### Post by mahiyar on 2007-12-11
From whatever I have seen in the posts and my own problem I feel this certainly is a speed/time issue. i.e if there is a java element in the page esp. feed kind of thing like ticker and it does not get input in time it hangs. Can anybody confirm whether their internets are slow when FF hangs?

---

### Post by Swervo on 2007-12-11
> **Alex Dinamo said:**
> Guys, if you did the "touch" procedure:

```
 touch ~/.config/xserver-xgl/disable
```

... to disable compiz and XGL and you still have it running around, then something is wrong. Compiz should NOT be running anymore...

Did you reboot after doing the procedure, right? I believe I forgot to mention that...



Here's what I've got filewise:

```

swervo@swervo-desktop:~/.config/xserver-xgl$ pwd
/home/swervo/.config/xserver-xgl

swervo@swervo-desktop:~/.config/xserver-xgl$ ls -l
total 0
-rw-r--r-- 1 swervo swervo 0 2007-12-09 23:27 disable

```

X still fires up with all the composite bells & whistles.

As far as the speed time issue, it's happened whether my connection is quick or not, and while it's locked up, Galeon runs plenty speedy.   It happens most often to me on javascript heavy mail sites (yahoo mail, gmail, etc), but it seems like it can happen on any page.   Once the page is done loading, however, it's fine.

---

### Post by billgoldberg on 2007-12-11
My firefox has greyed out a few times, only with lots of tabs open and some flash content (youtube, ...) playing.

I always do
```
pkill firefox
```
Then I restart firefox and restore, tis took me a 20 sec every time i had to do it. The same problem with epiphany and flash.

---

### Post by WileyCoyote on 2007-12-11
> **Alex Dinamo said:**
> Guys, if you did the "touch" procedure:

```
 touch ~/.config/xserver-xgl/disable
```

... to disable compiz and XGL and you still have it running around, then something is wrong. Compiz should NOT be running anymore...

Did you reboot after doing the procedure, right? I believe I forgot to mention that...

Since I did it, my system seems way better, more stable and performant... my Firefox runs better of course, and my Amarok hasn't made X break... either XGL or compiz or both were not working OK, at least with my ATI card. And that is a shame, because it means Ubuntu developers didn't think a lot on ATI users or didn't test enough. Believe me guys: Gutsy has been one of my most frustrating distro releases in some time. And I have used *quite* some distros in my life...

Stability and performance are of utmost importance for an OS. If you think that visual trickery and those kinds of  bells & whistles are first, then maybe you should switch to Vista. Good luck to you.

Alex

The first time I tried the procedure, I restarted X by didn't do a full reboot.  After that I noticed some real improvements in the graying situation, but it might have just been a transitory coincidence.  I mean I've noticed after a while that I AM still getting it, only its more with Gmail and a bit less with YouTube.  So my earlier confidence that I had things under control is gone.

At a later point I repeated things with a full reboot.  No dice.  Compiz.real is still running.  Greying still happens.  And Ubuntu has really shaken my confidence in them, because clearly this is a very common problem and it doesn't seem like they are doing much on their end to fix it.

---

### Post by Alex Dinamo on 2007-12-11
> **Swervo said:**
> Here's what I've got filewise:

```

swervo@swervo-desktop:~/.config/xserver-xgl$ pwd
/home/swervo/.config/xserver-xgl

swervo@swervo-desktop:~/.config/xserver-xgl$ ls -l
total 0
-rw-r--r-- 1 swervo swervo 0 2007-12-09 23:27 disable

```

X still fires up with all the composite bells & whistles.
.

I have no idea. It should work... Another Gutsy feature???

Alex

---

### Post by WileyCoyote on 2007-12-11
> **mahiyar said:**
> From whatever I have seen in the posts and my own problem I feel this certainly is a speed/time issue. i.e if there is a java element in the page esp. feed kind of thing like ticker and it does not get input in time it hangs. Can anybody confirm whether their internets are slow when FF hangs?
I am almost positive there's nothing slow overall about my Internet access when I get the greying problem.  Could it relate to slowness with the specific sites I see it most often with (YouTube, Gmail)?  Sure.  But those sites have LONG had performance issues and nobody else's browser on nobody else's operating system grays out for 30-90 second blocks of time every time they run into a challenging bit of javascript.

I mean I resent not even being able to cancel the page draw.  Or use my back button.  I just have to sit there like an *** and watch tons of grey screen time.  Or kill the whole browser and restart.

Lets put it this way.  I have a little handheld wireless-internet Nokia N800 device running Linux on a tiny wimpy ARM processor that can web browse to Gmail.com and run those crappy javascripts better than the current Ubuntu seems to be able to do it.  That says a lot.

What's most upsetting is that Ubuntu seems to have decided its not their problem.  They won't assign the problem and/or are rating it low priority.  Look at the following pages for proof of that.

[https://bugs.launchpad.net/ubuntu/+bug/172419](https://bugs.launchpad.net/ubuntu/+bug/172419)

Note the header "Bug #172419 is not in Ubuntu".

and

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/124581](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/124581)

Note the header "Bug #124581 in firefox". Also, the "importance low" rating.


This is all nonsense.  Nobody else's Firefox gets this.  Ergo, the problem IS in Ubuntu.

I'm a few days away, I think, from switching back to SUSE. Or perhaps playing with the new Fedora.  Because as much as I hate to reduce a computer to web browsing, that IS about 3/4 of what I do on one.  I may monkey around with some of the more radical solutions suggested to deal with this problem, but I find myself wondering if its worth the trouble.

---

### Post by mahiyar on 2007-12-11
I know how it feels. Luckily for me sites like gmail, youtube, etc work fine its only some site and always on those sites it freezes. For these sites I use Opera.

---

### Post by cresny on 2007-12-11
Add me to the satisfied Ubuntuzilla script beneficiaries. For the past week Firefox has worked flawlessly, with seemingly less CPU load (can't verify this). If you still get the gusty grey-out, don't waste any time, it only takes a minute to install. Btw, I have Google toolbar, adblock, and several other plugins + flash. No issues at all after a week of hard use. 

One plugin I do NOT have since installing standard firefox is Ubuntufox. This was new in gutsy - could it have been this all along, or did I miss someone uninstalling it?

Anyway, the folks at Canonical must be asleep at the wheel. If there's one way to make people hate the user experience, mess up the web browser!

---

### Post by ajhinz on 2007-12-12
I'm running 7.10 64-bit edition, and I was having the same problem.

My guess was that it had something to do with Flash.  I (mistakenly) used this script to install it:

[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

It was a mistake because I got my names mixed up (I thought 7.10 was Feisty Fawn).  Therefore i ran the script, telling it that I was running Feisty Fawn.  After that, Flash worked great in Firefox.

Later, Ubuntu tells me that nspluginwrapper is out of date.  After updating that, I started getting the grey out that people have talked about.

My solution was to remove nspluginwrapper with Synaptic (and probably any other flash-related packages installed) and run the script in the thread above.  It worked for me.

Maybe someone with more knowledge can look into if the current version of nspluginwrapper is bad?  Also, someone find out what version the script downloads.

---

### Post by bkline on 2007-12-12
> **bkline said:**
> Can you provide more details on the process you followed to install "Flash from the prompt that you get from the firefox browser ..."?  I followed your steps but then ended up with an "installation failed" message, which then took me to Adobe's site for "manual installation" with three options for Linux: a tar file, an RPM file, and a YUM file.  Which one did you pick?  Or did you not get the failure message pushing you into the manual installation path?

Well, brjoon1021 was apparently unwilling to share any further details so I went ahead and installed from the tar file.  Didn't solve the problem.  So I've tried the replacement Flash plug-in, the Ubuntuzilla dstro for the browser, and completely disabling the flashy desktop eye candy, and the browser is still freezing up solid several times per day.  I can't believe the Windows workstation I work on for one of my customers is more reliable than my main Linux workstation!  I never thought I'd see the day where the uptime for the Windows machine is measured in weeks and I'm rebooting Linux several times a day.

The icing on the cake was when I tried to back out the replacement Flash plug-in and reinstall the Ubuntu package, at which point I was told it couldn't install the plug-in because the MD5 sum is bad.

Ubuntu is in a shambles at the moment. :(

---

### Post by Merovius on 2007-12-12
Not sure if this is the cause for others. I was having crazy amounts of graying out and freezing up when large flash sites like YouTube were loading. I tried many reinstalls of Flash from Adobe and Gnash etc. No help. Then I disabled these two plugins:" Ubufox" and "User Agent Switcher". I have just run two videos from YouTube on separate tabs with no freeze up or gray. I even switched back and forth. No problem. Just thought I'd put it out there.:popcorn:

---

### Post by jamillikan on 2007-12-13
Installing Opera 9.50 resolved the issue for me.  No more freezing for me when I use Opera.  Firefox still freezes.  Wish they would fix Firefox because I really like it, but Opera, for me, is more reliable.

Wonder why that is?  It's definitely a problem with Firefox somewhere and not Ubuntu.

---

### Post by WileyCoyote on 2007-12-13
> **jamillikan said:**
> Installing Opera 9.50 resolved the issue for me.  No more freezing for me when I use Opera.  Firefox still freezes.  Wish they would fix Firefox because I really like it, but Opera, for me, is more reliable.

Wonder why that is?  It's definitely a problem with Firefox somewhere and not Ubuntu.
No, its Ubuntu.

At least in the sense that it appears to specifically be the interaction BETWEEN Ubuntu and Firefox.  It appears to be due to Ubuntu custom code or integration, because I haven't read ANY reports of a similar problem on other distributions.

If we let it be dismissed simply as a "Firefox" problem, it will likely never get fixed.  Is Firefox going to fix the Ubufox extension if its that?  Or the way that Compiz interacts with Firefox?  Sure, some combination of Flash, Java and Firefox is what's triggering this, and those are all non-Ubuntu maintained items, but something Ubuntu exclusive is interacting and doing this.  And it looks like they aren't going to admit it, or fix it, I guess.

---

### Post by ozone702 on 2007-12-13
Here's what I did to solve the problem:

I went to System / Preferences / Sound.
I went to Sounds tab.
I changed Log in: to No sound.
I changed Log out: to No sound.
I re-booted.

I'll bet what happens is Ubuntu tries to play the "Log in" sound while the sound driver is being loaded which causes fail loading.  Is there a log I can check to see if this is the case?

---

### Post by RgnKjnVA on 2007-12-14
> **RgnKjnVA said:**
> bkline, I tried the rpm and got all kinds of missing dependencies (I thought that's what RPM was supposed to handle). I then installed from the tar.gz. Not only did it not fix Firefox but now I can't stream video in Opera *sigh!*

FYI: my inability to stream video in Opera was due to the Flash update. Had to install the Opera 9.5 beta to be able to stream vids again.

However, it's not even necessary because the Firefox problem appears to be resolved. I've been using Firefox for 2 days now under what are normal conditions (6 tabs open now including  YouTube vid and news site front page) without a single freeze. Unfortunately, I've done so many things I'm not exactly sure what fixed it. I suspect it was installing from Ubuntuzilla and maybe more specifically getting rid of the Ubufox extension but I can't explain why the install didn't seem to fix the problem initially. Can't recall if I restarted or not so maybe it needed a bounce first. I'm just giddy to have my FF back! Hooray!

---

### Post by RgnKjnVA on 2007-12-15
LOL Oh well, I had a good run (3.5 days or so) but now FF is back to being incredibly sluggish. Doesn't fade and eventually all clicks on the locked up browser get executed. It's like it's having to swap or something even after re-login or reboot. This is REALLY kiling the thrill of my first install of Ubuntu. =o /

...now why is Opera running at 100% cpu?!  This thing is constant work

---

### Post by Turin Turambar on 2007-12-17
I didn't have any problem with firefox, BUT I noticed that it freezes on some sites more than usual. 
For example, when I open Ubuntu forum and other domestic site about plants, in 90% it will freeze. However, that's not something that happens in every site - far from that. FF is pretty stable, but  I thought it was a FF problem, from what I've read here, it seems that Ubuntu team messed something.

Did anyone fill a bug report on this issue (freezing)?

---

### Post by bkline on 2007-12-17
> **bkline said:**
> The icing on the cake was when I tried to back out the replacement Flash plug-in and reinstall the Ubuntu package, at which point I was told it couldn't install the plug-in because the MD5 sum is bad.

Ubuntu is in a shambles at the moment. :(

Well, the lockups have stopped, which I assume is result of the package manager's inability to install the flash plug-in.  Is this really the Ubuntu solution to the problem?  Personally, I would prefer a web without proprietary technologies, but that's not likely to happen in my lifetime.  So now I have the following options; I can't say I'm really excited about any of them:
[LIST]
[*]Live with the inability to view the content of sites with Flash
[*]Reboot my workstation several times a day, as if I had stepped through a time warp back to Windows 95
[*]Use a Windows machine to view sites with Flash
[*]Drop Ubuntu and switch to another Linux distro
[/LIST]

---

### Post by fragos on 2007-12-17
I have seen occassional lockups when first accessing this forum.  Restarting usually fixes the problem.

---

### Post by Turin Turambar on 2007-12-18
I definitely have the worst problems (FFF - firefox freezing)  with this forum. Usually when other sites are open in other tabs or windows.

That's quite ironic, isn't it? :(

---

### Post by fragos on 2007-12-18
I'll take that a step farther.  My initial entry that to my memory always works is [http://ubuntuforums.org/](http://ubuntuforums.org/).  When selecting from the Main Support Catagories that the problem occurs.  It seems that the failure occurs when opening the support caragory and not when displaying additional pages within the catagory.

---

### Post by sheazar on 2007-12-19
I expirienced the same problem on several sites, but since installing flash using [http://ubuntuforums.org/showthread.php?t=476924&highlight=install+flash](http://ubuntuforums.org/showthread.php?t=476924&highlight=install+flash)
it finally stopped :) so far at least...

---

### Post by RgnKjnVA on 2007-12-22
Update FWIW: The long delay I described above stops when I close Amarok. Upon closing Amarok, the browser immediately executes any clicks or wheel activity that occurred while it was in a locked-up state and runs fine thereafter. Hmmmm

FF also seems to keep Amarok from initializing the audio driver if it's running first. Why would a browser wrestle for the audio driver? These two don't seem to get along nicely which stinks 'cause I like to use both simultaneously.

---

### Post by SpookyET on 2007-12-22
I have a feeling that it is the new flash version that is causing this. I wish to go back to the previous version and test my theory, but I do not know how.

According, to the [Penguin.SWF]("http://blogs.adobe.com/penguin.swf") blog,

> 
This is also the first official Linux release to support the new XEmbed browser protocol which simply allows a browser plugin on Unix to behave better in a modern desktop environment.


I think that is causing the lockups.

---

### Post by WileyCoyote on 2007-12-24
> **SpookyET said:**
> I have a feeling that it is the new flash version that is causing this. I wish to go back to the previous version and test my theory, but I do not know how.

According, to the [Penguin.SWF]("http://blogs.adobe.com/penguin.swf") blog,



I think that is causing the lockups.
Maybe.  But part of the questioning process has to always be "why is this only happening on Ubuntu Gutsy"?

I mean I don't use other Linuxes daily, but I DO use them.  I've used SUSE 10.3,  Fedora 8, and Saboyon Linux all within the past few weeks.  On the SAME hardware as my Ubuntu Gutsy system, thanks to a removable hard drive.  And none of them are having ANY problem like this.

I've also frequently used a completely up-to-date copy of Ubuntu Feisty on another box, as well as Windows Vista on yet a third system.  All using Firefox, all using the same standard set up add-ons/plugins I use on every system.

So if its Flash, its Flash PLUS Gutsy.  There's no way around that.

---

### Post by ozone702 on 2007-12-24
> **RgnKjnVA said:**
> LOL Oh well, I had a good run (3.5 days or so) but now FF is back to being incredibly sluggish. Doesn't fade and eventually all clicks on the locked up browser get executed. It's like it's having to swap or something even after re-login or reboot. This is REALLY kiling the thrill of my first install of Ubuntu. =o /

...now why is Opera running at 100% cpu?!  This thing is constant work
Please do the following and report if this solved your problem:

Go to System / Preferences / Sound.
Go to Sounds tab.
Change Log in: to No sound.
Re-boot.

---

### Post by fragos on 2007-12-25
When I get annoyed with Firefox performance I switch to Epiphany.  It uses the same Gecko rendering engine and is much faster.  If not for some of the wonderful Firefox extensions I'd stick with Epiphany.  Hopefully Firefox 3 will make all well in Mozilla land again.

---

### Post by RgnKjnVA on 2007-12-25
same behavior with Log In set to No Sound.

---

### Post by ozone702 on 2007-12-25
Sorry to hear that.  I have the same behavior everyone is experiencing when mine is set to play a sound, but when I set it to No sound and re-boot, my browser works perfectly.

I was ready to give up on Ubuntu also until I accidentally figured this one out.

---

### Post by RgnKjnVA on 2007-12-28
Yesterday I discovered that XMMS plays much nicer with FF on my system and is a virtual WinAmp twin which is my media player of choice in Windows-land so win-win in that regard. Hooray! 

Now if only XMMS wouldn't jack up my system sounds. *sigh* It's always somethin' in Ubuntu as I'm quickly learning. Oh well, I guess I'll still count it as progress.

---

### Post by bkline on 2007-12-31
I think I may finally have a way to run Firefox+Flash on Gutsy without it freezing up on me all the time.  I was able to reinstall Flash by hand (no one has been able to figure out how to get the APT installer to use the right checksum) and then I turned off the powernow daemon.  Right after that last step the freezes, which had been *very* reproducible as long as Flash was installed, stopped suddenly.  I'm knocking on all the wood I can find.

I'm not convinced, looking over this thread, that there's only one single problem behind all of the undesirable behavior described.

Good luck, and here's hoping Ubuntu gets back to a more reliable state soon!

Bob

---

### Post by abrianb on 2008-01-13
Has anyone turned off Tracker? I turned off indexing under System>Preferences>Indexing Preferences, Unchecked the first two boxes and then no problem for a couple of weeks. I started having the Firefox gray screen again yesterday. I went to indexing preferences and found the first two were again checked. This must have occurred during updates as I did not do it. I unchecked them again and now I have Firefox working fine.

---

### Post by pranjal_24 on 2008-01-14
> **abrianb said:**
> Has anyone turned off Tracker? I turned off indexing under System>Preferences>Indexing Preferences, Unchecked the first two boxes and then no problem for a couple of weeks. I started having the Firefox gray screen again yesterday. I went to indexing preferences and found the first two were again checked. This must have occurred during updates as I did not do it. I unchecked them again and now I have Firefox working fine.

Yes, you're right that did it. [COLOR="Black"]_***[FONT="Arial Black"]Disabling indexing speeded up things a lot.[/FONT]***_[/COLOR]
Thanks [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

Oh, one more thing, If i use failsafe gnome, the browsers run faster in that.
I tested everything without compiz effects.

---

### Post by gaupe on 2008-01-14
oke my experience till now.
ffox Always when 3d instance wanted to start it freezed

i installed ffox via ubuntuzilla problems solved for me.
nevertheless i swicthed off indexing now toooo :)

---

### Post by jryprt on 2008-01-14
> **abrianb said:**
> Has anyone turned off Tracker? I turned off indexing under System>Preferences>Indexing Preferences, Unchecked the first two boxes and then no problem for a couple of weeks. I started having the Firefox gray screen again yesterday. I went to indexing preferences and found the first two were again checked. This must have occurred during updates as I did not do it. I unchecked them again and now I have Firefox working fine.

This works great Thank You

---

### Post by konradsa on 2008-01-27
FYI

I tried all the fixes outlined in this and other threads, but nothing worked for me and it was just too frustrating. ](*,) I can't live without my Firefox. I used to love Ubuntu, but it seems that the quality has rapidly deteriorated over the last two releases. I hope they turn it around with 8.04, otherwise many people may switch back to Windows, I came very close to doint it!

Anyways, I moved on to Opensuse 10.3 and I am not looking back anymore. Firefox works perfect, and it also seems a lot more polished than Ubuntu. Desktop effects worked out of the box on my laptop, it's amazing, something that I could not get to work on Ubuntu after days of trying. Wobbly windows are nice!! :) So did also hibernation and other things that gave me a lot of headaches on Ubuntu.

It has its fair share of downsides compared to Ubuntu (tip: use smart with its gui for package management, it's the only thing that even comes close to Synaptics on OpenSuse), but the advantages far outweigh all the problems I had on Ubuntu. It has been a very pleasurable experience and I would encourage anybody frustrated with the Firefox issue to give OpenSuse a try!

---

### Post by fragos on 2008-01-27
Glad your back to a good user experience.  Suse changed their package management in 10.1 and it was a major disaster.  It screwed up the system so bad that all it would do is crash.  That's when I went to Ubuntu.  My occasional Firefox grey outs have gone away and I'm still a happy Ubuntu user.  It's interesting that users can have such different experiences with the same distribution.

---

### Post by hanmade on 2008-02-03
I turned/uninstalled off a javascript debugger in ff which seems to have made a difference.

---

### Post by Chessmaster on 2008-02-05
I was having problems with Firefox Freezing and turning grey. I am on Dial-Up and was using the network manager, but as soon as I moved to using Gnome-PPP the greying and freezing stopped - I also found I could properly access web pages I couldn't before i.e. Yahoo.com and Hotmail. So if you are going Grey and using Dial-up, might be worth trying. 

Why this worked I have no idea. But it did, so I am much happier than before, although I would love to know why this worked.

---

### Post by kesman on 2008-02-05
Install adblock plus and flashblock add-ons to firefox and learn to use adblock's blockable elements.

---

### Post by Chessmaster on 2008-02-05
I tried turning on and off ad blocker, flash, javascript...uninstalling them etc..etc...I tried 5 different browsers...disabling this, disabling that...did something new basically every day for two weeks. Still got freezing and grey browser and no images in hotmail and yahoo.

The only solution I found was to install Gnome-PPP and use that instead of the network manager. It worked, but I have no idea why.

---

### Post by jorgecarrillo150990 on 2008-02-05
I have the same issues, but only when I start to download something, it opens the download box (in which you are supposed to click open, save, etc) But nothing appears, and then it turns gray.
Any solutions?
Sorry if this is highjacking a thread, but it turns grey.

---

### Post by koldphlame on 2008-02-05
YES IT HAPPENS TO ME AS WELL USELY WHEN II USE FIREFOX!

BUT HAS HAPPENS DURING OTHER APPLICATIONS 


:mad:

---

### Post by Gustavo on 2008-02-12
> **jorgecarrillo150990 said:**
> I have the same issues, but only when I start to download something, it opens the download box (in which you are supposed to click open, save, etc) But nothing appears, and then it turns gray.
Any solutions?
Sorry if this is highjacking a thread, but it turns grey.

Same here :(

---

### Post by halln on 2008-03-16
My 7and 4 yrs old kids are annoyed with this already. Im trying to train them  to use ubuntu as early as their age but everytime they play a game from a website called playhouse disney or thomas the tank engine it always grayed out and freezes  and lately they gave up using ubuntu because of this. I love ubuntu, I know that the problem is not ubuntu itself but still it is a part of ubuntu installation and it hurts me if I see my kids using xp again because of this graying thing. I tried most of the (fixes) I can find in this forum but nothing really works. Is it flash? is it ping delay? Is it compiz? Is it firefox and its addons? etc. 
 
I hope somebody knows out there knows the real fix that could help us Its not a big problem though but its annoying.  tnx in advance

---

### Post by fragos on 2008-03-17
I recommend you try the Gnome browser Epiphany.  Like Firefox it uses the Gecko rendering engine and is compatable with plugins like flash.  It runs much faster and doesn't crash.  If you're hooked on some of the Firefox extensions you may miss them but Epiphany has a number like Adblock. I changed to Epiphany a while ago.

---

### Post by erichmj on 2008-03-17
25 pages is a lot to go through. Normally I hate posting my thoughts before reading a thread in it's entirety but here we are. It's been my experience that flash causes many of the freezes associated with firefox. This may not be what causes your issues, but after tracing crashes this is what I have found. I will wait for adobe to fix this since Gnash is not an option and won't be any time soon.

---

### Post by A$h X on 2008-04-03
I'm not doubting that flash plug-in's are maybe the cause of this BUT I never get firefox to hang when visiting flash-based sites. In fact the ONLY site to make firefox crash is this site, our beloved ubuntu forums! :frown:

As far as I know, there aren't too many resource-intensive applets on the front page of ubuntu forums, I'm at a loss to explain why this site of all places would make FF hang? 

BTW it's not a complete hang, if leave FF for 5-10 mins then it will function normally. Also while FF is having it's funny turn, I can use the rest of the system fine, but ubuntu forums hanging firefox is a fairly common occurrence, unfortunately.

---

### Post by fragos on 2008-04-03
> **A$h X said:**
> I'm not doubting that flash plug-in's are maybe the cause of this BUT I never get firefox to hang when visiting flash-based sites. In fact the ONLY site to make firefox crash is this site, our beloved ubuntu forums! :frown:

As far as I know, there aren't too many resource-intensive applets on the front page of ubuntu forums, I'm at a loss to explain why this site of all places would make FF hang? 

BTW it's not a complete hang, if leave FF for 5-10 mins then it will function normally. Also while FF is having it's funny turn, I can use the rest of the system fine, but ubuntu forums hanging firefox is a fairly common occurrence, unfortunately.

My experience is the same. There's something about the entry into this site. I finally got annoyed to the point that I switched to Epiphany. It uses the same Gecko rendering and runs so much faster. It doesn't have as many extensions as Firefox but the plugins like flash still work. I've had no trouble with this site since I made the change.

---

### Post by mahiyar on 2008-04-04
If somebody wants to listen a poor mans advice here it is. The problem in firefox may be because of conflicting font settings in the browser. If you have unticked the Edit>Prefferences>Contents (tab) > Advanced> Allow pages to choose .....  button, then these settings might get in to conflict with flash fonts resulting in lock ups. This behaviour is demonstrable.

---

### Post by brjoon1021 on 2008-04-19
I started this so I feel ballsy enough to reopen it. I just had the same hang with totally different hardware (new computer) and FF was sitting on a page with no flash. This is what it visually looks like, the screen dims or tints for lack of a better word, kind of like what happens if you take your laptop and pull the plug and let it run on battery - it dims just a little. Sometimes, moving the mouse will bring it back to life, sometimes the mouse moves a little then just hangs there and the power supply is the only way to shut it down.

Now... I am using a desktop. Ubuntu has a hell of a lot of stuff geared at making laptops easy on the battery. I have always had the hunch that maybe the problem really is something to do with the CPU speed / power controls/ etc... stuff that may be trying to treat my desktop like a laptop. I know that there is some issue with FF because I have locked up on this very forum many times and had a bout where as soon as I even clicked enter after trying to browse to Yahoo.com, the whole thing would lock up as I described above.

Any thoughts  ?

---

### Post by fragos on 2008-04-19
The greying of a window seems to be a system thing that may relate to some form of inactivity or time out.  It doesn't happen often but I've seen it when my system was very busy CPU wise. Normally it will come back to life on it's own. The grey outs with Firefox however are more frequent and don't seem to come back alive. If you click to close a greyed window that is unresponsive you may get a system message that the ap is unresponsive and do you wish to wait or close. I switched to Epiphany. it's very much more responsive and uses the same Gecko rendering engine.

---

### Post by geokok1981 on 2008-04-23
Just upgraded to hardy (clean install). I never had the "grey out" problem with FF until now. FF will grey out for an amount of time in random sites, even the forums here. Sometimes it even remains greyed out even after I regain control. 

I guess I ll miss stumble upon the most....lets see..epiphany...opera..hmmm

---

### Post by FW190 on 2008-04-26
Hi guys, first post here, only recently started with Ubuntu but had really depressing issues with this FFF problem, I did try to use Opera but it's just not as versatile or user friendly as FF, or at least I think so. 

Few pages ago here in this thread somebody mentioned the ping delay as adjusted in the config editor, this really helped in my case (I use a current value of 25000) ad did adjusting the auto-raise delay but also lowering down the workload for the Compiz window decorations, helped to reduce any freezing up. 
This is of course not how it is supposed to be, but I'd rather have less eye candy than work with Opera. 
Also [these, I'd say, "workarounds"]("http://computertip.googlepages.com/ubuntutipsentrucs") helped a bit and although these pages are not in English, I'm sure the apps and plugins are universal. 
For "some reason" (read: trying to resolve another problem) my settings reverted to default which stuffed up FF again but reinstalling formentioned plugins helped a lot and just now I tested to adjust the ping delay back to the original setting, which resulted in FFF almost straight away. 

Hope this helps, just my $0.02
I don't know what going to happen to this in Hardy but although it's not perfect yet, I decided to keep on trying on Ubuntu/FF.

---

### Post by cogitordi on 2008-04-27
[http://ubuntuforums.org/showthread.php?p=4813298](http://ubuntuforums.org/showthread.php?p=4813298)

See post #6.

---

### Post by julianmag on 2008-05-06
**I'm experimenting the same problem.**

Please, anybody knows why this is caused?

I've a **Toshiba Satellite with 3GB RAM** (fast enough to be freezed so often).

I've upgraded to Ubuntu 8.04, Firefox 3 beta 5, Flash, and many other things such as Google Desktop, etc. but I was unable to detect what is the problem. Can you suggest me any tool to check Hard Disk IO accesses by processes? I also have compiz but it was installed previously and without problems.

Symptoms
- Firefox freezes so often. **50% of the time or more** (sometimes with gray screen and sometimes the normal screen).

Also I ran Firefox without plugins, in safe-mode, and still happening the same.

Any suggestion would be appreciated.

Julian

---

### Post by julianmag on 2008-05-06
Well, after I did some tests, I removed the Flash plugin, that seems to be causing most of these performance problems.

```
sudo apt-get remove flashplugin-nonfree
```

But, I'm not 100% sure if this would resolve the problem completely, any other suggestion is appreciated. Thanks.

julian (( at )) [weblatam.com]("http://weblatam.com")

---

### Post by Rohen on 2008-05-06
> **PartisanEntity said:**
> Has anyone else experienced this behaviour in Firefox? Sometimes it will freeze and turn grey, I then have to wait for a few seconds for it to resume again.

It's a bad upgrade/installation issue with Hardy.

I had exactly the same problem except it also happened in Evolution and Gaim.  A fresh re-install fixed everything and it's now running nicely :)

---

### Post by gtaluvit on 2008-05-06
It's a known bug. I forget where I saw the link but do a search for sqlite cache and you'll find it. For the time being, just disable "Warn if site is a suspected forgery" or "attack site" and you should be fine.

---

### Post by fragos on 2008-05-06
I switched to Epiphany months ago. Problem solvedwith basically the same rendering engine. Much faster as well.

---

### Post by CoolDreamZ on 2008-05-07
This has become worse recently on my Gutsy system. There is a known bug, see [here]("https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/177856")

---

### Post by julianmag on 2008-05-08
I[ve disabled Compiz and now it seems to be working fine. No freezes in firefox nor vmware.

Julian

---

### Post by julianmag on 2008-05-10
You can find a workaround to this problem on the following links:

[http://weblatam.com](http://weblatam.com)
[http://tombuntu.com/index.php/2008/05/07/firefox-3-excessive-disk-io-and-freezing/](http://tombuntu.com/index.php/2008/05/07/firefox-3-excessive-disk-io-and-freezing/)

---

### Post by wydesenej on 2008-06-01
Yes I have same problem on Kubuntu Hardy. When Iam on some web where is flash its about 3 minutes and then FF freezed. :mad:](*,)

---

### Post by bokbok on 2008-06-07
fwiw, I had this issue, but after I while I realized it was not isolated to FF, only seemed like it because I used it so much.  I turned off Visual Affects from the System->Preferences->Appearance menu, and it's been a few weeks since I've seen a single grey app.  I have some fairly lowend hardware, so I don't really mind needing to do this.....

---

### Post by fragos on 2008-06-07
Although some software, i.e. Firefox, has crashed while the window was grey, with compiz at least grey is a visual state that indicates the application is slow to respond compared to other applications. For example when you do a search runing the Synaptic package manager it will frequently grey out and return to normal visual when the search is complete.

---

