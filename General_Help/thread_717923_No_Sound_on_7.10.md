---
title: "No Sound on 7.10?"
date: 2008-03-07
forum: General Help
---

### Post by heyniceaddress on 2008-03-07
I recently have begun using Ubuntu after discovering how much I dislike Windows Vista. I have installed it on my new laptop and my three-year-old desktop; however, both of them have the same problem:

My volume icon has the red-slash "no" symbol through it. When I double-click I receive this message: "No volume control GStreamer plugins and/or devices found."

I have searched for, read, and tried many of the solutions that others have had with this problem that I have found on Google/Ubuntu forums, but none of it has helped.

I have downloaded all the updates for 7.10 and have Automatix, which provided all the codecs that may have been needed, and neither of these remedied the problem.

Help, please?

(I don't know where to find the system information for all of you if it is something you need to know in order to help me.)

---

### Post by Metaljaz on 2008-03-07
The commands in this thread are being typed from the terminal window. 
Under applications>accessories>terminal

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by chunchengch on 2008-03-07
try this,

1. open file /etc/modprobe.d/alsa-base

$ sudo gedit /etc/modprobe.d/alsa-base

2. add this line to the bottom of file

options snd-hda-intel model=auto

3. reboot

---

### Post by heyniceaddress on 2008-03-07
After typing in /etc/modprobe.d/alsa-base it tells me permission denied...?

---

### Post by heyniceaddress on 2008-03-07
Nevermind, I made a typo when I did it...let me try it now.

---

### Post by chunchengch on 2008-03-07
**[COLOR="Red"]sudo[/COLOR]** gedit /etc/modprobe.d/alsa-base

---

### Post by heyniceaddress on 2008-03-07
I tried it out, but it did not work: there's still a red slash through my volume control and it says the same thing as before. Thank you, though. I just looked at the other guy's post and it seems there's no driver available for Sound Blaster X-Fi

---

### Post by Sef on 2008-03-07
I had the similar problem.  Turned out the kernel was missing a piece.  Check out [my thread]("http://ubuntuforums.org/showthread.php?t=615513&highlight=sound") as to how it got solved it.

---

### Post by heyniceaddress on 2008-03-07
Thanks, I had manually gotten the kernel 2.6.22-14-386, too, but I had not installed it yet, as I did not know how. I tried the solution provided to you that showed how to install it and rebooted, but it still does not work and says the same thing.

Do you, or does anyone, know how to get -generic sound available like that guy was talking about in your link...? Maybe that will work...?

---

### Post by boeing777 on 2008-03-07
install GStreamer  from the Synpatics

---

### Post by boeing777 on 2008-03-07
System -->Administration -->Synpatics Package Manager

and install GStreamer

---

### Post by heyniceaddress on 2008-03-07
I installed and reinstalled all the GStreamer boxes that were available and rebooted: still the same.

:(

---

### Post by heyniceaddress on 2008-03-07
Does anybody think that this will help, since I have a Sound Blaster X-Fi  sound card?

[http://www.opensound.com/index.html](http://www.opensound.com/index.html)

If so, does anybody know whether it can be installed in Ubuntu 7.10; if so, which download do I choose; also, how do I go about installing it?

Thank you for your time!

---

