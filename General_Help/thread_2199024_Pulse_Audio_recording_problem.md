---
title: "Pulse Audio recording problem"
date: 2014-01-11
forum: General Help
---

### Post by rmcellig on 2014-01-11
I am trying to record shows off the radio using this code. I have been using this code for two years now with no issues. The recording part is not working at all and I think it is an issue with my Pulse Audio.

What do I need to do to get this working? I am using Xubuntu 13.10 with the default Pulse Audio that came with it.

My radio is directly connected to my PC through the line in port. It works fine except for the recording part.

I tried all the options under the show menu in the Recording tab of the Volume Control window. I have a feeling I have to install something to get this working?

---

### Post by Merrattic on 2014-01-11
Being able to see the script may help but don't think that is necessarily the problem.

Can you hear the radio through the speakers?

What is the input device if you can? (as shown in PA Volume Control)

Save fiddling about the pulse, you could always try using outRec which has always got round recording sound on my Xubuntu setups. Link: [http://outrec.sourceforge.net/](http://outrec.sourceforge.net/)
(you may need to install gambas2, not sure if only gambas3 on 13.10)

---

### Post by rmcellig on 2014-01-11
I think I know what the problem is. I just don't know how to implement it.

When I restarted my computer and booted into Crunchbang 11 Linux, Notice the Alsa plugin? I don't have that when I'm in Xubuntu.

I'm using the command line to arecord to record my shows. Works great.

---

### Post by Merrattic on 2014-01-12
Am using #! as my main OS at the moment too :)

In Xubuntu, try running alsamixer to see if you need to turn on capture

---

### Post by rmcellig on 2014-01-12
Thanks I will check out my Alsamixer settings again. I'm sure I have capture activated. Right now I am in Crunchbang because I have to record my shows today but later on I'll switch back to Xubuntu and take a look. One thing I love about Linux is that if worse comes to worse and let's say Crunchbang fails as well. I can always boot up from my trusty Puppy Linux CD and record my shows that way.

The choices you have in Linux has been a real eye opener to me. I'll post back later with my Xubuntu alsamixer results. Let's say that doesn't work, what are my other options? Do a complete removal of Pulseaudio through Synaptic Package Manager and then reinstall Pulseaudio?

---

