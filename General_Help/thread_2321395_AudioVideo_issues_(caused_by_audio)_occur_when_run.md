---
title: "Audio/Video issues (caused by audio) occur when running steam game (MB:W)"
date: 2016-04-22
forum: General Help
---

### Post by John_Throw on 2016-04-22
I'm pretty new to linux in general.

I'm running a ESXi6 VM with 14.04 on it using PCI passthrough of a R5 270 (fglrx) and a USB card for keyboard and mouse.
That all seems to work fine, everything works fine actually as long as long as I don't have any sound devices.

Sound mostly works using the HDMI audio, passed through onboard Aliza sound device or a USB sound card. Videos and MP3s play fine, startup sounds are OK, etc.

If I run mount and blade warband, the vast majority of the time it runs fine the first time I run it after boot. The second time I run it always fails with the audio messed up after load, the music is a rumbling noise. The video appears to be stuck with menu items not highlighting or the menu not loading at all. If I wait long enough the view will update. I can "guess click" to close this and it will eventually return to desktop and things return to normal. But its broken until a restart of the guest.

UNLESS, I start an MP3 playing and then load the game while its playing. Then the game will load fine every time! I got this weird idea because windows VMs with VMware are sometimes listed as having issues that are fixed by just starting WMP.

Anyone have any ideas on how to fix this? I've tried 3 different sound cards and they all had the option. The video stuck issues doesn't happen at all if a sound card is removed from the VM entirely. So that all points to sound being the issue. Running an mp3 before hand fixing it also does. But why does it fix it?

It doesn't happen if I install to bare metal, but that is going to be different of course.

---

### Post by John_Throw on 2016-04-25
Edit: So I seem to have solved this. Based on some other guides I was trying to change setting in pulseaudio to fix it. I don't have my notes in front of me but I was editing the fragment and fragment size parameters in:
/etc/pulse/default.pa

I *think* values were by default:
default-fragments = 10
default-fragment-size-msec = 4
Although I might have the numbers mixed up. A guide I read suggested, 5 and 2 as values. I chose that and the audio sounded static-y when the game loaded...but it never got stuck during a bunch of tests even though it sounded bad. I then changed the values to 5,4 (again, I might have these values backwards) and the audio sounded normal and I still was unable to cause things to get stuck.

I'm pretty confident that solved it now, even though I don't understand why.

---

