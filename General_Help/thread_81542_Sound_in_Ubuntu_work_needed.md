---
title: "Sound in Ubuntu work needed?"
date: 2005-10-24
forum: General Help
---

### Post by speedsix on 2005-10-24
Hi, one thing that really trips me up as a new user of Ubuntu is the sound. As a relatively new linux user I find it a massive downer to the whole ubuntu experience. 

I've just moved from Hoary to Breezy and again I have problems because I can't remember what I did in Hoary to get it to work, there are so many different HOWTOs relating to sound problems all seeming going in a different direction.

It's the whole ALSA/OSS/ESD 'thing', Where possible I have my apps set to alsa which works fine (using a custom alsa config file) but I need OSS apps like Frozen Bobble & Realplayer to route to ALSA. ESD is turned off as I don't see the point in yet another sound server, why can't everything use one, i.e alsa (seeing as mixing now works)

My questions..

1. How do I route OSS apps sound to use ALSA?

2. Can someone please explain gstreamer to me?


many thanks from an otherwise very happy Ubuntu user.

Cheers

Dom

---

### Post by speedsix on 2005-10-26
Anyone?

Thanks.

---

### Post by darrenrxm on 2005-10-26
Wow! That is surprising that sound is not working for you. Every computer that I try ubuntu on sounds works with no config. When I was using knoppix, some users suggested that I switch to a soundcard that was supported out of the box by linux. You can buy a linux supported soundcard very cheaply. I did not actually take the advice I was given. I just waited until my soundcard was supported by knoppix.

Anyway, what kind of soundcard do you have?

---

### Post by doclivingston on 2005-10-26
[QUOTE=speedsix]1. How do I route OSS apps sound to use ALSA?[/quote]

Frozenbubble and other SDL application can use ALSA directly, if you install the package "libsdl1.2debian-alsa" (which will replace "libsdl1.2debian-oss").

For other OSS applications you can install the package "alsa-oss" and use the oss->alsa mapping script in that; however I don't remember exactly hwo to do it off the top of my head (sorry).

---

### Post by speedsix on 2005-10-26
[QUOTE=doclivingston]Frozenbubble and other SDL application can use ALSA directly, if you install the package "libsdl1.2debian-alsa" (which will replace "libsdl1.2debian-oss").

For other OSS applications you can install the package "alsa-oss" and use the oss->alsa mapping script in that; however I don't remember exactly hwo to do it off the top of my head (sorry).[/QUOTE]

Thanks, I have been looking at alsa-oss but cannot suss out how to perform the mapping either :( 

I'm just confused why I cannot easily find this information considering how important it is, most of the HOWTOs involve using ESD in combination with alsa/oss which seems pointless to me.

Thanks

Dom

---

### Post by speedsix on 2005-10-26
Hi,

I installed the sdl libraries and Frozen Bobble now works!

As far as I can make out, there are 2 ways of mapping OSS sound to ALSA.

1. Kernel modules, I have tried this technique and it doesn't work in Breezy, I'm sure this was how I got it working in Hoary.

2. The better method is supposed to be modifying your asound.conf, I have done this and it doesn't work. I tell xmms to use OSS /dev/dsp and it plays but I get silence, if I set it to /dev/dsp0 it throws an error suggesting I check my settings as the card may be blocked. If I type aoss xmms at a shell it works!?

So I suppose it's like this..

ALSA = fine (sdl uses alsa now so frozen bubble works, also set GAIM to aplay %s and that works also)
OSS = not working, set apps to OSS and nothing
ESD = enabled this now and all sounds in Gnome work

I have also set Firefox & Realplayer to use AOSS, firefox has no sound whereas Relaplayer is crackly. I have noticed there are 2 instances of esd started?

```



pcm.!default 
{

type plug

slave.pcm "dmix-digital"

}



# Control device (mixer, etc.) for the nForce2 card

ctl.analog 
{

 type hw

 card 0

}







# The following devices are not useful by themselves.









# Alias for digital (S/PDIF) output on the nForce2/4 (hw:0,2)

# Do not use this directly--it requires specific rate,

# channels, and format

pcm.digital-hw 
{

 type hw

 card 0

 device 2

}




# Control device (mixer, etc.) for the nForce2/4 card

ctl.digital-hw 
{

 type hw

 card 0

}









# Direct software mixing plugin for digital (S/PDIF) output

# on the nForce2/4 (hw:0,2)

# Do not use this directly--it requires specific rate,

# channels, and format

pcm.dmix-digital 
{

 type dmix

 ipc_key 1235

 slave {

   pcm "digital-hw"

   period_time 0

   period_size 1024

   buffer_size 4096

   #rate 48000

 }

}




# Control device (mixer, etc.) for the nForce2/4 card

ctl.dmix-digital 
{

 type hw

 card 0

}










########
# AOSS #
########


# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp 
{
     type plug
     slave.pcm "dmix-digital"
}


# OSS control for dsp0 (needed?...this might not be useful)
ctl.dsp 
{
     type plug
     slave.pcm "dmix-digital"
}


# OSS control for dsp0 (default old OSS is mixer0)
ctl.mixer 
{
     type plug
     slave.pcm "dmix-digital"
}

```

---

### Post by speedsix on 2005-10-26
I think I'm closer to an anser whjy I can't get any OSS/aoss sounds.

cat test.wav > dev/dsp does nothing, well it seems to play but silence, just like XMMX set to OSS, it plays but is silent.

I have everything set to output to HW0,2 digital spdif btw in asound.conf.


Thanks dom

---

### Post by Riverside on 2005-10-26
My experience:

**Warty** - sound "just worked"

**Hoary** - sound didn't work, and I couldn't get a peep out of the speakers.  I couldn't remedy this, as Ubuntu developers for reasons best known to themselves ship Ubuntu with a cut down (crippled) version of ALSA in which one essential utility, alsaconf, is not included.  Running alsaconf as root, regardless of Linux distribution, gets sound working in 5-30 seconds on both of my desktop machines (both of which have onboard sound chips) without exception.  I Googled and searched these forums without success for several days in an effort to find out how to enable ALSA in Hoary.  Eventually, I tried uninstalling the packaged ALSA and compiling the ALSA source code from the ALSA web site in order to build a version with alsaconf, but it wouldn't compile.  I finally gave up on Hoary as a result after about five days.

**Breezy** - sound "just worked".

---

