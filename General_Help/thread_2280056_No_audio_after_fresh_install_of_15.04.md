---
title: "No audio after fresh install of 15.04"
date: 2015-05-27
forum: General Help
---

### Post by buzzie1 on 2015-05-27
[FONT=Verdana]Hi.  I was initially using Ubuntu 12.04 and there was no issue with my audio.  Upon performing a fresh install of Ubuntu 15.04, I no longer had  audio.  I want to use device 00 as noted in the lspci entry listed below, however 'aplay -l' only lists device 01.  How can I get Ubuntu 15.04 to recognize device 00 when I issue 'aplay -l' on my system?  Any suggestion(s) would greatly be appreciated.[/FONT]


[FONT=Verdana]lspci:[/FONT]

[FONT=Verdana]00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)[/FONT]
[FONT=Verdana]01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)



aplay -l:
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


[/FONT]

---

### Post by QDR06VV9 on 2015-05-27
Hi buzzie1 This was found on the same page you posted yours
[http://ubuntuforums.org/showthread.php?t=2279687](http://ubuntuforums.org/showthread.php?t=2279687) see post 2

---

### Post by mattharris4 on 2015-05-28
The "alsamixer" fix may solve part of the OP's issue.  However, it does not necessarily solve his issue about switching audio cards.  If he wants to switch just to see if his card is bad I would suggest checking alsamixer first, it may solve the problem as it has many others.  He can also attempt to switch audio cards in alsamixer as the instructions in line one say how.  However, if he has another reason to switch audio cards such as  suspecting compatibility issues (as he seems to think the one card is not recognized in the first place) or knows one card is better for something he wants to do with his computer and the alsamixer instructions don't help unfortunately I don't have the answer (I don't have much knowledge of that issue).  I am copying and pasting the alsamixer instructions below, I hope they are helpful:

Check alsamixer.  Here is a link to instructions to fix several different issues regarding sound but you need section two:  [http://www.unixmen.com/2012003-howto...lem-on-ubuntu/]("http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/") .

Here is the pertinent info:

PulseAudio controls underlying ALSA-level volume controls. To change the ALSA-level volume controls directly, you can do [[COLOR=#009900]_the following_[/COLOR][IMG]http://images.intellitxt.com/ast/adTypes/icon1.png[/IMG]]("http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/#"):Open a terminal. (The quickest way is the **Ctrl-Alt-T** shortcut)Enter** &#8220;alsamixer&#8221;** and press the Enter key.
In this user interface, you can do the following:

[LIST=1]
[*]Select your correct sound card using **F6 and select F5** to see recording controls as well
[*]Move around with left and right arrow keys.
[*]Increase and decrease volume with up and down arrow keys.
[*]Mute/Unmute with the **&#8220;M&#8221;** key. An &#8220;MM&#8221; means muted, and &#8220;OO&#8221; means unmuted.
[*]Exit from alsamixer with the Esc key
[/LIST]

I hope this solves the problem.



You will need to follow steps 2-4 with Master, Headphon and Speaker.  If  they aren't muted ("MM" under the graph bars means that function is  muted) before attempting to change them, you have another issue  entirely.

---

### Post by buzzie1 on 2015-05-28
> **runrickus said:**
> Hi buzzie1 This was found on the same page you posted yours
[http://ubuntuforums.org/showthread.php?t=2279687](http://ubuntuforums.org/showthread.php?t=2279687) see post 2



The alsamixer solution did not fix my audio problem. The attached shows the proper sound card selected in alsamixer and the other attachment for 'Sound Prefences' should show built-in anallog corresponding to the following device.  As previously mentioned, 'aplay -l' does not list card 0.


[FONT=Verdana]00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)[/FONT] 



ubuntu-mate@ubuntu-mate:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by QDR06VV9 on 2015-05-28
Forgive Me i was preoccupied yesterday!(No Excuse)
Do you have a Bios switch?(Enabled or Disabled)
Dose it work using a live cd?

---

### Post by buzzie1 on 2015-05-28
> **runrickus said:**
> Forgive Me i was preoccupied yesterday!(No Excuse)
Do you have a Bios switch?(Enabled or Disabled)
Dose it work using a live cd?

Hi.  Yes I have it enabled in the BIOS and previous versions such as 12.04 work fine with the built-in audio.  Ubuntu Mate 15.04 does not work.

---

### Post by QDR06VV9 on 2015-05-28
Would you install inxi it will help me and others to help.
```
sudo apt-get install inxi
```
Then paste back output
```
inxi -A
```
Just to show what gets reported here is mine
> mate@mate-Aspire-M3300:~$ inxi -A
Audio:     Card-1: NVIDIA GF119 HDMI Audio Controller driver: snd_hda_intel Sound: ALSA ver: k3.18.14-031814-lowlatency
           Card-2: Creative Labs SB Audigy driver: snd_emu10k1 

---

### Post by buzzie1 on 2015-05-28
> **runrickus said:**
> Would you install inxi it will help me and others to help.
```
sudo apt-get install inxi
```
Then paste back output
```
inxi -A
```
Just to show what gets reported here is mine

inxi -A gives me the following.  I want to use Card-2 in this case


Audio:     Card-1 NVIDIA High Definition Audio Controller driver: snd_hda_intel
           Card-2 Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k3.19.0-15-generic

---

### Post by QDR06VV9 on 2015-05-28
Sorry busy day for me.
Alsa seems to be out of wack.
Lets reinstall
```
**sudo apt-get remove --purge alsa-base pulseaudio**
```
Now install again
```
**sudo apt-get install alsa-base pulseaudio**
```
Reload Alsa
```
**sudo alsa force-reload**
```
If you do not have pulseaudio volume contorl It is a little better tool than alamixer
to install
```
sudo apt-get install pavucontrol
```
> PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume
control tool (mixer) for the PulseAudio sound server. In contrast to
classic mixer tools this one allows you to control both the volume of
hardware devices and of each playback stream separately. It also allows
you to redirect a playback stream to another output device without
interrupting playback.
Fingers Crossed

---

### Post by buzzie1 on 2015-05-28
> **runrickus said:**
> Sorry busy day for me.
Alsa seems to be out of wack.
Lets reinstall
```
**sudo apt-get remove --purge alsa-base pulseaudio**
```
Now install again
```
**sudo apt-get install alsa-base pulseaudio**
```
Reload Alsa
```
**sudo alsa force-reload**
```
If you do not have pulseaudio volume contorl It is a little better tool than alamixer
to install
```
sudo apt-get install pavucontrol
```

Fingers Crossed

Appreciate your input,  No luck after performing the following and now get error attached when trying to select 'Sound Preferences'

**sudo apt-get remove --purge alsa-base pulseaudio**

**sudo apt-get install alsa-base pulseaudio**

**sudo alsa force-reload**

**sudo apt-get install pavucontrol**

---

### Post by QDR06VV9 on 2015-05-28
Did you try to open Pulseaudio Volume Control? It is in sound and video in your menu.

---

### Post by buzzie1 on 2015-05-28
> **runrickus said:**
> Did you try to open Pulseaudio Volume Control? It is in sound and video in your menu.

Pulseaudio Volume Control from the menu shows the attached

---

### Post by QDR06VV9 on 2015-05-28
On the Config Tab at the top is where you want to be.
Here is a Screen shot for mine

---

### Post by buzzie1 on 2015-05-28
> **runrickus said:**
> On the Config Tab at the top is where you want to be.
Here is a Screen shot for mine


My screenshot looks different than yours.  Guess the newer versions don't like my system config. Might have to add an audio card to overcome issue???

---

### Post by QDR06VV9 on 2015-05-29
Ok one last attempt to get this card working, It would appear that card is indeed problematic with Alsa.
So if you would try this.
Open this file with gedit or text editor of your choice I am going to use gedit in this case though.
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
And then add this line at the bottom of the file.
```
options snd-hda-intel model=3stack
```
Save and Close, Then Reboot.
Hopefully that will let pulseaudio volume control to see that card.
And on the odd chance that fails, There is some good info here [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
Usually best to ignore all the stuff about recompiling ALSA and go directly to 'Manually Specify Module Parameters
Best of Luck;)

---

### Post by buzzie1 on 2015-05-29
> **runrickus said:**
> Ok one last attempt to get this card working, It would appear that that card is indeed problematic with Alsa.
So if you would try this.
Open this file with gedit or text editor of your choice I am going to use gedit in this case though.
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
And then add this line at the bottom of the file.
```
options snd-hda-intel model=3stack
```
Save and Close, Then Reboot.
Hopefully that will let pulseaudio volume control to see that card.
And on the odd chance that fails, There is some good info here [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
Usually best to ignore all the stuff about recompiling ALSA and go directly to 'Manually Specify Module Parameters
Best of Luck;)

Adding 'options snd-hda-intel model=3stack' to /etc/modprobe.d/alsa-base.conf worked!!!  Thank you very much for your assistance :)

---

### Post by QDR06VV9 on 2015-05-29
> **buzzie1 said:**
> Adding 'options snd-hda-intel model=3stack' to /etc/modprobe.d/alsa-base.conf worked!!!  Thank you very much for your assistance :)
That's Great:D
Could you do just one more thing it will help other's with similar problems and mark this thread solved!
Good Job!
Kind Regards

---

### Post by mattharris4 on 2015-05-30
> **buzzie1 said:**
> Adding 'options snd-hda-intel model=3stack' to /etc/modprobe.d/alsa-base.conf worked!!!  Thank you very much for your assistance :)

Glad you found a solution to your computer issue.  Enjoy your new Buntu install.

---

### Post by buzzie1 on 2015-05-30
> **runrickus said:**
> That's Great:D
Could you do just one more thing it will help other's with similar problems and mark this thread solved!
Good Job!
Kind Regards


It has been flagged as solved.  Thanks again :)

---

### Post by QDR06VV9 on 2015-05-30
You are very welcome, Thanks for your patience.

---

