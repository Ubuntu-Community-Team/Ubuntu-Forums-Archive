---
title: "Record Sound which is transmitted to a TV connected over HDMI"
date: 2015-01-14
forum: General Help
---

### Post by akshay-sulakhe on 2015-01-14
Hello friends,

I am using Ubuntu 14.04 X64 on my desktop. For some project, I am receiving a SIP call from another machine and the screen is being transmitted over VNC. Now I would like to record the screen with some screenrecording software(will search them soon) but with audio also. 
Can anyone tell me how can I record the audio which is being transmitted over speakers via an HDMI cable?

---

### Post by grahammechanical on 2015-01-14
I use Audio Recorder. It puts a app-indicator in the top panel which allows us to start and stop recording with a single click. This is what the author says about it.

> [COLOR=#333333][FONT=monospace]This is an audio recorder application for the GNOME 3 and Ubuntu's Unity Desktops.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]This amazing program allows you to record your favourite music and audio to a file. It can record audio from your system's soundcard, microphones, browsers, webcams & more. Put simply; if it plays out of your loudspeakers you can record it. This can also record your Skype-calls automatically.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]It has an advanced timer that can:
* Start, stop or pause recording at a given clock time.
* Start, stop or pause after a time period.
* Stop when the recorded file size exceeds a limit.
* Start recording on voice or sound (user can set the audio threshold).
* Stop or pause recording on "silence" (user can set the audio threshold and delay).[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]The recording can be atomatically controlled by MPRIS2-compatible media players.
Skype. It can also record all your Skype calls without any user interaction.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]This program supports several audio (output) formats such as OGG audio, Flac, MP3 and WAV.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]The installation is very easy. Run these commands on the command line:[/FONT][/COLOR]


I have found that installing the PPA and then installing audio-recorder was enough. Some of the packages listed as necessary may already be installed.

[https://launchpad.net/~osmoma/+archive/ubuntu/audio-recorder](https://launchpad.net/~osmoma/+archive/ubuntu/audio-recorder)

Regards.

P.S. I have used Audio Recorder since it first came out. At that time we needed to compile the code to get the application. I recommend Audio Recorder.

---

