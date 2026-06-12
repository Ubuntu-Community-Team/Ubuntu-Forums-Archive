---
title: "Issue with Audio Sampling Rate on Ubuntu 24.10 with External Audio Interface and Nvid"
date: 2024-11-21
forum: General Help
---

### Post by spiritwind on 2024-11-21
[SIZE=4][FONT=comic sans ms]Hi everyone,
[/FONT][/SIZE]
[SIZE=4][FONT=comic sans ms]I&#8217;ve installed Ubuntu 24.10 and I&#8217;m experiencing an issue with my external audio interface and JACK.
[/FONT][/SIZE]
[SIZE=4][FONT=comic sans ms]I have a Behringer UMC404HD set to 192kHz, but every time I start JACK, the Nvidia GPU (selected as the audio interface) defaults to a 48kHz sampling rate, overriding my external audio settings.[/FONT][/SIZE]
[SIZE=4][FONT=comic sans ms]I&#8217;ve attached screenshots showing:
[/FONT][/SIZE]

[LIST=1]
[*][SIZE=4][FONT=comic sans ms]The Nvidia GPU being automatically selected at 48kHz.[/FONT][/SIZE]
[*][SIZE=4][FONT=comic sans ms]The available interfaces, including my external audio device (UMC404HD 192k).[/FONT][/SIZE]
[/LIST]
[SIZE=4][FONT=comic sans ms]Despite selecting the correct interface and settings, the GPU keeps overriding the sampling rate at startup.[/FONT][/SIZE]
[SIZE=4][FONT=comic sans ms]How can I force JACK to use my external interface and maintain the 192kHz sampling rate without conflicts?
[/FONT][/SIZE]
[SIZE=4][FONT=comic sans ms]Thanks in advance for your assistance![/FONT][/SIZE]


[[IMG]https://i.postimg.cc/ZWVQ8n91/Whats-App-Image-2024-11-21-at-20-50-22-1.jpg[/IMG]]("https://postimg.cc/ZWVQ8n91")

[[IMG]https://i.postimg.cc/McHFdwVX/Whats-App-Image-2024-11-21-at-20-50-22.jpg[/IMG]]("https://postimg.cc/McHFdwVX")

---

### Post by bobunderwood99 on 2024-11-21
Ubuntu 24.10 has Pipewire. [https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/home](https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/home) 

You cannot use QJackCtl to set sample rate and buffer size in Pipewire - it doesn't work.

I suggest you install [Ubuntu Studio Installer]("https://ubuntustudio.org/ubuntu-studio-installer").

Then use [Audio Configuration]("https://ubuntustudio.org/audio-configuration/") to set the Pipewire sample rate and Quantum (buffer size).

---

### Post by spiritwind on 2024-11-22
> **bobunderwood99 said:**
> Ubuntu 24.10 has Pipewire. [https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/home](https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/home) 

You cannot use QJackCtl to set sample rate and buffer size in Pipewire - it doesn't work.

I suggest you install [Ubuntu Studio Installer]("https://ubuntustudio.org/ubuntu-studio-installer").

Then use [Audio Configuration]("https://ubuntustudio.org/audio-configuration/") to set the Pipewire sample rate and Quantum (buffer size).

How can I use PipeWire with my external audio interface, make it recognized, and specifically adjust the sample rates? I know about the app Qpwgraph, but it feels much more complicated compared to QJackCtl. Can you help me?

---

### Post by bobunderwood99 on 2024-11-22
Do what I suggested above. Your interface will pickup the sample rate and buffer size set in Pipewire.

---

### Post by bobunderwood99 on 2024-11-23
Are you using the (Behringer) interface for music production or outputting surround sound?

---

