---
title: "Web Filtering"
date: 2006-11-26
forum: General Help
---

### Post by saxaphone_man on 2006-11-26
My dad has recently been bugging me about installing parental control software on ubuntu, but I haven't found how I can do this. I need to be able to setup a parental control program that will allow my dad to make a password in order to edit it, but still allow me to use sudo to install packages, and edit my system files (ex /etc/modules).

I've been looking at using DansGuardian ([www.dansguardian.org](www.dansguardian.org)) and tinyproxy, or squid, and it seems that this is the best way at going about it, yet the config. files can easily be edited with my password with sudo.

I was also looking at CensorNet ([www.censornet.com](www.censornet.com)) but I can't get that to work, it freezes after I boot up into it.

So, finally, I come here to ask if anyone has any work arounds, or any ideas, because if I don't install it today by 3 PM EST, I have to install winbloze back, since that has Norton Parental Controls (AH!).

One thing I was thinking of, is if my dad could set the root password on my system, and if there was a way to edit the dansguardian files only with that password, or have another password or account that only it could edit the dansguardian files. Is this possible?

---

### Post by pianoboy3333 on 2006-11-26
I've been wondering how to do the same.

---

### Post by saxaphone_man on 2006-11-26
Can anyone help me? I've only got another few hours...

---

### Post by saxaphone_man on 2006-11-26
Can SmoothWall do what I want? Or does that have to use Dansguardian in combination with that?

---

### Post by mayonaise15 on 2006-11-26
I think Smoothwall would be a great solution.  The only requirement is that it requires a dedicated PC with at least 2 NIC's.  The great thing about Smoothwall is that it can run on some seriously ancient hardware.  You would still have to install DansGuardian on the SmoothWall box, but once it is installed it can all be administered through a web page.  There are instruction for installing DansGuardian on Smoothwall here: [http://community.smoothwall.org/forum/viewtopic.php?t=8488](http://community.smoothwall.org/forum/viewtopic.php?t=8488)

Smoothwall is also a sweet firewall, by the way.

---

### Post by saxaphone_man on 2006-11-26
> **mayonaise15 said:**
> I think Smoothwall would be a great solution.  The only requirement is that it requires a dedicated PC with at least 2 NIC's.  The great thing about Smoothwall is that it can run on some seriously ancient hardware.  You would still have to install DansGuardian on the SmoothWall box, but once it is installed it can all be administered through a web page.  There are instruction for installing DansGuardian on Smoothwall here: [http://community.smoothwall.org/forum/viewtopic.php?t=8488](http://community.smoothwall.org/forum/viewtopic.php?t=8488)

Smoothwall is also a sweet firewall, by the way.

I understand, but is there a way so that my dad can create a password, and only he can edit the files, but I can still do all of my system tasks (ie: installing packages, editing root files) with sudo + my password.

---

### Post by Refrozen on 2006-11-26
> **saxaphone_man said:**
> I understand, but is there a way so that my dad can create a password, and only he can edit the files, but I can still do all of my system tasks (ie: installing packages, editing root files) with sudo + my password.

That's really never going to be possible with a software solution. If you wanted to get around it you could always just unistall the program, or kill it's process.

Just tell your dad it's possible, haha.

---

### Post by ehird on 2006-11-26
Perhaps slightly offtopic, but you're >allowing< yourself to be WILLINGLY censored on the internet? No wonder to me now what's happening to the world...

---

### Post by mayonaise15 on 2006-11-26
> **saxaphone_man said:**
> I understand, but is there a way so that my dad can create a password, and only he can edit the files, but I can still do all of my system tasks (ie: installing packages, editing root files) with sudo + my password.
Yes, Ubuntu will be running on your computer and Smoothwall will be running on a separate computer all together.  Different computers = different root passwords.

The way that it works is the Smoothwall box is the gateway to your network.  All internet traffic goes through the Smoothwall before it gets to your computer, so it can block web pages before they get to your computer.

Hope that helps :)

---

### Post by saxaphone_man on 2006-11-26
Well, my dad runs a windows box, could he filter my ubuntu box through his computer? fyi, we're all connected on the same wifi

---

### Post by mayonaise15 on 2006-11-26
Hmm...I don't think he could filter your traffic through a wifi connection, unless he had 2 wifi cards in his computer.  Then you would have to find some sort of Windows filtering/gateway software.  

I take it that you don't have any extra computers that could be a box dedicated to running Smoothwall?

---

### Post by saxaphone_man on 2006-11-26
we could... not a horrible idea... I have an extra crap computer hanging around...

---

### Post by saxaphone_man on 2006-11-26
so what would I do with it? couldn't I just simply turn it off? rofl

---

### Post by Refrozen on 2006-11-26
No, because you'd be connected directly through it.

You could, however, just plug your network cable directly in to the network, avoiding the filter all together.

I can't believe you're helping your dad censor your internet use. This is ridiculous. Your dad is ridiculous.

---

### Post by saxaphone_man on 2006-11-26
all the roads seem to lead to hell :(

---

### Post by saxaphone_man on 2006-11-26
CensorNet seems good, but it doesn't work... I don't know why

I boot into it, and then my computer essentially freezes, caps lock doesn't turn my light on, spacebar doesn't make it continue... I've tried burning and downloading several copies... like... 10.

---

### Post by saxaphone_man on 2006-11-26
> **Refrozen said:**
> No, because you'd be connected directly through it.

You could, however, just plug your network cable directly in to the network, avoiding the filter all together.

I can't believe you're helping your dad censor your internet use. This is ridiculous. Your dad is ridiculous.

I'm not exactly helping him... it's either I get this to work... or it gets uninstalled...

---

### Post by saxaphone_man on 2006-11-26
Is it possible to set dansguardian up, and have a way to setup a password that only my dad can use, so that when you edit files, you'd have to use that password, and using sudo wouldn't do anything...? Is it possible to not be able to edit the files without the root password...?

---

### Post by mayonaise15 on 2006-11-26
I'm looking around at some docs right now that talk about sudo configuration.  It may be possible to actually limit what you can do with sudo, but I'm not sure how detailed those settings can get.

---

### Post by urukrama on 2006-11-26
There was a discussion about this earlier. See [http://ubuntuforums.org/showthread.php?t=177591&page=2&highlight=internet+filter](http://ubuntuforums.org/showthread.php?t=177591&page=2&highlight=internet+filter)

---

### Post by ehird on 2006-11-26
> **saxaphone_man said:**
> I'm not exactly helping him... it's either I get this to work... or it gets uninstalled...

Your dad, to quote a previous poster, is ridiculous.

Over-protected much? :-|

---

### Post by saxaphone_man on 2006-11-27
Damn, it seems like I'll need another box for CensorNet too from that post... **** what do I do...?

---

### Post by saxaphone_man on 2006-11-27
Is there something my dad can run on _his_ computer  (winbloze box) to web filter my computer since I get my internet from the same router...?

:(

---

### Post by urukrama on 2006-11-28
If you connect to the internet through his computer, that should be possible. I'm not sure how this would work with wireless, however (never used it myself -- the joys of old hardware ;) ). If his internet is filtered, yours should be too.

You'll find several posts about sharing internet connections on these forums. Do a forum search for 'sharing internet'. Good luck.

---

### Post by saxaphone_man on 2006-11-28
> **urukrama said:**
> If you connect to the internet through his computer, that should be possible. I'm not sure how this would work with wireless, however (never used it myself -- the joys of old hardware ;) ). If his internet is filtered, yours should be too.

You'll find several posts about sharing internet connections on these forums. Do a forum search for 'sharing internet'. Good luck.

Through his computer... that's an interesting idea... We're across the hallway, but I could run a wire up into my attic. So if I plug directly into his computer... then he should be able to filter me with something like Norton Parental Controls?

---

### Post by saxaphone_man on 2006-12-25
Can anyone help me? If I don't get this figured out I'm gonna have to go back to XP and lose ubuntu!

---

