---
title: "no sound in flash"
date: 2008-04-23
forum: General Help
---

### Post by ELD on 2008-04-23
I have no sound in my flash, any idea how i can fix this, i have no real idea where ti look, got sound everywhere else :(

---

### Post by RyanBFS on 2008-04-23
are you using USB speakers or standard?  I had this problem with a logitech usb set once.

---

### Post by Seisen on 2008-04-23
Check this link out [https://edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/29760/comments/12](https://edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/29760/comments/12)

---

### Post by ELD on 2008-04-23
> **Seisen said:**
> Check this link out [https://edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/29760/comments/12](https://edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/29760/comments/12)

Tried it and no dice, myspace music crashed and no sound on anything else.

Standard jack input of speakers.

---

### Post by yaknowwat on 2008-04-24
Are you using PulseAudio (Its automatically included in 8.04)

There are some issues with PulseAudio and Flash will crash the application using it most of the time if sound and pulseaudio are involved.

I've been looking for a NSPluginWrapper for a 32-bit OS to cover flash and stop the crashing of the entire browser via flash.

---

### Post by ELD on 2008-04-24
> **yaknowwat said:**
> Are you using PulseAudio (Its automatically included in 8.04)

There are some issues with PulseAudio and Flash will crash the application using it most of the time if sound and pulseaudio are involved.

I've been looking for a NSPluginWrapper for a 32-bit OS to cover flash and stop the crashing of the entire browser via flash.

I'm just using your standard hardy install so whatever it uses for the sound on install i am using that.

Have tried under opera and firefox3 no dice in either :(

Someone please help!

---

### Post by MozBlue on 2008-04-24
BUMP

Got the same issue here, some one must know the solution.

FYI - I'm using and HP pavilion 8200 laptop using inbuilt sound and speakers.

Music player and desktop sounds are working just fine.

---

### Post by xaenyx on 2008-04-24
I had the exact same problem.  Fixed it by installing libflashsupport

```
sudo apt-get install libflashsupport
```

---

### Post by MozBlue on 2008-04-24
> **xaenyx said:**
> I had the exact same problem.  Fixed it by installing libflashsupport

```
sudo apt-get install libflashsupport
```

That worked a treat, cheers for that.

Though this now leads to another question why is Flash Player full screen so rubbish!!! Is it a Firefox thing or a Linux support issue?

---

### Post by bouchmil on 2008-04-25
> **xaenyx said:**
> I had the exact same problem.  Fixed it by installing libflashsupport

```
sudo apt-get install libflashsupport
```
It doesn't work for me. I'm using Firefox 3 beta 5 on my brand new 8.04 64bit.

---

### Post by ossi on 2008-04-25
Had the problem, that everywhere in Ubuntu sound could be played simultaneously, except when Firefox tried also to get the audio device. Libflashsupport solved the issue. Thanks:)

---

### Post by ELD on 2008-04-27
Yeah libflash worked for me, this is such a simple solution why can't the devs sort it.

---

### Post by stoffe on 2008-04-27
> **ELD said:**
> Yeah libflash worked for me, this is such a simple solution why the heck can't the devs sort it.

Yeah why indeed? What is your guess? Malice? Incompetence? A mix of both?

Or, you could just take a peek at the relevant bugs to get the answer. libflash currently causes lots of hard crashes for many users. So, the choice was "flash without sound" or "flash that brings everything down". Fixing "flash with sound that does not crash" is in progress.

If you are one of the few that don't get crashes with libflash, good for you. Maybe you can help "sort it".

---

### Post by ELD on 2008-04-27
> **stoffe said:**
> Yeah why indeed? What is your guess? Malice? Incompetence? A mix of both?

Or, you could just take a peek at the relevant bugs to get the answer. libflash currently causes lots of hard crashes for many users. So, the choice was "flash without sound" or "flash that brings everything down". Fixing "flash with sound that does not crash" is in progress.

If you are one of the few that don't get crashes with libflash, good for you. Maybe you can help "sort it".

There was no need for such a post semi-attacking me, i was simply asking about it. Maybe when we install flash they could kindly put a note up saying there is no sound due to bugs etc.

I actually experienced a lot of crashes in firefox flash related or not who knows i sure don't.

How about being nicer to people in future friend.

---

### Post by AR_Kozz on 2008-04-28
does libflashsupport apply to pre-hardy versions as well, I still use 7.04 which uses ALSA I think, but I have the same damn problem with sound in flash, it works everywhere but flash (and gnash sucks as an alternative)

I guess I will try it and see

Nope, it's not in the feisty repo's.

---

