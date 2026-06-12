---
title: "Live tv without internet"
date: 2024-11-04
forum: General Help
---

### Post by docstafford on 2024-11-04
Greetings all. Can anyone tell me if it is possible to use my Ubuntu powered laptop towatch live tv without an inter et connecfion? I presume a tuner dongle with an
antenna is needed along with appropriate application. Will be used in case of electrical outage.

---

### Post by ajgreeny on 2024-11-04
Yes, you will need a TV tuner usable in your country to receive broadcasts.
You will, of course, only be able to do this using a laptop with a usable battery or some other power supply.

---

### Post by joey-elijah on 2024-11-04
> **docstafford said:**
> Greetings all. Can anyone tell me if it is possible to use my Ubuntu powered laptop towatch live tv without an inter et connecfion? I presume a tuner dongle with an
antenna is needed along with appropriate application. Will be used in case of electrical outage.

Yeah, a dongle type thing (make sure it's one that works with Linux), a cable, and an antenna - and then software.

I think /most/ Linux users use software called *TVHeadend. *It's a bit complicated to set up as it's a server (a background process) and you will need to use the 'client' to connect to the server (running locally) to watch stuff, browse the EPG, and record (if you wanted). Much of the online documentation/blog posts/how to focus more the 'server streaming to other devices' feature as the tool is popular with users of Linux-based media centers, Raspberry Pi, etc but it can be used to watch TV *without* internet on the same device the server part is installed. 

Easier options may exist though! 

In Europe I know VLC, mplayer, and a few other media players did work with DVB tuners. I'm not sure if that's the case any more, but that'd be worth looking in to.

---

### Post by crip720 on 2024-11-04
A tv antenna suitable for your area is needed.  In the US/Canada the web site tvfool is useful to finding out the tv channels available for your location.  If you can receive tv stations at your location, you can search for tv dongles available for Ubuntu, or just attach the antenna to a tv.   Some locations(outside of cities/towns) require a signal  booster on the antenna to bring in stations plus a antenna turner(or climb up and turn by hand) to turn the antenna, so a car battery plus a small inverter would work.   There might be cable dongles available, but I do not have cable so never bother to search about them.  TV antennas are under the Location ,location, location matters area.  Being in a valley is a bad location.

---

### Post by deadflowr on 2024-11-05
Thread moved to General Help.
You originally posted in the Tutorial sub-forum which is not quite what it's for.
Because of the mixed nature of the thread as you'll be needing both hardware and software to get what you want, 
I felt it wasn't right to move it into either o the Hardware subforum or the Multimedia Software subforum.


In terms of what you want, in the USA, broadcast uses the ATSC format (or standard or whatever they call it).
So you'll need a tuner dongle that can handle that.

VLC works, but there are other apps too.
I would choose something like vlc over apps like tvheadend or mythtv as those require more work for little payoff for what you need.
And I doubt you want a complex database running.

As far as antenna go, you'll need to find a way to keep it stationary and stable once you figure out how to get a good signal.
Digital antenna signals are fickle to movement.

---

### Post by docstafford on 2024-11-05
Thanks, best regards.

---

