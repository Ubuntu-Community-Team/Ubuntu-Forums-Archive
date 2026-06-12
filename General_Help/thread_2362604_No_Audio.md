---
title: "No Audio"
date: 2017-05-31
forum: General Help
---

### Post by Quarkrad on 2017-05-31
Running Mate 16.04.  A few weeks ago I started to experience my audio stopping - I would get it going again by opening sound preferences and re clicking on the output device but now it has stopped all together.  I have tried a number of things but starting to go into things I'm not sure of, so stopping.   I  have the following:

```
dad@dadubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

When I launch alsamixer in terminal I get mixer1.png and if I hit the Tab key I get mixer2.png.  When I launch Pulseaudio Volume Control I get pa1.png.  Any help appreciated.

---

### Post by Quarkrad on 2017-05-31
I have got sound back via step 2 in [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) - not sure exactly what did it though.  I will leave thread open for a few days to see if sound is consistent before marking closed.

---

### Post by Quarkrad on 2017-06-01
Hmm.. something odd is happening (and it keeps happening).  I boot up and all is well -  can play audio files via any audio player or as a preview via the mouse.  My Sound Preferences are as s1 and s2 (note that the Output Volume shows the level) - PulseAudioVolume Control is pulse1good and pulse2good and I've also shown the alsamixer output.   All is good.

---

### Post by Quarkrad on 2017-06-01
Then for no reason something happens and I have no audio from my audio players - although I do get audio via a web browser.   Note s3 and s4 show no output level (they are greyed out) - and the hardware device has changed.  PulseAudio Volume Control just cannot make a connection.   When in this mode (no audio) if I try and play a file via vlc it says *Audio Output Failed: The audio device "default" could not be used: Connection refused*.

---

### Post by Quarkrad on 2017-06-05
bump

---

### Post by patrickbot on 2017-06-06
Bump; I'm having similar problems with no audio via HDMI in the latest version of Ubuntu, tried numerous fixes already with no luck.

---

### Post by Quarkrad on 2017-06-06
I would be interested to know what flavor and version of Ubuntu you are using.

---

### Post by patrickbot on 2017-06-06
Ubuntu LTS 16.04, dual boot system with Windows 10. Sound works fine in Windows 10 through all outputs, but I can only get sound through the analogue port using Ubuntu. Re-installing Ubuntu didn't solve the problem. Everything appears to be correctly configured in the GUI. Tried numerous fixes so far to no avail.

---

### Post by Quarkrad on 2017-06-07
Just re-installed 16.04 and updated everything - now Sound Properties will not launch. Initially it loads but then immediately closes - this happens via the gui or terminal.  This is my terminal output:

```
dad@dadubuntu:~$ mate-volume-control
shm_open() failed: No such file or directory
shm_open() failed: No such file or directory
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Protocol error


(mate-volume-control:7108): libmatemixer-alsa-WARNING **: Failed to open ALSA control for default: Connection refused

(mate-volume-control:7108): GLib-CRITICAL **: g_source_remove_poll: assertion '!SOURCE_DESTROYED (source)' failed
Segmentation fault (core dumped)

```

---

### Post by Quarkrad on 2017-06-10
bump - this is really odd.  Reinstalled 16.04.2 and still having same issue. Tried even more 'google' suggestions and sound does work - and then for some reason, after all sorts of times, it disappears (not in a browser - just playing audio files on Desktop/pc).  Pulseaudio Volume Control just sits there saying 'Establishing connection, please wait' and Sound Settings refuses to launch.

---

### Post by Quarkrad on 2017-06-14
Audio has come back but I do not think it was something I did. I got some help on launchpad and went through [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) - which I've done before.  I got to step #1c and rebooted - no effect, still had sound issues.  However, a few boots later and the audio seems to have corrected itself. I will leave this thread as unsolved as Patrickbot still has an issue.

---

### Post by Quarkrad on 2017-06-15
Spoke too soon - one day later and I'm back to square one.  Still having trouble as initially posted.

---

### Post by Quarkrad on 2017-07-16
Still having problems but perhaps a few more clues.  Clean boot gives me good1 and good2 and audio from Desktop audio file - after a random time (tends to be quite long though) something changes my hardware settings to bad1 and bad2.  I can get audio back, and good 1 and good2 by this command in terminal** pulseaudio --kill**.  Interestingly (or is it?) clean boot, good1 and good 2 with audio - launch firefox and - no audio bad1 and bad2.  If I close firefox and run pulseaudio --kill then I'm back to audio and good1 and good2.  Obviously I have only one set of h/w on my motherboard but something somewhere seems to change the settings - either randomly or when firefox is launched.

---

### Post by Quarkrad on 2017-07-16
Firefox is fixed to pulseaudio so I guess there is no surprise that when I **pulseaudio --kill** during a youtube video (on FF) firefox freezes.  If I launch Audacity and play a Desktop file no sound, this is because Audacity is pointing to an HDMI channel. If I change Audacity to point to my PCH channel then I hear audio.  My motherboard has 4 settings:
HDA Intel PCH: ALC887-VD Analogue (hw:1.0)
HDA INtel HDMI:0 (hw:0,3)
HDA INtel HDMI:1 (hw:0,7)
HDA INtel HDMI:2 (hw:0,8)

The PCH setting is the one that produces audio and good1 and good2 - so my issue, perhaps, is what changes this setting to one of the HDMI settings?

---

### Post by Yellow Pasque on 2017-07-16
@Quarkrad: do you use the HDMI audio?

---

### Post by Quarkrad on 2017-07-17
No - this is a simple standalone pc with a cheapish pair of desktop speakers connected via standard 3.5mm jack into the back of my motherboard.

---

### Post by Quarkrad on 2017-07-17
I'm getting confused now - on a reboot I have sound coming from my speaks when I play a desktop audio file.  My sound settings are as attached.  When I press Test Speakers I get no sound out of the speakers.  If I close the Sound Preferences window and play the audio file I get sound out of the speakers.  Sound preferences does not change, if I open it again it is per attached. Surely, if I test the speakers I should get sound out of them?

---

### Post by Yellow Pasque on 2017-07-17
I would try disabling the HDMI audio if not using it.

```
echo "options snd-hda-intel enable=0,1" | sudo tee /etc/modprobe.d/disablehdmi.conf
```

After you reboot, then reset the pulseaudio config to make it "forget" about the HDMI:
```
rm -rf ~/.config/pulse*; pulseaudio -k
```

If you're still having issues or HDMI is still enabled, get more info:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Quarkrad on 2017-07-18
Wow - that did it, I'm very grateful.  One thing you might be able to help me with.  I use Ubuntu Mate that has the ability to play an audio file when you hover the mouse over it (preview audio) - which I find very useful.  At the moment if I hover the mouse over a Desktop audio file no music plays - nor does audio play if I try and play the file with Rhythmbox (I don't use Rhythmbox generally but always use the hover/preview functionality). However, I have set in System Preferences, for audio files to be played with VLC and if I double click an audio file I get audio (I have configured VLC to point to my **ALSA audio output** and **HDA Intel PCH, ALC887 default audio device**). (The same happens if I play via Audacity - I have configured it to point to Intel PCH).  Is there a command that will enable me to have audio via the hover/preview function?

---

### Post by Yellow Pasque on 2017-07-18
Rhythmbox uses gstreamer, and I believe caja (the MATE file manager) does too. Make sure you've got the appropriate packages for playing all formats:
```
sudo apt-get install gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-tools gstreamer1.0-pulseaudio
```

---

### Post by Quarkrad on 2017-07-19
Hmm... I seemed to be ok re: those packages.

```
dad@dadubuntu:~$ sudo apt-get install gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-tools gstreamer1.0-pulseaudio
[sudo] password for dad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer1.0-pulseaudio is already the newest version (1.8.3-1ubuntu0.4).
gstreamer1.0-tools is already the newest version (1.8.3-1~ubuntu0.1).
gstreamer1.0-plugins-bad is already the newest version (1.8.3-1ubuntu0.2).
gstreamer1.0-plugins-bad set to manually installed.
gstreamer1.0-plugins-ugly is already the newest version (1.8.3-1ubuntu0.1).
gstreamer1.0-plugins-ugly set to manually installed.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

---

### Post by #&amp;thj^% on 2017-07-19
> **Quarkrad said:**
> Wow - that did it, I'm very grateful.  One thing you might be able to help me with.  I use Ubuntu Mate that has the ability to play an audio file when you hover the mouse over it (preview audio) - which I find very useful.  At the moment if I hover the mouse over a Desktop audio file no music plays - nor does audio play if I try and play the file with Rhythmbox (I don't use Rhythmbox generally but always use the hover/preview functionality). However, I have set in System Preferences, for audio files to be played with VLC and if I double click an audio file I get audio (I have configured VLC to point to my **ALSA audio output** and **HDA Intel PCH, ALC887 default audio device**). (The same happens if I play via Audacity - I have configured it to point to Intel PCH).  Is there a command that will enable me to have audio via the hover/preview function?
Have you opened Caja>>Edit>> Preferences>>Top Tabs>> Preview and select "Local Files Only"
Should get you a hover/preview option for audio files.

---

### Post by Quarkrad on 2017-07-19
Yes - mine is exactly the same as above.

---

### Post by Yellow Pasque on 2017-07-19
> **Quarkrad said:**
> Pulseaudio Volume Control just sits there saying 'Establishing connection, please wait' and Sound Settings refuses to launch.

Is this still happening to you? This sounds like what I experienced when I ran Ubuntu MATE 16.04 in a VM. I would have to start pulseaudio manually at every login. I guess some other folks experienced it too.
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1604497](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1604497)
It seems the bug was fixed in later Ubuntu versions, but there's no indication it was fixed in 16.04.

> Tried even more 'google' suggestions and sound does work

I'm guessing you added your user to the audio group and set programs to use the sound card directly instead of through pulseaudio?

---

### Post by Quarkrad on 2017-07-20
I was not a member of the audio group (name was there but no tick in the box) - but having joined there is no difference, hover does not work.  Pulseaudio volume control just says **Pulseaudio Establishing connection. Please wait**.   Having pointed VLC and Audacity to my PCH sound card I can double click and hear audio (through either app).  However, if I open an audio file with Rhythmbox I hear no sound.  I'm sure I read on an unrelated thread (that I no longer can find) there is a relationship between Pulseaudio issues and systemd.

```
dad@dadubuntu:~$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7d10000 irq 31
dad@dadubuntu:~$ 

```

---

### Post by Quarkrad on 2017-07-20
This sort of sums up where I am. I am listening to an audio track playing via VLC - I can adjust the volume via top panel volume control but Sound Preferences says there is no application playing.  Pulseaudio is connecting.  This isn't surprising as I've pointed VLC to my PCH card.  Perhaps Sound Preferences is not that accurate - logically I would have expected Sound Preferences to be saying that currently VLC is playing an audio file.

---

### Post by Yellow Pasque on 2017-07-20
When you first log in, try and run pulseaudio:
```
pulseaudio&
```

Does volume control and hover preview work properly then?

> I can adjust the volume via top panel volume control but Sound Preferences says there is no application playing. ... Perhaps Sound Preferences is not that accurate - logically I would have expected Sound Preferences to be saying that currently VLC is playing an audio file. 
That's because you're playing VLC directly to the soundcard rather than pulseaudio.

> hover does not work...if I open an audio file with Rhythmbox I hear no sound. 

They're not going to work until pulseaudio is running properly. (Are you sensing a theme here?)

---

### Post by Quarkrad on 2017-07-20
Yes - I can hover and get audio - the output is:

```
dad@dadubuntu:~$ pulseaudio&
[1] 2374
dad@dadubuntu:~$ E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.
```

The killer app is Firefox - as soon as I play something on youtube with audio then pulseaudio crashes in the background.  When/If I close Firefox hover/audio is not working due to the Pulseaudio crash.  You are right - this is a Pulseaudio issue.  I am very happy how you have helped me - I guess further effort is not going to solve this PA issue so perhaps not a good use of your time.  Since 8.04 this is the first real unsolvable (I guess a bug or incompatibility somewhere) that I have had.  Thanks.

---

