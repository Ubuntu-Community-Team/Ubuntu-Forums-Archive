---
title: "hardy not playing sound in certain programs"
date: 2008-05-01
forum: General Help
---

### Post by rory096 on 2008-05-01
Sound does work at least in Firefox and mplayer, but it doesn't in VLC, Totem and apparently the system itself (when going to system-administration-sound, none of the example sounds actually play). This happens with both headphones and speakers.

---

### Post by Bubba64 on 2008-05-01
Have you installed the extra gstreamer and Ubuntu restricted extras in add remove. gstreamer if your using that set. Also have you opened up the repositories in software sources and added medibuntu.

---

### Post by rory096 on 2008-05-01
> **Bubba64 said:**
> Have you installed the extra gstreamer and Ubuntu restricted extras in add remove. gstreamer if your using that set. Also have you opened up the repositories in software sources and added medibuntu.

I just tried both of those, neither worked.

---

### Post by Bubba64 on 2008-05-01
> **rory096 said:**
> I just tried both of those, neither worked.

I am not sure if any of my suggestions are the fix for your problem, but which both of those. There are multiple gstreamer programs in add remove if you click on all available. If you give a good description of what you have installed the people who can help you will probably reply, the problems your having are all over this forum so specificity will be a great help to you.

---

### Post by rory096 on 2008-05-01
> **Bubba64 said:**
> I am not sure if any of my suggestions are the fix for your problem, but which both of those. There are multiple gstreamer programs in add remove if you click on all available. If you give a good description of what you have installed the people who can help you will probably reply, the problems your having are all over this forum so specificity will be a great help to you.
I installed basically all of the gstreamer programs in add/remove (many were already installed), including the restricted extras. I followed the instructions on the medibuntu site to install that (sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list 
then 
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update). I didn't have this problem running Gutsy, and Amarok also won't play sound.

---

### Post by rory096 on 2008-05-06
The problem is still going on, and it's getting rather annoying.

---

### Post by rory096 on 2008-05-14
Hmm, when opening Foldit in WINE it gives an error message saying "Can't open audio device." That probably has something to do with this.

---

### Post by smorar on 2008-07-15
I have a similar and possibly related problem as the original poster.

My sound works after a fresh reboot, however, after a number of suspend and resume cycles, none of my gstreamer applications play any audio. This is fixed by a reboot!

---

### Post by vikrant82 on 2008-07-15
Are you using pulseaudio. 

There is a bug here with me on intrepid where default device that is chosen is a virtual device. So many a times I have to manually make the real audio device as my default device. On reboots, the other device again becomes the default device.

---

### Post by smorar on 2008-07-15
Yes, I am using pulseaudio, however, I am still on hardy at the moment.

How do you manually change the default device that is being used? Bear in mind, non gstreamer based apps still seem to work.

Oh, and updating my previous message - logging out and back into my gnome session also seems to solve the problem.

---

### Post by vikrant82 on 2008-07-15
If you have installed, pulseaudio volume manager, you'd see some devices in Devices tab, A wrong device gets marked as default for me. So i have to manually select the second device and mark it as default.

I might drop you a screenshot once i reach home in another, 2-3 hours.

---

### Post by paulnn on 2008-07-15
I'm not sure of the details, i think the way to do what vikrant is suggesting is to go System->Preferences->Sound. You will see the 'devices' tab first. and change anything here set to 'autodetect' to 'ALSA'. Worked for me with this problem.

---

### Post by vikrant82 on 2008-07-15
> vikrant is suggesting is to go System->Preferences->Sound.

Well that's not what I meant. Pulseaudio also has its own volume manager. 

Go [here.]("https://wiki.ubuntu.com/PulseAudio"), under installation section.

---

### Post by smorar on 2008-07-23
Just installing Pulse audio's volume manager + related utilities, and messing around with them seems to have prevented this issue from occuring again.

If it happens again, I'll revisit this thread, and pick up the discussion again.

Thanks.

---

