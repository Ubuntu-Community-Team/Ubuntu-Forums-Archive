---
title: "Joining a meeting at gotomeeting.com"
date: 2007-12-16
forum: General Help
---

### Post by Debbie on 2007-12-16
I am part of a group of people who are conducting meetings online through GoToMeeting, and I would like to participate, but have been unable.  I did not choose that application for teleconferencing, but apparently all of the other participants use Windows, so I am outnumbered.  My problem is not necessarily with Linux, but with the [http://gotomeeting.com]("http://gotomeeting.com") website.  When I click on the button to join a meeting, some script apparently checks my operating system and redirects me to a page telling me that I need to use a *supported os* (Windows or Mac).  I contacted GoToMeeting support, only to be told that their teleconferencing will not work on Linux, and they *might* eventually come out with a Linux version if there is enough interest.  I am NOT asking GoToMeeting for support with an installation.  All I want to do is TRY to go to a page on their site without being stopped by that #!@*! script.

Now for my questions.  Is anyone familiar with the GoToMeeting application?  My understanding is that the part to create meetings has to be purchased after a 30-day trial period, but anyone is supposed to be able to *join* a meeting through their website for free.  Is there any way to get around that os checking script to at least see if it will work?  I have tried disabling java and javascript in my browser, and using Internet Explorer running through WINE to try to trick the site into letting me in, but had no luck. If this application runs through their website, I would not think it would matter what os was being used.  If some client application needs to be downloaded to my computer first, does anyone know where I can get it?  The only place I see is the official website, and they will not let me get to a download page after they check the os.  Thanks.

---

### Post by tshrinivasan on 2007-12-19
Hi,

gotomeeting.com checks the OS first.
because, it installs some ActiveX controls in the system.

ActiveX is the technology by MS, so it supports only Windows.

ActiveX controls can not be installed in linux.

So, gotomeeting.com wont work under Linux.

---

### Post by atomkarinca on 2007-12-19
Your best bet would be opening the page using [ies4linux]("http://www.tatanka.com.br/") but I just tried and no go, sorry.

---

### Post by Debbie on 2007-12-20
Then is there a way to use ActiveX through WINE?  I am just miffed that their website will not even let me download anything to see if it will work.

---

### Post by atomkarinca on 2007-12-20
Yeah, that's the problem. It's not doing an ActiveX check, it's doing an OS check. Maybe you can report this to the admins and they change it.

---

### Post by zaphod777 on 2007-12-20
you may want to run XP in virtual box for these issues when there is no other choice. I wish more sites would support open source multi platform browsers.

---

### Post by stewballs on 2008-03-05
Hi,

I subscribe to GoToMeeting for my [company ]("http://www.netforttechnologies.com") and i was stopped having an online conference with a French organisation because of this limitation. 

Webex support a similar product that will support linux platforms, namely Ubuntu 7.04 and Red Hat,etc.

you could always try those.

Stuart

---

### Post by wormser on 2008-04-23
I created a brainstorm for Ubuntu to develop their own version.

[COLOR=Red]**Vote for it here:  [http://brainstorm.ubuntu.com/idea/7487/](http://brainstorm.ubuntu.com/idea/7487/)**[/COLOR]

---

### Post by kweiner on 2008-05-07
I have been frustrated by GotoMeeting's lack of support for Linux as well.  I recently discovered an alternative cross-platform product called Yugma.  Check it out: [http://www.yugma.com/](http://www.yugma.com/)  I think there are a few features that aren't yet working in Linux, but full support is on the roadmap.

---

### Post by smithbt5 on 2008-06-09
I was looking at switching my wife's pc to Ubuntu, but she requires the use of GotoMeeting.  While looking at their website, I noticed that they now support Mac in their newest version.  That indicates that they aren't installing an ActiveX on all platforms.  Anyone try this lately on Ubuntu?

---

### Post by cashmoney on 2008-06-18
> **smithbt5 said:**
> I was looking at switching my wife's pc to Ubuntu, but she requires the use of GotoMeeting.  While looking at their website, I noticed that they now support Mac in their newest version.  That indicates that they aren't installing an ActiveX on all platforms.  Anyone try this lately on Ubuntu?

Just did and no go.  I was searching for a way to try to bypass the BS and came across this thread.

---

### Post by muamw10 on 2008-06-26
You can bypass their OS check by modifying the about:config page in firefox and setting "general.useragent.override" to
"Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9) Gecko/2008052906 Firefox/3.0"

It gets you to the point of being able to download a g2m exe file.  I tried it under wine and it was a no-go.

-Andrew

---

