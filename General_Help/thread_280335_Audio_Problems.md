---
title: "Audio Problems"
date: 2006-10-19
forum: General Help
---

### Post by Duffy on 2006-10-19
I am having problems with a new installation of Ubuntu 6.06.1 on a computer I just built.  

Audio pretty much has two settings - High or off.  I cannot get the slider controls to do anything but either go max or mute.  There are two devices on the Volume Control: Realtek ALC861 - HDA ATI SB (ALSA Mixer) and Realtek (ALC861) OSS Mixer. When I select the HDA ATI SB, nothing happens as in no audio no matter what controls are adjusted. When I select the Realtek, I get audio, but the controls do full or off only - the cannot be set in the middle at all. Anyone know a solution?

---

### Post by Duffy on 2006-10-27
Folks, I posted a request for help four days ago and got zero responses. I am still having these issues even after upgrading to V6.10

Audio pretty much has two settings - High or off with most - not all - programs. Sometimes I cannot get the slider controls to do anything but either go max or mute. There are two devices on the Volume Control: Realtek ALC861 - HDA ATI SB (ALSA Mixer) and Realtek (ALC861) OSS Mixer. When I select the HDA ATI SB, nothing happens as in no audio no matter what controls are adjusted. When I select the Realtek, I get audio, but the controls do full or off only - the cannot be set in the middle at all. 

If I use EMMS, the volume works fine just as it should. But other programs the volume is either 100% or 0%. In some cases I cannot even turn it off, it depends on the application.

Anyone know a solution?

---

### Post by John.Michael.Kane on 2006-10-27
Have alook over this
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

If you still can't get your sound working,and want to file a bug look here [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

---

### Post by Duffy on 2006-10-28
Thanks, but my issue isn't that the sound is not working. It works, but it is how it works that is the problem. For instance, I can control the volume level with XMMS, but I cannot control the volume output with gMFSK.  I also cannot control the audio level input into gMFSK. Same thing if I install the Real Player. The volume is either at 100% or off - no way to set the volume at the mid-point.

aviplayer is the same way, volume level seems to be 100%, and changing the volume control on the player has no effect.

Kaffiene on the other hand, the volume control works as it should.

Question, why do some applications work fine and others do not - aren't they all using the same ALSA application? If not, how do I get all the applications to work the same way?

---

