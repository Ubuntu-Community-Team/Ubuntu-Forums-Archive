---
title: "Mic Always On, Feedback when shut laptop lid"
date: 2016-09-19
forum: General Help
---

### Post by webmanoffesto on 2016-09-19
The mic on my Asus K55A Laptop is always on. If I turn up the output volume and tap on my laptop I hear the tap through the mic, I hear an ongoing buzz, and when I shut the laptop lid I get feedback (until is sleeps).

If I go to Settings / Sound I see that the mic shows as being is shut off, but as I explained, it is on.

How do I REALLY shut off the mic?

---

### Post by _duncan_ on 2016-09-19
alsamixer sometimes works when the GUI sound settings doesn't.

Open a terminal, then type the command:
```
alsamixer
```

F6 to change device
left / right arrow keys to navigate various volume settings
press m to toggle on/off
up / down arrow keys to increase/decrease volume
esc to quit

I'm not familiar with your laptop nor am I a sound guru. If it doesn't work maybe someone else can help.

---

### Post by webmanoffesto on 2016-09-20
[QUOTE=_duncan_;13547256]
Open a terminal, then type the command:
```
alsamixer
```

That seemed like a good method, so I tried it. It did not solve my always-on-microphone and microphone-speaker feedback problem. Right now, my only "solution" is to keep the sound off (i.e. speaker off) so I don't get feedback.

Also, after seeing this post "Audio Feedback - Make it stop!" [https://ubuntuforums.org/showthread.php?t=973201](https://ubuntuforums.org/showthread.php?t=973201)
I installed pulseaudio volume control. That didn't solve the problem either.

---

### Post by webmanoffesto on 2016-09-23
I'm still stuck with an always-on microphone. Can anyone help me resolve this problem?

> **_duncan_ said:**
> 
Open a terminal, then type the command:
```
alsamixer
```



I'm still stuck with an always-on microphone. Can anyone help me resolve this problem?


[[img]http://i.imgur.com/rM1cpIxs.png[/img]](http://imgur.com/rM1cpIx)
This Alsamixer screenshot shows the mic turned off, but actually it is still on and it give feedback too.

---

### Post by _duncan_ on 2016-09-23
another sound-related package you can play around with is alsa-tools-gui.

```
sudo apt-get install alsa-tools-gui
```

It consists of the following tools:
-echomixer
-envy24control
-hdajackretask
-hdspconf
-hdspmixer

I've been going through a lot of sound-related posts both here and askUbuntu regarding my own sound problems. Some people were able to solve their problems using these tools, particularly hdajackretask. It's supposed to allow you to retask your microphone jack into a headphone jack. Unfortunately the posts I saw did not provide step-by-step account of the solution. Maybe you can experiment with it a little.

---

### Post by webmanoffesto on 2016-09-23
> **_duncan_ said:**
> another sound-related package you can play around with is alsa-tools-gui.
```
sudo apt-get install alsa-tools-gui
```


I ran the code. Does it install Gnome Alsa Mixer? 
[[img]http://i.imgur.com/bTFpKvds.png[/img]](http://imgur.com/bTFpKvd)
I checked that and I put a "check mark" in the box but the mic is still on.


Following the instructions "Sound Troubleshooting Procedure" [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
I installed and ran PavuControl
```

$ sudo apt-get install pavucontrol 
$ pavucontrol

``` 
[[img]http://i.imgur.com/0pOwf2Ls.png[/img]](http://imgur.com/0pOwf2L)
But I still have the same problem

---

### Post by _duncan_ on 2016-09-24
No, alsa-gui-tools is not the same as gnome-alsa-mixer. It is a collection of GUI tools / programs to configure audio devices.

I mentioned alsa-gui-tools with emphasis on _hdajackretask_ as possible avenues for _your_ research. I can't give you detailed instructions since I have minimal experience with it.

I'm using standard ubuntu 16.04 unity, not gnome desktop. I'm not familiar with how to launch programs in gnome-desktop. In unity, hdajackretask can be launched using dash. It is a GUI program to retask audio jacks. I was thinking _maybe_ you can retask your microphone jack to do something else so it won't emit sound. **I have no idea which settings will work for you, if it work at all**.

Since you already executed the command "sudo apt-get install alsa-gui-tools", hdajackretask is already installed in your system, along with other tools mentioned in my earlier post. Im not sure, but _perhaps_ you can launch it using the terminal:

```
hdajackretask
```

or

```
hda-jack-retask
```


Good luck.

---

### Post by webmanoffesto on 2016-09-24
> **_duncan_ said:**
> Im not sure, but _perhaps_ you can launch it using the terminal:
```
hdajackretask
```


That sounded promising but I got an error message
```
tee: /sys/class/sound/hwC0D0/reconfig: Device or resource busy
```
[[img]http://i.imgur.com/QeVzMHds.png[/img]](http://imgur.com/QeVzMHd)
[[img]http://i.imgur.com/jNO4cV4s.png[/img]](http://imgur.com/jNO4cV4)

---

### Post by webmanoffesto on 2016-09-26
> **_duncan_ said:**
> 
```
hdajackretask
```


running "hdajackretask" at the commandline worked.
I set "internal mic" and "black mic right side" both to "not connected".
I clicked on "Install boot override", rebooted, and the microphone was finally shut off.

Thank you for your help.

Now I just have to remember this setting so I can turn the mic back on, if I ever need to use it.

---

