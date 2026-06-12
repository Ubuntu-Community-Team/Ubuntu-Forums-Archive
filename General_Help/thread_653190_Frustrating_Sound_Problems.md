---
title: "Frustrating Sound Problems"
date: 2007-12-29
forum: General Help
---

### Post by jlacroix on 2007-12-29
I hope someone can help me. I bought an Audigy SE card for my PC, but it apears that I can only have one sound application open at one time.

For example, if I watch a video on youtube, then I stop the video, and try to play music on Rhythmbox or Amarok, no other application can gain access to the sound server. I have to close Firefox for a while and then reopen my music player so it can play music. 

So basically I can only have one application open that plays sound at any one time, even if the other applications aren't utilizing sound at that moment.

Previously, I was using an Audigy 1 card and after that I was using my onboard Realtek card, neither one had that problem. The onboard Realtek card sucks, but at least it didn't have trouble giving up control to other applications.

In fact, I didn't even have sound on my rear speakers until I used a custom asoundrc file.

I'm extremely frustrated right now. I don't understand why an Audigy 1 card (which I don't have anymore) would work perfectly and an Audigy SE card won't work right at all.

Is this just a sound card driver issue? Or do I need to take the card back and suffer with a crashing Firefox? (With my onboard sound card, Firefox crashes constantly).

---

### Post by jlacroix on 2007-12-29
Well, I'm making progress! Here's my (new) problem.

If I use this .asoundrc file, I can have multiple applications using the sound server at any one time, but I only get sound out of 2 of my five speakers:
```
pcm.ca0106 {
          type hw
         card 0
       }
       
      ctl.ca0106 {
          type hw
          card 0
       }
```

If I use this .asoundrc file, I have sound out of all of my speakers, but only one application that uses sound can be open at a time:
```
pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}
```

I don't understand any of the code in either file but hopefully one of you can help me combine the two together so I can have all my speakers work and listen to more than one application at a time.

---

### Post by jlacroix on 2007-12-29
Anyone? Is there a fix for this or do I just need to take it back to the store and suffer without sound?

---

### Post by jkzubu on 2007-12-29
---edit---

---

### Post by jlacroix on 2007-12-29
I really appreciate you trying to help, but you aren't understanding my problem. I'm not sure how much better I can explain it, but I'll try.

My Audigy SE works, it is the default already, and no other sound cards are turned on or could have interfered. The driver you told me to set it to was the driver it was automagically set to.

The problem is I have a 5.1 surround system. Only the front two speakers have sound. If more than one program that uses audio is open, no other application can have access to the sound server.

If I use this .asoundrc file, more than one application can use the sound card at the same time but only the front two speakers work:

```

pcm.ca0106 {
          type hw
         card 0
       }
       
      ctl.ca0106 {
          type hw
          card 0
       }
```

If I use this asoundrc file, all speakers work, but only one application can use the sound server at a time:

```

pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}
```

Anyway, I'm probably just going to forget about it. I've been searching Google for two days and no one can tell me how to get all speakers working and be able to have more than one application use the sound server at the same time, which is something every sound card I've ever used for the last five years was able to do.

No offense to anyone, but this is an inexcusable bug, which I guess was reported already:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/46233](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/46233)
And ignored by the Ubuntu developers since 2006. Nice. The fact that the most common retail sound card is not supported correctly in Ubuntu and the matching bug report has been ignored for almost two years is just plain pathetic. I've had it! At this point I'm considering another distribution or even Windows.

Again, no offense to anyone, I'm extremely frustrated at trying to fix this problem for two days now with no results at all!

---

### Post by ghsfr33d0m on 2007-12-29
i understand what your saying, and i just fixed my sound drivers, but your issue just looks ****** up. thats a really wierd glitch. id consider getting another card, mabey it does not like your mobo? im sure uve tryed to reinstall your drivers, but thats always a good place to start.

anyway dude, sry cant be more help, that just looks ****** up..

---

### Post by jlacroix on 2007-12-29
I thought about getting a different sound card, but the only options in any store within a 100 mile radius at least is either the Audigy SE card that I have now, or an X-FI card which I understand doesn't work in Linux at all.

So really, there is no viable option to have sound in Ubuntu. This is sad. I had alot of respect for Ubuntu, it was my favorite distribution, however this issue has just killed Ubuntu for me, and lack of fixes from the developers has buried it.

---

### Post by jlacroix on 2007-12-30
Sorry about my rant earlier guys. I was just really frustrated.

This problem is solved. I took the Audigy SE back to the store and got myself a 7.1/24-bit Diamond Multimedia card. (I was shocked to actually find one for sale). Everything worked without me having to configure anything.

Word to the wise: If you use Linux, DON'T buy from Creative. Their current line of products don't work with Linux at all, and their entry-level card has problems with Linux. Creative probably won't ever fix the problems either.

---

