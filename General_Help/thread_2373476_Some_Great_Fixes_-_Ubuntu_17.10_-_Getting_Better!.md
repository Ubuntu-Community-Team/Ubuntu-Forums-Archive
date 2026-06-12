---
title: "Some Great Fixes - Ubuntu 17.10 - Getting Better!"
date: 2017-10-06
forum: General Help
---

### Post by markackerman8@gmail.com on 2017-10-06
I prefer to give good news as yo bad so here is my update - **HAPPILY**

Slow to Shutdown                                                   - ** NOT Fixed**  Still  hangs for more than a minute
Slow to boot    (to Login Screen                 -** Fixed**)
Slow to log in  (Still takes 30-40 MORE seconds!)  -** NOT Fixed**
Slow to Log out                                        -** Fixed**
Slow to launch ANY APP - ANY APP!            -** Fixed**
Download speed is fine (wait going to check - nope Super Fast as it should be)
Suspend not working properly                    -** Fixed**
Extensions not working well                             -** Fixed**  at least MUCH better
- not remembering Workspace Allocation           -** Fixed**  at least MUCH better
- Application Launcher not working (My Bad - I was wrong) 
                                                              -** Fixed**  
Wayland not working at all                                       -**NOT  Fixed**
Display not remembering its Previous Settings    -** Fixed**  at least MUCH better

Perhaps they are reading this! 
Good Job Ubuntu Team :P

Trying to be constructive, Mark

---

### Post by dino99 on 2017-10-06
Wayland not working at all -NOT Fixed  :lolflag:

read the many wayland comments, fully satisfied, and the workaround for some pkexec apps  ;)

---

### Post by markackerman8@gmail.com on 2017-10-06
And If I may add (great to have someone listening for a change)

** Somewhat  Fixed**  Hurray !!
The biggest reason for my hopeful switch from good Ole' Ubuntu-Gnome 16.04.3 LTR to Artful Aardvark
was to hopefully get rid of Screen Tearing with Nvidia - which has plagued Linux for over 2-3 years.
** Somewhat Fixed**   Hurray !!


Before you say it's Nvidia's fault, lets look at the reason.  Simply getting VSync to work on any Optimus Laptop with Proprietary Drivers.
Please remember,
90% of ALL high end laptops in the past 3 years ARE Optimus
70% of All high end laptops in the past 3 years USE a Nvidia discrete GPU for Performance (along with Intel's for passthrough)

And since Wayland is reported to be able to get VSync working properly and eliminate Screen Tearing let's not put all the blame on Nvidia,

Please keep up the good work, and try and fix this relatively SIMPLE, pervasive, and sad stain on Linux!

Ever Hopeful,
Cheers, Mark:eek:

---

### Post by wildmanne39 on 2017-10-06
If you really want these things fixed or to help please see if there are bug reports and add your name to the list or create a new bug report for each issue if there is not one, just posting here really does not help.

You can find information at the top of the page in Ubuntu Development for how to report bugs.

Thanks

---

### Post by mc4man on 2017-10-06
> **markackerman8@gmail.com said:**
> And If I may add (great to have someone listening for a change)

** Somewhat  Fixed**  Hurray !!
The biggest reason for my hopeful switch from good Ole' Ubuntu-Gnome 16.04.3 LTR to Artful Aardvark
was to hopefully get rid of Screen Tearing with Nvidia - which has plagued Linux for over 2-3 years.
** Somewhat Fixed**   Hurray !!


Before you say it's Nvidia's fault, lets look at the reason.  Simply getting VSync to work on any Optimus Laptop with Proprietary Drivers.
Please remember,
90% of ALL high end laptops in the past 3 years ARE Optimus
70% of All high end laptops in the past 3 years USE a Nvidia discrete GPU for Performance (along with Intel's for passthrough)

And since Wayland is reported to be able to get VSync working properly and eliminate Screen Tearing let's not put all the blame on Nvidia,

Please keep up the good work, and try and fix this relatively SIMPLE, pervasive, and sad stain on Linux!

Ever Hopeful,
Cheers, Mark:eek:
Well there is no wayland session for optimus devices in 17.10 so what are you talking about?

However it is possible to remove tearing in the xorg session though that remains something a user has [to set up]("https://ubuntuforums.org/showthread.php?t=2365449").

---

### Post by markackerman8@gmail.com on 2017-10-06
Some Other Things Developers,

Another thing plaguing Gnome **for over 5-7 YEARS !!** is its' inability to remember a session after a reboot.
This is somewhat moot as Suspend and Hibernate somewhat solves this.
But as we all know Ubuntu is prone to needing many reboots for every kernel++ etc, etc, 
(of course this specific problem is fixed if you use Ubuntu's AWESOME free Live Patch - but only for LTR's (sadly and somewhat stupidly)
so can we get Live Patch working for this historic (non-LTR) version of Ubuntu?? or KSplice, Kpatch etc etc, but open source for Ubuntu?

Having said this a great solution 7 years later came in the form of an extension, specifically 
"Auto Move Windows" Extension which tries to rectify this other seemingly SILLY stain on Gnome.
now to my specific point 
"Auto Move Windows" is not working well in 17.10, it settings options are NOT WORKING,
no doubt it will get fixed soon, but I though it worth pointing out I hope.

but Happily MOST others ARE .... AWESOME! 

trying to help
Mark

---

### Post by markackerman8@gmail.com on 2017-10-06
And Apps are now opening up Lightning Fast as expected,

Awesome, Mark

---

### Post by Chanath on 2017-10-06
> **markackerman8@gmail.com said:**
> 
Having said this a great solution 7 years later came in the form of an extension, specifically 
"Auto Move Windows" Extension which tries to rectify this other seemingly SILLY stain on Gnome.
now to my specific point 
"Auto Move Windows" is not working well in 17.10, it settings options are NOT WORKING,

Extensions, I believe, are the problem of the extension creators, and the users, who install them, not the 17.10 devs. You may have to tell [fmuellner]("https://extensions.gnome.org/accounts/profile/fmuellner") at [http://git.gnome.org/gnome-shell-extensions](http://git.gnome.org/gnome-shell-extensions) 

For example, Hide Top Bar troubles Ubuntu Dock, for it'd go underneath, but its not an Ubuntu devs' problem as it becomes the problem of those, who install it. I like to hide the top panel, and all I can do is ignore the visual problem.:)

---

### Post by markackerman8@gmail.com on 2017-10-06
> **Chanath said:**
> Extensions, I believe, are the problem of the extension creators, and the users, who install them, not the 17.10 devs. You may have to tell [fmuellner]("https://extensions.gnome.org/accounts/profile/fmuellner") at [http://git.gnome.org/gnome-shell-extensions](http://git.gnome.org/gnome-shell-extensions) 

For example, Hide Top Bar troubles Ubuntu Dock, for it'd go underneath, but its not an Ubuntu devs' problem as it becomes the problem of those, who install it. I like to hide the top panel, and all I can do is ignore the visual problem.:)

Good Point, and Yes I knew that but thanks for the link - I will throw it in their with the details in the console type psmall window that opens up.

I am so glad this thread is getting listened to - AWESOME.

Question? - Why would the most common type of laptop (Optimus) not get Wayland Support - No Worries -Just kinda curious.  I will just have to wait until they figure it out - perhaps the same complication is why Nvidia Screen Tearing has caused Optimus Laptops for over 2-3 years.

Thanks for your :P input, Mark

p.s. To be more clear - Don't you think a sophisticated Gnome GDM should have its' own Session Save Ability like KDE does so effortlessly and continuously for the past decade?  I guess this is what I was getting too.

p.s.s.Don't get me wrong - your Extensions are in my opinion what is making Gnome the best Linux DE ever and perhaps will even take over MS!:P
p.s.s.s. Posted on your suggested link - Thanks Chaneth!

---

### Post by markackerman8@gmail.com on 2017-10-09
restate - get a Gnome session manager that saves a session on REBOOT!  Please!

Suspend is not working from the top RHS menu, but it is from Cairo-dock (but not well - screws up windows and/or resolution ALWAYS!)

Just trying to help

---

### Post by markackerman8@gmail.com on 2017-10-09
reboot still sketchy often when shutting down
startup to login screen                            **FIXED, Fast ... 20 seconds**
login            -  SLOW             **40 seconds**

top bar "Pause" and "Shutdown"                    **NOT WORKING**

re-iterating the aforementioned issues still plaguing
gnome-session restore unavailable (my pet peeve for 7 years)
a great solution from gnome-shell-extensions "Auto Move Windows"  NOT WORKING nearly as well as in Ubuntu-Gnome (which itself only works for 70-80% of apps - in Ubuntu 17.10   10-20% of apps and no settings working)
and yes I told the maintainer already.

Getting tired of this, and tried to get into my Ubuntu-Gnome session but this 17.10 install has pooched it (and yes I know I can reinstall)

Oh well I will wait this out 
Release Candidate — October 12th.
Ubuntu 17.10 final release — October 19th.

Good work Ubuntu, Mark

---

### Post by markackerman8@gmail.com on 2017-10-09
Good News -

Screen Tearing is almost non existent - WooHoo!  

Possibly just my imagination or hopeful thinking - We'll see after a few reboots/days/ if it is indeed real.

:P Cheers, Mark

---

### Post by timrichardson on 2017-10-12
Hi Mark, nvidia tearing on optimus is already fixed, but you need to enable modesetting for the nvidia driver. Bad news is that this doesn't work with gdm3. No one seems to know why, but wayland and nvidia is not working very well for Optimus. Actually, it's not working at all based on my experience over the past month. So we are stuck on X. However, this seems to work really well these days. You can get tear-free Optimus on 17.04 and the latest 16.04 (in both cases, not with Wayland).

---

### Post by markackerman8@gmail.com on 2017-10-12
For the record,

I was just getting frustrated with a few persistent problems. And i was about to install Ubuntu-Gnome 16.04.3 AGAIN as 17.04 has somehow made this partition unbootable, but here is the good news and a few solutions, and a few problems outstanding(not so big - WooHoo):
1/  TeamViewer not connecting to network, 
Not Ubuntu's Fault apparently, - temporary fix
Solution
> sudo teamviewer daemon stop
sudo teamviewer daemon start
works until a reboot

2/ Suspend/Logout NOT working from Top Bar

Solution:
Use cairo-Docks Logout Button they all work there,

Problem:
the return from Suspend kills the awesome "Workspace to Dock" Extension

Solution: 
other than rebooting (messy), restarting X solves this.

trying to help, MARK :cool:

---

### Post by cariboo on 2017-10-12
I sure hope you are creating bugs on [https://bugs.launchpad.net](https://bugs.launchpad.net)

---

### Post by IanW on 2017-10-12
I have a small warning. Today's update switched me from my preferred KDE desktop to Gnome _without warning!_.

Attempting to boot into KDE from gdm results in a mouse on a black screen.

EDIT:- Looks like I was missing a dkms update. Also a "sudo dpkg-reconfigure sddm" helped

---

### Post by markackerman8@gmail.com on 2017-10-12
In case any developers are reading this:

Problem:
- reboot results in boot error

Solution 1/  Don't have usb HDD on top bootup device (never a problem with any other Distro)
Solution 2/  Unplug external HDD's on reboot              (never a problem with any other Distro)

Could cause others to lose faith in Ubuntu 17.10

I will try to find a way to post this on 
[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

Does not seem as user friendly at all

Cheers, Mark

---

### Post by markackerman8@gmail.com on 2017-10-12
For others looking to report a bug ...
just email: [https://bugs.launchpad.net/](https://bugs.launchpad.net/)
and apparently it gets reported, hmmmm we'll see.:confused:

it got rejected because I did Not add
"space affects Distro/App if applicable"
my ex) " affects Ubuntu 17.10 Beta"
the distro was stated in the body but it needs to be done that way
and no return error with that at the top (at least so far)

Perhaps - this channel will get the attention of Ubuntu Developers?
Any thoughts on this?

Thanks, Mark

---

### Post by ventrical on 2017-10-13
> **markackerman8@gmail.com said:**
> For others looking to report a bug ...
just email: [https://bugs.launchpad.net/](https://bugs.launchpad.net/)
and apparently it gets reported, hmmmm we'll see.:confused:

it got rejected because I did Not add
"space affects Distro/App if applicable"
my ex) " affects Ubuntu 17.10 Beta"
the distro was stated in the body but it needs to be done that way
and no return error with that at the top (at least so far)

Perhaps - this channel will get the attention of Ubuntu Developers?
Any thoughts on this?

Thanks, Mark

Hi Mark,

There are some developers who are reading the threads. Jbicha is often examining several of the threads and Will Cooke is linked into the unity7 testing while others stop in from time to time from the desktop team to examine the threads but do not use ubuntuforums as their main resource as there are several mailings list and other forum methods that they use.

As admin of the Ubuntu Development Version testing Team I will often send links from Ubuntu forums to  developers if they are of critical concern. 

Regards..

---

### Post by ventrical on 2017-10-13
@mark,

Do you have a launchpad account?


Regards..

---

### Post by cariboo on 2017-10-13
> **markackerman8@gmail.com said:**
> For others looking to report a bug ...
just email: [https://bugs.launchpad.net/](https://bugs.launchpad.net/)
and apparently it gets reported, hmmmm we'll see.:confused:

it got rejected because I did Not add
"space affects Distro/App if applicable"
my ex) " affects Ubuntu 17.10 Beta"
the distro was stated in the body but it needs to be done that way
and no return error with that at the top (at least so far)

Perhaps - this channel will get the attention of Ubuntu Developers?
Any thoughts on this?

Thanks, Mark

This:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

will help you create valid bug reports.

---

### Post by markackerman8@gmail.com on 2017-11-05
For the record, Good News,

ALL is working PERFECTLY in Ubuntu 17.10 now it's finally out and a couple weeks later.

at least 95% anyway.

If you have issues with one or many of the Awesome Gnome-Extensions, MANY do not work when logging into Ubuntu, so log out and choose the "Gnome on Xorg" or Gnome Wayland version if you are lucky enough to get this working.

Good Work Ubuntu Developers!

Trying to help, Mark :P

---

