---
title: "Linphone via sip"
date: 2013-05-03
forum: General Help
---

### Post by yoramdavid on 2013-05-03
Hi,

Problem: cannot phone landlines.

Trying to find help to make my viopbuster account work on linphone has been a nightmare.
Most threats are old an with no solution, or the program does not look the way it is described any more.
Some people say it works, but they are at work and will post the settings once at home then they never come back !

So I am trying again.
I am using Linphone 3.3.2 (I know there is version 3.5 on the linphone web site, but it is a .tar.gz which one is supposed to unpack, then run `./configure' and finally `make' to compile the package. And that returns the same error it always returns when I run that command: "no target found, no file indicated".

Anyway, those are my sip settings:
Your display name: my name
Your username: [email]myusername@voipbuster.com[/email] (also tried with just "myusername")

Your SIP identity: sip:myusername@voipbuster.com
SIP proxy address: si:sip.voipbuster.com
Route (optional): sip:
Registration duration (sec): 3600
Register at startup (yes)
Publish presence information (yes)

There was then a popup window asking for the password, which was accepted.

I have opened the port 5060 on the router for the IP (which I made fixed IP).

When I start the linphone from the command line, I get all those errors:
[HTML]
(linphone-3:2223): GLib-GObject-WARNING **: g_object_set_valist: object class `GtkSettings' has no property named `gtk-button-images'
ortp-warning-Cannot read config, no core created yet.

(linphone-3:2223): libglade-WARNING **: Error loading image: Failed to open file '/usr/share/linphone/linphone2.png': Ficheiro ou directoria inexistente

(linphone-3:2223): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `icon'

(linphone-3:2223): libglade-WARNING **: Radio button group video_item could not be found

(linphone-3:2223): libglade-WARNING **: Error loading image: Failed to open file '/usr/share/linphone/linphone2.png': Ficheiro ou directoria inexistente

(linphone-3:2223): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `icon'
ALSA lib conf.c:4687:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:951:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib conf.c:4687:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default:0
ALSA lib conf.c:4687:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default:0
[COLOR="#FF0000"]DEBUG: [get_output_if] connect: Rede inacessível
DEBUG: [get_output_if] connect: Rede inacessível
DEBUG: [get_output_if] connect: Rede inacessível
DEBUG: [get_output_if] connect: Rede inacessível[/COLOR]

(linphone-3:2223): Gtk-WARNING **: Theme file for default has no name


(linphone-3:2223): Gtk-WARNING **: Theme file for default has no directories[/HTML]
In red: "connect: network not accessible"

I know I have to dial "00 + country code + phone number.
I tried to connect voipbuster on another computer with another account, and I was able to phone from it to linphone but not from linphone to voipbuster.
The status on the bottom bar is either "ready" or "Registration on sip:sip.voipbuster.com successful."

I added users which show offline although they are online.

I have tried many other softwares with no result. Ekiga was worse not being able to configure network. Others did not even said they could connect.

Any help is appreciated.
Thank you.

---

### Post by yoramdavid on 2013-05-16
I wonder... is it possible to do what I am trying to do or is it a myth?
Nobody can help?

---

