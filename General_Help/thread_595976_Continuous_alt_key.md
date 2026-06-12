---
title: "Continuous alt key"
date: 2007-10-29
forum: General Help
---

### Post by Perrako on 2007-10-29
So, this is a completely fresh install of Gutsy, aannnndd... I've got a few other minor problems in another thread, but one really goofy one -- on occasion, my computer just decides to hold down the alt key. It's done it a few times while typing this post, and it does it while just browsing. It's fixed by pressing the alt key, but it is incredibly obnoxious. Also, I left it on overnight and when I woke up it was holding down the alt key. What is going on?

Hardware:
Logitech G15
MX Revolution
Nostromo n52

---

### Post by JBAlaska on 2007-10-29
Most likley it's your Keyboard going bad/shorting. Sometimes prying off the key cap and cleaning the stud helps, but unless it's lappy, just grab a new KB there cheep

---

### Post by megamania on 2007-12-07
> **JBAlaska said:**
> Most likley it's your Keyboard going bad/shorting. Sometimes prying off the key cap and cleaning the stud helps, but unless it's lappy, just grab a new KB there cheep
I'm having the same problem, and it's NOT the keyboard.

First I thought it was the batteries (it's a wireless keyboard), and replaced them. But the problem didn't stop.

After lots of tries, I completely **disconnected** keyboard and mouse from the computer, but the problem is still there: every 30 seconds the ALT key is pressed!
That's apparent under Konsole, Open Office and other applications where the ALT key selects the first item of the menubar (i.e. "File"): it is selected and deselected every 30 seconds or so without any keyboard or mouse connected!

Any ideas?

---

### Post by megamania on 2007-12-08
Anybody?

---

### Post by megamania on 2007-12-27
So... :-)

I had this problem coming and going for quite a long time. After checking and changing my keyboard, and even  unplugging it (even without a keyboard the ALT key was "pressed" anyway!), I decided to try a "scientific" approach.

I started timing the frequency of the ALT keypresses. _Exactly_ 30 seconds. Hmm. A broken keyboard or faulty motherboard wouldn't be that sharp.

I then started closing every application I had running when the problem started, one at a time.

I'm very surprised to say that the problem stops when I quit Totem (what? Totem? Why?), which was launched with this command to play a streaming radio:

```

totem http://live.mediaserver.kataweb.it/capital

```
As far as my problem is concerned, it is solved. Sometimes the ALT keypress problem doesn't show up for days, and when it does I just quit that instance of Totem and start it again.

Am I crazy, or is there an explanation to this?

---

### Post by flamer on 2007-12-27
> **megamania said:**
> So... :-)

I had this problem coming and going for quite a long time. After checking and changing my keyboard, and even  unplugging it (even without a keyboard the ALT key was "pressed" anyway!), I decided to try a "scientific" approach.

I started timing the frequency of the ALT keypresses. _Exactly_ 30 seconds. Hmm. A broken keyboard or faulty motherboard wouldn't be that sharp.

I then started closing every application I had running when the problem started, one at a time.

I'm very surprised to say that the problem stops when I quit Totem (what? Totem? Why?), which was launched with this command to play a streaming radio:

```

totem http://live.mediaserver.kataweb.it/capital

```
As far as my problem is concerned, it is solved. Sometimes the ALT keypress problem doesn't show up for days, and when it does I just quit that instance of Totem and start it again.

Am I crazy, or is there an explanation to this?

Thats strange. I have the same problem with the ALT key but not in Totem it's happenig in Xine 
:confused:

---

### Post by megamania on 2007-12-27
> **flamer said:**
> Thats strange. I have the same problem with the ALT key but not in Totem it's happenig in Xine 
:confused:
So this is crazy, but it's good to know that I'm not crazy (at least for the ALT key problem :-) )

I'm very curious to understand why this is happening!

---

### Post by tnauss on 2008-04-08
Hi,
I just want to confirm the totem problem and thank you for this tip.
Thomas

---

### Post by biodiesel-bri on 2008-04-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/216939](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/216939) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I can confirm this problem with Kubuntu Gutsy 64bit and Totem.  Closing totem stops the problem.

I'm filing the bug now.

---

