---
title: "opera/firefox/pidgin crashing constantly"
date: 2007-12-10
forum: General Help
---

### Post by zonedate on 2007-12-10
A few months ago I switched 100% from XP to Ubuntu but i have recently started to have problems with browsers and Pidgin shutting down unexpectedly, for no apparent reason.  Either that or the app will freeze and grey-out, so I have to force-quit the program. Up until this morning I thought it was strictly a probelm with Firefox and possibly with the fact that I have used Automatix to install a lot of codecs - but I have had no problems up until now.  So I installed Opera, and after a few hours with no issues I have started to have the same problem - the app closes / crashes / freezes constantly. Opera also runs extremely slowly - I can click on a link or right click to get a menu, and there is a significant pause between my click and any response.

When I force-quit Opera and try to restart i get this message box:

"It appears another opera instance is using the same configuration directory because its lock file is active: /home/(my name)/.opera/lock
do you want to start Opera anyway?"

So now I'm perplexed. I'm wonderring if there are instances of other apps running in the background that are responsible for my issues and would like to know how I can find  and how I can kill thes un-needed processes.

---

### Post by itsjustarumour on 2007-12-11
> So now I'm perplexed. I'm wonderring if there are instances of other apps running in the background that are responsible for my issues and would like to know how I can find and how I can kill thes un-needed processes.

Hi zonedate,

Have you looked under System>Adminstration>System Monitor?  

Thats the Ubuntu equivalent of pressing Ctrl+Alt+Del in Microsoft Windows and selecting "Task Manager" - you can check what processes are running on your machine, and kill any that have stopped/crashed.

Also - post up some basic specs for your setup, so we can get an idea how fast things ***ought*** to be running!  :-)

itsjustarumour

---

### Post by itsjustarumour on 2007-12-11
Also, I just found a possible solution to your error message on the Opera forums at [http://my.opera.com/community/forums/topic.dml?id=200961](http://my.opera.com/community/forums/topic.dml?id=200961)

Go to /home/(your user ID)/.opera and delete the file named "lock" (with Opera closed)  :-)

---

### Post by pieisgood4589 on 2007-12-11
Yes, Automatix BREAKS YOUR SYSTEM. Nobody should be using it. I don't get why people even do use it. It frequently completely ruins your Ubuntu computer after updates.

---

### Post by zonedate on 2007-12-12
Thanks for the responses, I did not know about System Monitor, and did not see it in the Ubuntu Book.  I'm heading over to the Opera forum next,  but the issue started with Firefox. I only installed Opera after I began having issues. Last night I turned off the Visual effects and  rebooted the sytem. so far, so good (no crashes today, but I haven't used it as much as I did this past weekend).

_** This is what I'm working with:**_

Ubuntu 7.1
Kernel Linux 2.6.22-14-generic
Gnome 2.20.1
System updated almost daily.
*** Automatix installed ***
[COLOR="Blue"]*** Google Desktop Recently Installed ***[/COLOR]
Visual Effects set to "None"
---
Dell Dimension B110
2.0 gb RAM
Celeron 2.53 GHZ
160gb HDD/129.3 Available, (5.8 gb Swap
17"  Monitor, onboard audio and video
---
XMMS/Streamtuner is usually running in the background, 24/7
I use Opera 9.24 or Firefox 2.0.0.11
Firefox Extensions: Delicious/StumbleUpon/Google Toolbar/Facebook Toolbar, Adblock Plus, Flashblock, Forecastfox, Ubufox
The apps I use are: Screem, Gftp, Tomboy Notes, and "Text editor", often all at the same time.
I have been doing this for months with no problem, so its not my hardware.

As for Automatix, for newbies like me it is the easiest way to install all of the codecs we want and use.  I've read about the latest comments concerning how it can't be fixed well enough to become supported, so I think it's obvious that a replacement is needed.  How would I know if Automatix is the cause of my problems?

Thanks again for all the help and information.

---

### Post by rahimveron on 2007-12-12
Why use Automatix which is discouraged from other users when installng appz is so easy with Synaptic Package Manager? Codecs, Java, Flash,etc are all there in the reposotories. Just select them and install. Believe me it is now a myth that appz are difficult to install in Linux. Each Distro has a package manager which handle your installation enough very smoothly.

---

### Post by itsjustarumour on 2007-12-12
> **rahimveron said:**
> Why use Automatix which is discouraged from other users when installng appz is so easy with Synaptic Package Manager? Codecs, Java, Flash,etc are all there in the reposotories. Just select them and install. Believe me it is now a myth that appz are difficult to install in Linux. Each Distro has a package manager which handle your installation enough very smoothly.

I believe there are still a couple of things that are still only available to install "the easy way" via Automatix - I've had to use it in the past for things like Google Earth and Adobe Acrobat Reader.  I'm not sure what the exact status is now though as I haven't checked what it offers recently, although when Gutsy came out I had to download and compile Google Earth from the Google website as it wasn't available from the official Gutsy repos (or from Medibuntu) at the time (likewise the latest RealPlayer) in an attempt to avoid using Automatix. Its a shame all these things aren't always in the official Ubuntu repositories (or in the "official unofficial" Medibuntu one) as this policy just tempts newbies towards breaking their systems with Automatix.  And downloading and compiling source from third-party websites also has a small but significant chance of breaking your system, chiefly from a lack of dependency resolution.  Being able to install ***everything*** from official Ubuntu repositories using Synaptic would of course be the safest option, its just not always an option thats there unfortunately.

As for telling if its Automatix thats causing problems, I don't think theres any way of telling that.  But if you haven't checked it out already, do take a look at Medibuntu [http://www.medibuntu.org/](http://www.medibuntu.org/)    It is at least tacitly endorsed by Ubuntu as their cheeky way of circumventing legal restrictions on some software, by "not-discouraging" someone else to host it in another country where its legal  ;-)

---

### Post by zonedate on 2007-12-15
Thanks for the info guys, I'm still not sure exactly what has been going on,  but on several occasions when I have had 7+ tabs open in either browser, I have seen my CPU use suddenly skyrocket to 90% then jump to 99%, then the browsers close. 

 I habitually keep POPURLS or Drudgereport open in one tab, then click on multiple stories and then close the main Drudge or Popurls tab - and then I read each article in succession, closing tabs as I go.  I also do this with Google Reader - I open multiple feeds/blogs in different tabs, close the original tab, and then I go through the articles i find interesting.

I have not had issues with this routine until just recently and did not know it was taxing my CPU so much, but I still have no clue why it has suddenly become a problem when it was not a problem before.  Any more troubleshooting advice before I uninstall everything and start over? I am thinking that I will have to either methodically uninstall add-ons/extensions if I want to figure out which one (or combination) is the culprit. I really don't have the time or patience for this so any alternative advice would be MUCH appreciated.

EDIT: Now it's happening in Firefox without any related spikes in resource use. I'm using only one tab, RAm use is around 230mb out of 2gb and cpu use is only hitting 28% (but that's still pretty high)..

---

