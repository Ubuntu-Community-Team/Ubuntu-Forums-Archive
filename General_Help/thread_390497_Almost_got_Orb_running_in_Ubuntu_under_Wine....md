---
title: "Almost got Orb running in Ubuntu under Wine...?"
date: 2007-03-22
forum: General Help
---

### Post by n00buntu NJ on 2007-03-22
I won't make any claims about having any kind of skill hacking anything.
I was just making a passive attempt at installing this new Orb media server app, which would allow me to stream media from my PC to my Xbox360.
None of the other solutions work under wine in Ubuntu, but this one might work...?

[http://www.orb.com/gamers/xbox.htm](http://www.orb.com/gamers/xbox.htm)

Check it out.  I downloaded the .exe and just tried to install it - with no luck.
Running the ~/.wine/drive_c/Program Files/Orb Networks/Orb/bin/Orb.exe in the terminal returned a bunch of errors about the following .dlls:

wmvcore.dll
GdiPlus.dll
msvcr80.dll
WMASF.dll

After some trial and error I uninstalled the Orb application via the provided "uninstall.exe", then I found that if I copied the above stated dlls from a machine running XP into the ~/.wine/drive_c/windows/system32/ directory, and ran the installer again I made some progress.
Now I was greeted with a configuration dialog during the installation.

At the prompt for your Orb account it generates an error, but if you follow the "Create Account" link, you can complete the installation, and OrbTray.exe will be executed, appearing in the Notification Tray.

From here I couldn't make any progress.  The Xbox360 still can't see my PC, although I was getting excited.

If anybody else out there could give me some pointers, or would also like to give this a shot - I'd love to hear about it.

Thanks 

OH - BTW, I'm running Ubuntu Edgy (Gnome) / wine 0.9.33 ... I'm not sure what other info will help...

Thanks again...

---

### Post by priegog on 2007-04-27
Bump, and I am quite interested too... Actually I'm surprised there isn't an equivalent program for linux since it really seems it wouldn't be that hard to do. If I am missing something and somebody knows of a replacement for Orb, please let me know, as it is one of the thing I most miss about windows.

---

### Post by blamecanada on 2007-04-27
Seems like the poblem is in the system try icon, perhaps you can run that through wine as well, although will it work with gnome-pannel?

---

### Post by CrossCrucial on 2007-06-04
any progress? I currently you Orb to stream to my 360 from XP. I think running it through an XP virtual machine would be crap because the transcoding for the stream to the 360 is very demanding.

Glad to hear someone is working on this.

---

### Post by Ralob on 2007-07-02
Any more progress on this front? I would also love to stream Orb to my 360.

---

### Post by RockTonic3 on 2008-04-07
bump.  orb is awesome, except that i have to boot to windows to use it.  ubuntu needs an equivalent.

---

### Post by priegog on 2008-04-07
> **RockTonic3 said:**
> bump.  orb is awesome, except that i have to boot to windows to use it.  ubuntu needs an equivalent.
There is an equivalent: mythtv, but it's a pain in the *** to setup.

---

### Post by msmollin on 2008-04-10
If I may offer a FOSS:
[http://en.jinzora.com/](http://en.jinzora.com/)

It does everything Orb does (well except put your content on a central server), and works on ubuntu natively since its just a web site.

This person did a pretty nice guide for setting it up on 6.10. I'm sure we could figure it out for 7.10 or 8.04: 
[http://rubbervir.us/projects/ubuntu_media_server/](http://rubbervir.us/projects/ubuntu_media_server/)

--Matt--

---

### Post by fain on 2008-04-10
> **msmollin said:**
> If I may offer a FOSS:
[http://en.jinzora.com/](http://en.jinzora.com/)

It does everything Orb does (well except put your content on a central server), and works on ubuntu natively since its just a web site.

This person did a pretty nice guide for setting it up on 6.10. I'm sure we could figure it out for 7.10 or 8.04: 
[http://rubbervir.us/projects/ubuntu_media_server/](http://rubbervir.us/projects/ubuntu_media_server/)

--Matt--

That looks pretty cool but i really want a Live tv streamer. Gmyth offers some hope but its still hard to set up and not up to par yet.

---

### Post by hartland08 on 2008-05-10
I tried installing this on ubuntu hardy today and it harps on me at the regsvr32.exe it does this like 3 times while installing then the config. wizard comes up fine but my system fails while trying to do system check. It comes up with Cab error.....saying to check my network connections and that my firewall? (which i didn't think i have) might not allow cabdirectory and all Orb processes. Try restarting cabdirectory service. Then it pops up with later could not connect to internet.

We've been waiting for a Linux version of this program long enough.

---

