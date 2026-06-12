---
title: "J-Pilot Sync"
date: 2005-05-27
forum: General Help
---

### Post by tegrady on 2005-05-27
I don't want to use Evolution as a PIM, and want to use J-Pilot instead and export my contacts to Thunderbird.  Here's my problem.

I can sync my Palm Zire 32 fine with Evolution, but it won't sync with J-Pilot.  I have installed jpilot and jpilot-plugins, but the available conduits in PalmOS Devices are still just the Evolution ones.

How do I get my Palm to sync with J-Pilot and not Evolution?

---

### Post by jonrkc on 2005-05-29
When you installed or began to use Evolution, there must have been made a default setting somewhere that sets Evolution as the client that works with your Zire.  I never used Evolution, and JPilot (which I've used forever) worked right away with my Tungsten E.

I think you will find in KDE and also in Gnome a control panel service that allows you to change the designated client from Evolution to JPilot. Since I've never had to do it, I can't say exactly where it is, but I'll bet it's there.  If you can't find it, post back and I'll fire up KDE and/or Gnome Desktop and poke around.  I normally use IceWM so I don't have those panels handy right now.

---

### Post by chascon on 2005-05-29
> When you installed or began to use Evolution, there must have been made a default setting somewhere that sets Evolution as the client that works with your Zire
I tried jpilot first as per some ubuntu wiki but it never worked on ppc.  Thus, my use with Evolution.
I don't think it is some switch that controls this.

---

### Post by jonrkc on 2005-05-29
In your Pilot preferences > settings panel, do you have the device set as /dev/ttyUSB1? It seems from what I've read that often JPilot fails to see the device it's supposed to work with.  I wonder if that's what's happening.  I used to use /dev/ttyUSB0 but for some reason with the setup I have now, it needs to be /dev/ttyUSB1, and (again from what I've read) that seems to be the most common usage.

---

### Post by tegrady on 2005-05-29
All that I can find is System->Preferences->PalmOS Devices.  The only thing that it allows me to do is enable or disable the existing conduits, not add the Jpilot ones in. 

I don't think that I need to change any of the device settings as I can sync with Evolution OK.

---

### Post by jonrkc on 2005-05-29
[QUOTE=tegrady]All that I can find is System->Preferences->PalmOS Devices.  The only thing that it allows me to do is enable or disable the existing conduits, not add the Jpilot ones in. 

I don't think that I need to change any of the device settings as I can sync with Evolution OK.[/QUOTE]
 I've had JPilot fail to recognize my Palm device when other apps (namely the Pilot-Link suite itself) could.  I've posted a screen-shot of the Preferences dialog in my JPilot with the Settings tab opened, at
[http://www.jonrkc.com/my_images/JPilot_screen_shot.jpg](http://www.jonrkc.com/my_images/JPilot_screen_shot.jpg)
to show what it looks like in my version.  Here is the information about my version, obtained from 
jpilot -v   ---
J-Pilot version 0.99.8-pre6
 Copyright (C) 1999-2004 by Judd Montgomery
 [email]judd@jpilot.org[/email], [http://jpilot.org](http://jpilot.org)
J-Pilot comes with ABSOLUTELY NO WARRANTY; for details see the file
COPYING included with the source code, or in /usr/docs/jpilot/.

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; version 2 of the License.

Date compiled Nov 28 2004 04:01:45
Compiled with these options:
 Installed Path - /usr
 pilot-link version - 0.11.8
 USB support - yes
 Private record support - yes
 Datebk support - yes
 Plugin support - yes
 Manana support - yes
 NLS support (foreign languages) - yes
 GTK2 support - yes

---

### Post by tegrady on 2005-05-29
Thanks for the help jonrkc.  It's folks like you who are willing to help that will make Linux and OSS move forward.  But I'm back to square one, now I'm not syncing at all!  What a huge pain this is becoming.  Maybe I'm not following the sequence properly.  Should I press the sync button in JPilot and then the Sync button on my Palm or the other way around?  Or should the sync button on my Palm initiate the sync on Jpilot (like Evoloution was working previously)?

This is a great example of why a lot of organizations and individuals are slow to adopt Linux and OSS.  I am a fairly seasoned computer professional with 11 years in the PC and networking field.  Most of my experience is with Novell NetWare, Windows, Mac and Routing/Switching.  I'm really excited about Linux and have been playing with it off and on for a few years.  I've finally decided to just format my primary home workstation and go whole hog.  I've had similar issues with several distros (Suse, Mandrake and Fedora)  I actually derive some sick pleasure from digging in to problems and coming out the other side with a solution, but your average person has absolutely no desire to spend  hours and hours making their Palm sync properly.

---

### Post by jonrkc on 2005-05-29
First, I agree totally with your take on Linux difficulties being a hurdle the average, or even quite-a-bit-above-average home computer user is not willing to jump.  And that goes for businesses, too: They're not going to be willing to spend expensive person-power on troubleshooting and tweaking all day.  I always get criticized by the crowd that says, "If you want something simple, just stick to Windows."  Well, for me not using Windows is a moral issue, not one of easy versus hard.  I will not use Windows because I believe the philosophy and practices behind it are predatory, greedy, and just plain not RIGHT.

Now as to the sync issue, the procedure is to press the "button" on the Zire or Tungsten first, wait about four or five seconds for the system to awake from its complacency and recognize the connection, and THEN select the "sync" button in JPilot.  It's the only way it will work, as far as I know.  

I certainly understand your frustration with getting the Palm device to work right.  I've spent hours and hours fiddling with this and that.  I was very surprised when it worked right off the bat after I switched from Mandriva to Ubuntu.  I fully expected to spend a day or two--again--getting things set up right.

---

