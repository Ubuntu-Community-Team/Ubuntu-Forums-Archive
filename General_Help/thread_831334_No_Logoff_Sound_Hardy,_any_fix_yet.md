---
title: "No Logoff Sound Hardy, any fix yet?"
date: 2008-06-16
forum: General Help
---

### Post by stchman on 2008-06-16
Hello all,

I was wondering if anyone found a way to fix the no logoff sound.  I know it is extremely minor and if it is an easy fix I will do it.


Thanks.

---

### Post by rainwalker on 2008-06-17
I've had this issue too but never bothered to search for a solution :P
All I get is a system beep when I shut down...

---

### Post by pedro_orange on 2008-06-17
This is probably totally wrong. 

But I think I heard on the Ubuntu-UK podcast that Ubuntu shuts down too fast for it to play the shut down music.
They had an interview with the guy who wrote the music to the startup/shutdown sounds and they mentioned that as an off-comment.

---

### Post by isaacj87 on 2008-06-22
I'm surprised. There are plenty of bug reports for this problem. The logout event sound doesn't play on my laptop nor my desktop. If anyone has a fix, I'm all ears! :D

---

### Post by angry_johnnie on 2008-06-22
Only a [quick and dirty]("http://ubuntuforums.org/showthread.php?t=789858") fix.  But then... you did say **any** fix. :p  Haha don't worry, it's a nice, easy solution.

---

### Post by BigSilly on 2008-06-25
It does work as a quick fix, but to me it's not ideal really. I'm surprised there's no official fix for this yet as it's a well known issue and there's a few mentions of it on Launchpad.

I did use the above workaround, and it did work, but I found if I used it, it made the shutdown splash screen chuck up a load of text about network manager on closing. I don't know why it does that, but I felt I'd rather just stick with a quiet shutdown and a proper splash screen.

---

### Post by rainwalker on 2008-06-25
> **BigSilly said:**
> It does work as a quick fix, but to me it's not ideal really. I'm surprised there's no official fix for this yet as it's a well known issue and there's a few mentions of it on Launchpad.

I did use the above workaround, and it did work, but I found if I used it, it made the shutdown splash screen chuck up a load of text about network manager on closing. I don't know why it does that, but I felt I'd rather just stick with a quiet shutdown and a proper splash screen.

Mine does that already :(

---

### Post by BigSilly on 2008-06-25
> **rainwalker said:**
> Mine does that already :(

Mine used to too, so I don't really want to return to it! I tried a load of fixes from the forum, but what I think ended up sorting it for me was re-installing gdm and ubuntu-gdm-themes. I did this, messed about a bit with different themes, then it just...went away! Great solution eh? :lolflag:

I really like Ubuntu and Hardy, but I still feel as though a certain bit of polish is missing from the release. Not only that, but I've read that some of these issues go back to earlier Ubuntus, and they've obviously carried through to Hardy somehow, which is a bit disappointing.

I've thought about trying other distros instead of Ubuntu, but can't see anything I like as much. There's Fedora, but the package manager is not so hot, and trying to install "restricted" drivers for an nVidia card is a mind-boggling feat. I have Mandriva on my spare partition, and that's pretty good tbh, but you still get the dreaded RPMLock regularly. They've been having that for years, and it's still an issue. There's Suse, but well, we all know the issues there. 

I don't really want to create a dependency for myself on one distro (isn't that what got us into all this bother with Microsoft?), so I think I will install something else soon. But what - who knows?

---

### Post by rainwalker on 2008-06-25
Eh, I'm not going to mess with it.

Honestly, I personally feel that Hardy is one of the most unpolished releases so far, mainly because the devs focused on getting it out on time. Gutsy worked perfectly for me :?

I tried a live CD of openSUSE, and it was actually *really* fast! And it had a lot of options

---

### Post by DoDoENT on 2008-06-27
The problem is in pulseaudio sound server. This server is run as user, and not as root. It is started at the time of logging in (in the same time when applets are started). So the problem is on shutdown, log off or restart because pulseaudio server is stopped before log off sound is played.

Is there any way to manage priorities of stopping the user-started programs on logoff?

---

### Post by BigSilly on 2008-06-27
> **DoDoENT said:**
> The problem is in pulseaudio sound server. This server is run as user, and not as root. It is started at the time of logging in (in the same time when applets are started). So the problem is on shutdown, log off or restart because pulseaudio server is stopped before log off sound is played.

Is there any way to manage priorities of stopping the user-started programs on logoff?

Is this true? There must be a fix for it somewhere then.

---

### Post by DoDoENT on 2008-06-27
So far, I haven't got a clue about how to fix this. It is possible to use old ESD sound server instead of pulseaudio, but pulseaudio is much much better than ESD and has got a lot more features than ESD.

Try this tutorial: [http://www.pulseaudio.org/wiki/PerfectSetup#GNOME](http://www.pulseaudio.org/wiki/PerfectSetup#GNOME)

and tell if it worked for you. Unfortunately it didn't work for me, but I found a lot of good tips and tricks in it.

If we could prioritize the termination of user-runned programs, then we could set the pulseaudio to stop last. But I don't know how to do that :(

---

