---
title: "Volume very low after upgrade"
date: 2015-08-29
forum: General Help
---

### Post by Halbarad on 2015-08-29
PC: laptop Asus Z53H
Sound card: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)

I cloned my Linux sda6 with Clonezilla Live. On reboot, I realized that I had extremely low audio in just two situations: Skype and the sound effects of Wesnoth (the music is ok). (There were no sound issues either in Skype or in Wesnoth before.) Edit: I did the backup after upgrading some packages (libtag1-vanilla; libtag1c2a; libnautilus-extension1a; nautilus-data) but, contrary to all my expectations, the audio problem was still there after restoring a much older backup; therefore the upgrade was not responsible for it.
If I browse to the Wesnoth sound directories the ogg files play alright, but all the wavs have extremely low audio. Extremely low means I thought they didn't play at all until I set all the volume sliders to max in pavucontrol; and even then, they sounded very far and muffled. Now that I know they are there, I can hear them, very very faintly, even at normal volume, provided that the background is perfectly silent. **But, if I play some musical *wavs,* the audio is ok.**
First I checked the volume sliders in alsamixer and pavucontrol. (If I set the volume to max in pavucontrol I can just hear the wavs and skype, but all other sounds deafen me).
Then I uninstalled pulseaudio (it's required by Skype) rebooted and checked: Skype was mute as I expected, but the sound files in the Wesnoth sound dir still played at extremely low volume. So I also uninstalled and reinstalled alsa-base and alsa-utils but this did not help. 
I tried two speaker tests.
> speaker-test -c2 -t wav
        works well
> speaker-test -c1 -t wav
	low, muffled
So I also tried
> aplay /usr/share/sounds/alsa/Front_Center.wav
	muffled, again, I can hardly hear what she says at max volume.
Following the troubleshooting guide by Lkjoel and Wildmanne, I typed the following command from terminal:
> ~ $&#8827;echo "Sound cards recognized by the system:"; lspci -nn | grep --color=none '\[04[80][13]\]'; echo "Sound cards recognized by ALSA:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel modules: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done; echo "Sound cards recognized by ALSA, and activated:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel drivers in use: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done

     Sound cards recognized by the system:
     00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)
     Sound cards recognized by ALSA:
     00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)
     Sound cards recognized by ALSA, and activated:
     00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)

I am at a loss. I edited the BIOS parameters and set the speakers volume to the top, but to no effect.
My planned next move is to remove the upgraded packages, one at a time, and see what happens.
Any help would be much appreciated

---

### Post by Halbarad on 2015-08-29
I think all the trouble is with libtag1-vanilla and libtag1c2a; they are both beta versions. (I just wonder why I accepted the upgrade, damn it.) By Synaptics I can try to roll back the libtag1-vanilla, but it would uninstall many packages (including e.g. vlc, and above all several libraries) so I'm afraid the system would be broken after that.

---

### Post by Halbarad on 2015-08-29
It may seem incredible, but this does NOT depend on the upgrades I made (I felt almost sure it should have to do with the vanilla stuff). I restored an old image (Dec. 2014) and the problem is still there. Therefore, I'd say it is a problem connected to the hardware or to the firmware. Maybe Clonezilla live or libtag1-vanilla somehow interfered with the firmware and set some switch or flag or...? -- I tried to set the audio volume to max from the keyboard controls (F11 and F12); it worked by the problem is still there, both with Skype and with the Wesnoth files.
I am going to boot from Windows XP (it has been sleeping for such a long time...) and see if anything can be done. I've also copied the Wesnoth sounds to the Win partition to test them there. These PCs are so strongly integrated with Windows that the problem might be solved there... My next choice will surely be a Linux friendly PC!
This post does not seem very popular ;-) I just go on writing in case anyone might have similar problems in the future.

---

### Post by Halbarad on 2015-08-29
In XP audio volume is ok, both for Skype and for the Wesnoth WAV sounds. It's so weird that in Lubuntu some WAV files are played at the right audio volume while others are practically silenced... In Audacious the diagram for the volume audio shows higher levels for the muffled WAVs than for the loud ones. The muffled WAVs remain muffled even if I convert them to ogg; moreover, at a very high volume, they are distorted and "scratching".
Another test: the sound is ok in the speakers, that is if I unplug my headphones. I tried different headphones, but the problem persists.
Well, if no one can help I think I am going to give up, cannot spend my life studying the vagaries of my PC :-)

---

### Post by Halbarad on 2015-08-30
I've explored my sound problem a bit more. I realized that most of the data I provided here are irrelevant, if not misleading. Therefore I'd open a new thread where only the relevant data are posted.

---

