---
title: "Firestarter/IPTables questions"
date: 2007-12-30
forum: General Help
---

### Post by Ertai87 on 2007-12-30
OK, so I've got a couple concerns about Firestarter and IPTables, and I'd just like some quick answers if anyone happens to have them:

1) On a fresh install of Gutsy, is IPTables enabled?  I've heard both yes and no from different sources, so I want an absolute answer.  If so, what are its settings?

2) My computer has a LAN and Wireless connection (it's a laptop, go figure).  Firestarter confuses me a bit as to how to configure this.  I'm going to be in a situation in a week from now where I'm going to be using both LAN and WLAN a lot, so I want to configure Firestarter to track both LAN and WLAN traffic without having to manually switch between the two.  What are the settings I should use?

3) When I booted my computer up today, I noticed I got a "fail" in my boot data when the boot loader tried to load firestarter.  I ran Firestarter manually and it said it was on, but I'm just wondering if anyone knew what that was about.  It also said my eth1 (wireless) connection couldn't be detected (which was also fixed by the time the boot was finished).  Is it safe to assume that the two are related?

4) In Firestarter's events data (status tab, top frame), does it only count packets I should be concerned about or should it be counting all packets?  I ask because it's not counting anything and I'm wondering if this is a good sign (i.e. nothing's hacking me) or a bad sign (my firewall's not stopping things that might be hacking me).

Thanks!

---

### Post by scxtt on 2007-12-30
IPtables is routed through the kernel, so technically it's "enabled", but there are no rules defined after installation ... by default, a fresh install has NO services listening - so it's inconsequential to block anything @ that point ...

---

### Post by Ertai87 on 2007-12-30
Ah, so...correct me if I'm wrong, but basically you're saying that I have a firewall that's not actually listening to any data...huh...gotta fix that then...

---

### Post by scxtt on 2007-12-30
**iptables -L** will list your rules ... firestarter is just a GUI frontend that will allow you to create (basic) rules ...

i don't know that i'd say it isn't "listening to any data" - but network traffic that's routed through it may not be filtered in any way if you don't have any rules ...

---

### Post by Ertai87 on 2007-12-30
Ah.  Basically all I'm concerned with is that if anything were to happen, would it get detected?  I haven't set up anything important or irreplaceable on my laptop yet (I'm still a bit of a newbie to Ubuntu and am waiting till I got back to Uni next week where a lot of Linux users are who can help me get really set up), so it's not a big deal if I get hacked or anything, but I'd at least like to know so that I know if I should bother formatting or not.  Right now, Firestarter says my firewall status is "active", but I haven't set any rules on it yet, and my "total" and "serious" counts for both inbound and outbound traffic are set to 0 (and have never changed since I installed Firestarter, which is what question 4 is asking about).  My "internet connected network device" is my wireless card.  Is this a proper setup, or is there something wrong?

Oh, and do I have to sudo the iptables -L?  It says I do...

---

### Post by scxtt on 2007-12-31
yes, you'll need to use sudo ... i wouldn't worry about getting "hacked" ... when you're using wireless on someone else's network, just make sure you don't have any listening services (like SSH) running and you really don't have much to worry about (if anything) ...

chances are, if you have NO services listening - firestarter doesn't have much to report on ... to test it, you could have SSH listening, create a rule to block the traffic, then try to connect to it from somewhere else ...

---

### Post by Ertai87 on 2007-12-31
Well I do have this service called "ssh-agent" running.  It's using no memory ever (well, whenever I check anyway)...I think it's to enable me to open ssh connections easier by using the "ssh" command...would that be an apt analysis?  I can't ssh to localhost anyway.  I tried locking my firewall and then surfing, and those counts didn't increase despite the packets being blocked...what does this mean?

---

### Post by bodhi.zazen on 2007-12-31
What is it you are expecting a firewall to accomplish for you ?

In Linux things are "modular". You should not user firestarter to monitor your network as it needs to be running as root to do so and doing this is a bigger security risk then doing nothing.

Second, the firewall is iptables, firestarter is a gui configuration tool. However, installing firestarter changes settings of iptables.

Third, firewalls are not intrusion detection tools. Firewalls are a set of rules governing (internet) traffic on your computer. A default Ubuntu installation has not servers installed, so there is nothing to connect to. So a firewall is redundant.

If you install servers, you need to learn how to secure them, and a firewall is one of several things to consider.

I suggest you start with this link :  [[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

That link contains basic security information. Let us know if you have additional questions.

---

### Post by scxtt on 2007-12-31
> **Ertai87 said:**
> Well I do have this service called "ssh-agent" running.  It's using no memory ever (well, whenever I check anyway)...I think it's to enable me to open ssh connections easier by using the "ssh" command...would that be an apt analysis?  I can't ssh to localhost anyway.  I tried locking my firewall and then surfing, and those counts didn't increase despite the packets being blocked...what does this mean?you'd need to install **openssh-server** to have an ssh-server listening ...

sudo aptitude install openssh-server

and the firewall won't block *outbound* traffic (i.e. web browser usage) {unless you explicitly tell it to, i think}

---

### Post by Ertai87 on 2008-01-01
OK, so let me explain a bit:

I got a virus on my Windows install (same box, different OS) about a month and a half ago.  Since then, I've formatted my computer 3 times (twice with Windows, once with Ubuntu) and had various weird networking things happen.  For example, I had icons in Windows that were appearing, disappearing, changing, etc, and DLL files were getting wonky and stuff.  My dad had a problem the other day where his comp slowed down almost to a screeching halt which seemed to be solved after running a registry cleaner, although he only had about 15 problem items.  My Nintendo Wii which is also on my network is unable to copy particular game save data to an SD card and also while I was playing with it last night actually froze while loading a part of the game.  I have a zombie process running on my box which is a child of x-terminal-manager that never goes away (it starts on boot; it's a utility I use and the utility itself works fine, but part of the utility is this zombie process) that a friend of mine who uses the same application doesn't have, despite the fact that we have almost identical setups (both Ubuntu Gutsy, except her install is much older than mine, and we're using the same language support and everything).  Weird things like these keep happening to me on an ongoing basis, and have been for the past month and a half.  I'm not sure if these are all isolated incidents, but they make me nervous, especially since I had no problems until I got this virus on my Windows install.  As such, these are basically my concerns:

1) I'm fed up with formatting.  I don't want to have to format.  I installed Ubuntu because it's secure, has no viruses, malware, spyware, etc, and I wanted that level of security.

2) If I get a virus, malware, spyware, hack attack, etc, I want to know about it.  If I know about it and it's serious enough, I can format.  I don't want bad stuff on my system.  I know this is a bit unreasonable to ask because there are no known Linux viruses, so how can I know if I got one, but it still makes me nervous.

Keep in mind I've been using Windows since Windows 3.1, so I'm heavily set in the "Windows mindset".  A lot of what I'm saying probably sounds really stupid to a veteran Linux user, but that's where I'm coming from.

Anyway, so I set up the rkhunter thingy.  It found no rootkits or other infections, but it gave me a bunch of warnings.  I'm not sure if I set it up properly (I set it up using the default thingy).  One of the warnings said I needed to run --propupd to set the base case for rkhunter.  The problem is that (and again, Windows mindset) I'm not sure if I have the right files and stuff to start with.  I haven't added any sources except medibuntu and the Wine base, so I should be OK, but, again, Windows mindset.

Other than that warning, the others I got said something about "[filename] has been replaced with [same filename]: [some modifier]" where the modifiers are POSIX shellscript executable, Bourne-again shellscript executable, or perlscript executable.  Should I be worried?  What does this mean?

---

### Post by bodhi.zazen on 2008-01-02
Yes, we understand that sentiment. Start with the thread I gave you. Security is an active process, it is not a matter of installing an application and forgetting about it.

In general, there are a lot of false positives with anti-viral and root kit detection (MUCH better then false negatives). In general warnings are not a problem, but you should google them and read.  If you have a specific question about a specific warning, post it and we can give you better advice. consider a new thread in the Servers and Security sub-forums, it will get more attention then this thread.

---

