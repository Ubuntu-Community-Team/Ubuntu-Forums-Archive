---
title: "No input signal to monitor"
date: 2008-07-05
forum: General Help
---

### Post by JustGus on 2008-07-05
I turned on my machine and inexplicably I'm getting zilch on my screen: the monitor states "no input signal." Fiddled with all the cables, rebooted, fiddled some more rebooted some more and zip. A black screen. The fans whirr, lights go on, etc on the PC.  I'd been having some other [problems]("http://ubuntuforums.org/showthread.php?p=5298025#post5298025") meaning I had to turn off from the plug, so don't know if this has anything to do with it.
I also tried rebooting from the original CD, thinking that somehow the OS or BIOS may be telling it to stop the signal, but can't get it to boot off anything other than the HDD.
Can anyone help?! 
I'm running Hardy on a MiniITX machine.
Thanks in advance for any help!
Gus

---

### Post by overdrank on 2008-07-05
> **JustGus said:**
> I turned on my machine and inexplicably I'm getting zilch on my screen: the monitor states "no input signal." Fiddled with all the cables, rebooted, fiddled some more rebooted some more and zip. A black screen. The fans whirr, lights go on, etc on the PC.  I'd been having some other [problems]("http://ubuntuforums.org/showthread.php?p=5298025#post5298025") meaning I had to turn off from the plug, so don't know if this has anything to do with it.
I also tried rebooting from the original CD, thinking that somehow the OS or BIOS may be telling it to stop the signal, but can't get it to boot off anything other than the HDD.
Can anyone help?! 
I'm running Hardy on a MiniITX machine.
Thanks in advance for any help!
Gus
HI and are you able to see and video  while booting, like the bios boot? Have you tried to use the ctrl, alt, F1 keys and attempt to reach the command prompt?

---

### Post by JustGus on 2008-07-05
Thanks for the response - No, I get no video, even when the initial BIOS screen loads.  After waiting for boot up (or what should have been adequate time for it to have occurred) I hit Ctrl, Alt, F1, then entered *sudo halt -i -p* blind, hoping this will at least shut down.  But the machine stays booted up.
Have also tried jiggling the video cables around at each end, in the hope that it's just a loose cable but no luck there, either.  Arhggggg!
Any other suggestions would be very, very welcome!

---

### Post by overdrank on 2008-07-05
> **JustGus said:**
> Thanks for the response - No, I get no video, even when the initial BIOS screen loads.  After waiting for boot up (or what should have been adequate time for it to have occurred) I hit Ctrl, Alt, F1, then entered *sudo halt -i -p* blind, hoping this will at least shut down.  But the machine stays booted up.
Have also tried jiggling the video cables around at each end, in the hope that it's just a loose cable but no luck there, either.  Arhggggg!
Any other suggestions would be very, very welcome!

Well if the system has onboard graphics that would be my guess is they have failed. You may open the system and reseat the memory and if it has a graphics card the it also. :(

---

### Post by JustGus on 2008-07-06
Thanks for the suggestions.  I've cracked open the case and tried reseating the memory.  I can't tell if there's onboard video (this is the machine [here]("http://cgi.ebay.com.au/ws/eBayISAPI....m=370059585860"), in case its possible to determine from the description).  Had a fiddle with all the internal cables and hooked up the monitor to another PC, just in case and it works fine with the other machine.  But after putting it all together again, the problem is still there.
If the onboard graphics have failed, what are my options?  I noticed there's a remaining PCI slot. Is it something where I can simply find a cheap one and add that?  The only purpose of this machien is to stream audio, so flashy graphics aren't needed...just the ability to get the machine up and running. 
Gus

---

### Post by lynwode on 2008-07-06
I have exactly the same problem. The machine was off for a few weeks and I have just got to boot it up and I have no screen. The machine is up and running as I can telnet into it. Anyone got any ideas?

---

### Post by overdrank on 2008-07-06
> **JustGus said:**
> Thanks for the suggestions.  I've cracked open the case and tried reseating the memory.  I can't tell if there's onboard video (this is the machine [here]("http://cgi.ebay.com.au/ws/eBayISAPI....m=370059585860"), in case its possible to determine from the description).  Had a fiddle with all the internal cables and hooked up the monitor to another PC, just in case and it works fine with the other machine.  But after putting it all together again, the problem is still there.
If the onboard graphics have failed, what are my options?  I noticed there's a remaining PCI slot. Is it something where I can simply find a cheap one and add that?  The only purpose of this machien is to stream audio, so flashy graphics aren't needed...just the ability to get the machine up and running. 
Gus

Hi and the link to the system did not work, but I have attached a example of a motherboard that has onbaord graphics. the location of the connection is a good indication of on board graphics. As for additional PCI slots then yes you may be able to add a card and reuse the machine. This is where the testing comes in and it maybe the cpu died or some bad memory. Do you here any system beeps? You may remove the memory and see if you receive system beeps.

---

### Post by cariboo on 2008-07-06
Sounds like a bad video adapter. If you've got a PCI video card lying around you could that a try.

Jim

---

### Post by JustGus on 2008-07-06
Will have a look tonight.  Might be able to get my hands on a used video card as well.  Thanks guys!

---

