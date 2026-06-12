---
title: "simultaneous audio with alsa... not working?"
date: 2008-05-04
forum: General Help
---

### Post by javaTN on 2008-05-04
wasnt exactly what i should have called this post, but im in desperate need. i just migrated from the manifested giant (Windows XP) over to Ubuntu (no dual booting here!)... i love to listen to music when im playing my video games.

i just installed WoW and Counter Strike Source, both working fine... (even have in winecfg set to use audio as ALSA) because i know alsa is the only one that is supposed to support multiple audio outputs at the same time... however it doesnt seem to be working properly... i can only hear my game sounds, or my music playing (depending on which is running first).

how can i get both to work at the same time?!

thanks,
-tom

---

### Post by chronographer on 2008-05-04
Try setting up mpd and see if it works, its a great audio player, do a search and use it with sonata!

If you're keen, do 'sudo apt-get install mpd sonata' then edit /etc/mpd.conf to your liking, and then I do a 'sudo ln -s /pathtomusic /var/lib/mpd/music' Then I go 'mpd --create-db' now to use it jsut run sonata (alt F2, type sonata). Its really nice, uses ~10mb while playing and there is even a webUI called pitchfork, which I use to change the music playing on my server from my laptop.

---

### Post by javaTN on 2008-05-04
im not exactly sure how thats supposed to help me... thats just another audio player. ive tried using exaile, vlc, and other audio / media players while running my games.

im curious to know what my computer is using for sound, and what is this "PulseAudio" deal about (that i see when i go to the Sound configuration.)

out of the millions of people using Ubuntu, at least one person has to have brought up a similar question like this and has the answer to it.

---

### Post by jocko on 2008-05-04
You probably need to set up alsa to use software mixing.
This is one way to do it:

First find out the name of your sound card by pasting this in a terminal:
```
asoundconf list
```Then generate a default configuration for that card:
```
asoundconf set-default-card *name_of_your_card*
```where *name_of_your_card* is the output from the first command.

Then reload alsa:
```
sudo /sbin/alsa reload
```And for now it seems like pulseaudio blocks any other apps from using alsa, so either set **all** apps to use pulseaudio or set **all** apps to use alsa.

---

### Post by javaTN on 2008-05-04
so i ran aplay -l and returned this
> thomas@thomas-ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


then i generated a default config:
> thomas@thomas-ubuntu:~$ asoundconf set-default-card CK804

and lastly... reloaded alsa:
> thomas@thomas-ubuntu:~$ sudo /sbin/alsa reload
[sudo] password for thomas: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/thomas/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 5960(pulseaudio) 6089(mixer_applet2). 
Unloading ALSA sound driver modules: snd-intel8x0 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-intel8x0 snd-ac97-codec snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-intel8x0 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.


whats all that "garbage" in the 3rd step?

this didnt seem to work. :(

---

### Post by jocko on 2008-05-04
> **javaTN said:**
> so i ran aplay -l and returned this


then i generated a default config:


and lastly... reloaded alsa:


whats all that "garbage" in the 3rd step?

this didnt seem to work. :(

Sorry, I think I mixed up the commands for you. The first command should have been:```

asoundconf list
```The "garbage" is just information to tell you what is happening. It unloads and reloads the alsa modules, exactly what the command should do...
but it fails because pulseaudio and mixer_applet2 is still using alsa.
So first kill pulseaudio and mixer_applet2:
```
pulseaudio -k
killall mixer_applet2
```and then try to reload alsa again. Or reboot.

---

### Post by javaTN on 2008-05-04
ok, so what do i do now? it returned:
> thomas@thomas-ubuntu:~$ asoundconf list
Names of available sound cards:
CK804

---

### Post by jocko on 2008-05-04
> **javaTN said:**
> ok, so what do i do now? it returned:

Well, then it should work (if you managed to reload alsa or reboot).
Try playing sound from two different applications using alsa (not pulseaudio, it will prevent all other applications from using alsa).

---

### Post by javaTN on 2008-05-04
yes! it worked after i killed pulseaudio and the mixer... thanks alot!!!

---

