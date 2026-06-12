---
title: "Headphones no sound (speakers work)"
date: 2022-09-07
forum: General Help
---

### Post by Datoyminaytah on 2022-09-07
Yet another sound problem question. I'll try to post as much as I know.

Acer Chromebook 317
Can dual-boot between ChromeOS and Lubuntu (and a few other linux OSs on thumb drives)
Speakers working in Lubuntu, largely from booting ChromeOS and inspecting/copying files to Lubuntu (mainly asound.state and /etc/modprobe.d files related to alsa, blacklisting some modules etc.)

But headphones... In Lubuntu, when I plug them in, sound continues to be played from the speakers, and there is no sound from the headphones.

alsamixer in both ChromeOS and Lubuntu shows card as sof-rt5682, chip Intel Jasperlake HDMI, and has these items (among others that look the same on both)

Headphone Jack
HPOL
HPOR
Left Spk
Right Spk

On ChromeOS, when I plug in headphones, it mutes Left Spk/Right Spk, and unmutes Headphone Jack, HPOL, and HPOR. Vice-versa when I disconnect them.

On Lubuntu, it does not. And, if I mute/unmute them myself, still no headphones sound (although muting speakers works.) Also unmuting everything possible and bumping up db on any faders that were at 0.

The only sound I get from the headphones, is if I toggle HPO Signal Demux between OneBit and Legacy, there is a click.

On Lubuntu, acpi_listen shows

jack/headphone HEADPHONE plug
jack/headphone HEADPHONE unplug

...when I connect and disconnect headphones. So it's detecting the plug!

I am at a loss. The only other difference I have seen is:

Diffing /proc/asound/card0/codec#2 between ChromeOS and Lubuntu shows one repeated difference, for 5 nodes, 0x04, 0x06, 0x08, 0x0a, and 0x0b, all "Pin Complex"...

  In-driver Connection: 4
     0x03 0x05 0x07 0x09

Hmm, 5 Pin Complex In-Driver connections, 5 items in alsamixer... could this be related or a red herring? But I have no idea how to work backward from info in /proc to find where it's configured.

I do know the nodes are the same as shown in:

/sys/class/sound/hwC0D2/init_pin_configs

0x04 0x18560010
0x06 0x18560010
0x08 0x18560010
0x0a 0x18560010
0x0b 0x18560010

(same on both ChromeOS and Lubuntu)

I've taken a look at hdajackretask. It shows those same 5 pin ids but I have no idea what to set here. If I override one I can only choose HDMI/DisplayPort or Not Connected, unless I click Advanced override, but here I have no idea what to set. (And hung my machine the one time I tried.)

Any ideas?

---

