---
title: "Can't change default sound card"
date: 2007-02-21
forum: General Help
---

### Post by Shampyon on 2007-02-21
Up until about a half-hour ago my sound was working just fine. I turned the computer off for a few minutes, then rebooted. When it restarted, my sound had gone.

I've tried a dozen other fixes, but gotten no results. I think the root of the problem is related to one odd occurence:

when I go to System>Preferences>Sound>Sounds, the default card is listed as CA0106. I need the default card to be HDA Intel for sound to work, so I click that dropdown box, choose HDA Intel and close the preferences window. That should fix it, right? Well, it would if it accepted my choice.

When i go back to System>Preferences>Sound>Sounds, the default card is once again CA0106. No matter how many times I reselect HDA Intel, it keeps reverting to CA0106. It's driving me batty! How can I get this stupid thing to just accept the fact that I want HDA Intel as my default card?!

---

### Post by Shampyon on 2007-02-21
Okay, this is odd. I did:

```
sudo asoundconf list
```

I got back:

```
Names of available sound cards:
CA0106
Intel

```
I then did:

```
sudo asoundconf set-default-card Intel
```

followed by a reboot to test.

Sure enough, the Intel is now set to default. But I still don't have sound?! All the sound settings are exactl;y as they were before I lost audio. What the heck is happening here?!

---

### Post by Shampyon on 2007-02-25
So I've retried all of the methods. Still nothing. Edgy refuses to recognise my card any more.
I've been two weeks without any sound on my machine. Any tips?:-({|=

---

### Post by livingtarget on 2007-02-27
Here's something to try, in preferences > sound try switching the sound to the wrong device and see if you get sound now :).

Something weird happened with my sound, the NVidia HDA Intel wasn't the first option anymore but suddenly the second option in the drop down list. I then set the default card to NVidia and all of a sudden my sound option was set to the wrong device and now it works. 

Weird...

Anyhow if that doesn't work, try taking the PCI sound card out. (assuming your intel is the onboard sound card). It sure can get confused with two sound cards in.

---

### Post by Shampyon on 2007-02-28
When I go to Preferences> Sound, there are no sound cards listed.
I would have assumed that the hda-intel one was my on-board sound too, but when i first bought the mobo they claimed this one didn't have on-board sound. Wierd, I know, but it's a strange board. HAs one of those extra power connectors you normally see on a server board and... but I digress.

I'll try removing that sound card anyway just to see what happens.

---

### Post by Shampyon on 2007-03-01
Okeydoke, rather than remove my pci card I've disable on-board sound in the BIOS. I then recomplied ALSA from the source and followed the Sound Guide instructions to the letter.

Successful? Nope. However, I'm one step closer. I got sound when the Login Manager started!

Unfortunately my elation was short-lived, as I'm still having the same problems once I log in. Alsamixer won't start because 
> alsamixer:function snd_ctl_open failed for default: No such device
When I double-click on the Volume Control applet, I get this error:
> No volume control GStremer plugins and/or devices found.
My sound card still doesn't show up under Default Sound Card (nor doesn any other card) when I go to System > Preferences > Sound > Sounds.

I'm closer! Any advice on where to go from here?

---

