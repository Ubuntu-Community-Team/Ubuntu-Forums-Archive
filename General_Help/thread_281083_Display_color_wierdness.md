---
title: "Display color wierdness?"
date: 2006-10-20
forum: General Help
---

### Post by dai on 2006-10-20
Hi - I'm starting to get an occassional problem on my Ubuntu Dapper laptop (Nvidia graphics, no desktop oddness other than murraine)

After leaving my machine on for a while, I occasionally come back to find that the colours in the display have degraded. The best way I can describe it is that it looks like when you run windows in 'safe mode' and only have 256 colors. This is most noticable where I have text boxes or documents open, the white paper becomes a dark grey and the text is impossible to read.

Logging off and then back on usually clears it, but ocassionally fails to and I have to restart the machine.

I've searched the forums and the web but this seems to be pretty rare, if not unique as I am unable to find any information on this problem anywhere.

I would be very grateful for any advice as to what is happening here and how I can prevent it.

Many thanks in advance!

---

### Post by bonzodog on 2006-10-20
This actually sounds like a hardware problem. Could it be the laptop screen, maybe?

---

### Post by dai on 2006-10-20
Doesn't appear to be. I dual boot with Windows XP, but I have never seen a similar problem when forced to use windows for long periods (I do get this wierd headache and intense feelings of despair though, but that may be another issue).

I'm currently thinking it has to do with the way linux suspends/hibernates/sleeps/whatever when you leave it for a while.

---

### Post by dai on 2006-10-23
Bumped.

Interestingly, even when the display is miscoloured and unreadable, when I click the log out icon, as soon as the window giving me options (log out, restart, shut down etc) is displayed the desktop looks absolutely normal behind it. When I exit the window, however, it just goes back to how it was.

I am absolutely stumped. ](*,) 

Also this happens occasionally when I first turn the laptop on, to the extent that the log-in screen is miscoloured and the text is unreadable. i have to log in and then log back out again, and then log in. :mad: 

Very grateful for any help anyone can offer.

---

### Post by dai on 2006-10-27
Further bump. Upgraded to edgy and same problem.

Completely stumped.

Very grateful for any help or suggestions.

---

### Post by edieguez on 2006-10-31
I am having a similar problem I think since upgrading to Edgy. When I start up KDE, all the black colors actually look like the black in Windows when you start it in "safe mode" - its a rainbow of dark greens, reds, etc. Strangely enough if I open up the Nvidia control center the screen blinks and the colors are fixed.

---

### Post by rocktorrentz on 2006-11-02
> **edieguez said:**
> I am having a similar problem I think since upgrading to Edgy. When I start up KDE, all the black colors actually look like the black in Windows when you start it in "safe mode" - its a rainbow of dark greens, reds, etc. Strangely enough if I open up the Nvidia control center the screen blinks and the colors are fixed.

I have this exact problem. However i've been fixing it by changing the monitor driver from 1280x1024@76hz to 1280x1024@74hz and back again then restarting X. I shall try the nvidia method. Do you think it could be an nvidia driver bug?

---

### Post by edieguez on 2006-11-02
I am not sure. Was the NVIDIA driver updated for Edgy (relative to Dapper)?

---

### Post by rocktorrentz on 2006-11-02
I have no idea...i'll check the repositories.

edit:
Edgy:   1.0.8774+2.6.17.5-11
Dapper: 1.0.8762+2.6.15.11-5

Looks like an upgrade to me.

---

### Post by edieguez on 2006-11-03
Have you tried downgrading back to the old driver?

---

### Post by ronmarley1 on 2006-11-03
> **dai said:**
> Hi - I'm starting to get an occassional problem on my Ubuntu Dapper laptop (Nvidia graphics, no desktop oddness other than murraine)

After leaving my machine on for a while, I occasionally come back to find that the colours in the display have degraded. The best way I can describe it is that it looks like when you run windows in 'safe mode' and only have 256 colors. This is most noticable where I have text boxes or documents open, the white paper becomes a dark grey and the text is impossible to read.

Logging off and then back on usually clears it, but ocassionally fails to and I have to restart the machine.

I've searched the forums and the web but this seems to be pretty rare, if not unique as I am unable to find any information on this problem anywhere.

I would be very grateful for any advice as to what is happening here and how I can prevent it.

Many thanks in advance!

I have no solution here, sorry.  Just wanted to add my similar experience.  I had/have this issue also.  However, I'm using a laptop with a an Intel graphics card.  I saw it every once in a while when using Dapper.  At first I attributed it to Beryl, as I never saw it until I installed the first release of Beryl.  Then, after formatting and installing Edgy (Wed. night), I've seen it once, and only at boot.  I also thought my screen  might be going bad, but I've never seen it in Windows.  All I need to do to fix it is drag my mouse on the screen and the color "pops" back to normal. This is a wierd one...

---

### Post by dai on 2006-11-05
> However, I'm using a laptop with a an Intel graphics card

I've an NVIDIA G6200 in my laptop. Problem has not occured for a while, and I think changing from the proprietry driver to the open source driver (nvidia to nv) has helped. This is a difficult issue to test, though. So I can't be sure.

---

### Post by Ossipon on 2006-12-13
I'm having the same problem. It only changes black colours and started happening after I installed Beryl. I've removed beryl now, but the problem continues. I can see it every time I start up, changing to another tty and back (crtl+alt+1 -> crtl+alt+7) as well as restarting X fixes it until the next reboot. But I'm afraid I don't have a solution yet.

---

### Post by rocktorrentz on 2006-12-14
The funny thing is that mine was fixed after installing beryl. I think it is a bug with some versions of the nvidia driver; I changed driver when I installed beryl to the ones from [here](http://albertomilone.com/driver_edgy.html)

---

