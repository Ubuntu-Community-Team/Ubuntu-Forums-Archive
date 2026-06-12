---
title: "Ubuntu server as a NAS/media server (n00b help, please)"
date: 2008-03-17
forum: General Help
---

### Post by monsterthrash on 2008-03-17
Wasn't too sure where to post this...

I have in mind a little project that i'm definitely going to need some help with due to my lack on Linux Ubuntu experience.  I was thinking about using FreeNAS for a NAS build but i've been thinking that i'd like to do more than just use it for storage (subversion repository, web server, etc) so I think running an Ubuntu server would be a smarter choice.  I have some questions, though:

1. Is it possible to install an Ubuntu server on a Compactflash card?  How small, generally?

2. How do I create a software RAID-5 array and manage it (rebuild if necessary, etc)?

3.  Right now on the Windows side I use TVersity to stream and transcode content (if needed) to my PS3.  Is there a Linux equivalent?

4. I'd like to run the server headless (no monitor) and manage it remotely.  How would I set this up?

5. What hard drive power saving options would I have?

I know it's probably a lot of material to cover but my Ubuntu/Linux experience is limited and I think it'll be the best choice for what I want to do.  I probably have more questions but this is all that's coming to mind right now.

Thanks!

---

### Post by DoctorMO on 2008-03-17
1. Yes

2. Unknown, search for software RAID 5 guide and howto as it's quite an advanced topic.

3. Depending on the protocol, you can use mencoder to transcode media if required, transmission though is unknown.

4. Investigate ssh and the use of using logon keys, if you want remote gui you can search for remote X forwarding (-X option) or you can use VNC.

5. The bios sets hard drive power management, linux tends not to touch them so you'll have to investigate that with your motherboard.

hope this helps, sorry it's not complete.

---

### Post by Ecclesia on 2008-03-17
Hi there,

You might have better luck posting each of these questions as a separate post after you do a search of the forums.  I have had better luck searching with google than with the forum search function, but either should give you something to look at.

1) There are a couple linux distros that are meant to work as a server via flash drive.  I'm not sure if someone has done this with Ubuntu or not.  I'm sure it's possible, it's just not likely to be terribly small - last I looked into this I only saw people doing this for the desktop.  I'm guessing that you could do it with 1gb or less if you were going without desktop functionality, but I don't have any experience with this.  You might want to look into something like NimbleX that's made for this type of thing.

3) I have used mediatomb for streaming media content.  Its newest version can transcode.  It's likely that it would work with a PSP.

4) There are three major ways of doing this, SSH, web gui, and VNC.  I use VNC to do this - I have my media server connected to the stereo and then use VNC to turn a nokia tablet into a remote control for the computer.  If I weren't doing this I would want to administrate it via the web gui.

The first thing that I would do if I were you would be to check out FreeNAS.  It's unbelievably easy to configure (compared to installing a version of Linux and trying to figure out what all your settings should be) and it sounds like it's built to do exactly what you're talking about.  The web gui is nice and fairly easy to understand and it has a fairly easy set up for RAID.  I believe it has mediatomb built in now.  Come to think of it, maybe it works on a flash drive.  It does work off a live cd... 

I would use it if I didn't want to use my box as a music player.

Good luck.

---

