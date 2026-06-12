---
title: "Hardy... sound stopped working"
date: 2008-06-01
forum: General Help
---

### Post by jbeiter on 2008-06-01
What is it with Ubuntu and sound spontaneously going FUBAR?

The new system I setup for my kids was working just fine.. they wanted to play windows games so I go to install virtual box. "apt-get install virtualbox"

It installs and and I reboot to get the drivers loaded okay... and x11 doesn't want to start. I go through xconfig and my card/driver is nowhere to be found and won't work like the initial install. I get by on the generic vesa driver but sound is gone.

I don't even have a sound device. Sound periodically goes screwy on my own system and I have to reload stuff, jump up and down, unplug stuff/plug it back in and sound starts working again. This has me stumped.. I tried reinstalling alsa, pulseaudio, removed virtualbox.. auplay -v just says "no sound cards detected.

I even tried installing a soundblaster card scavanged from another computer.. nothing.

I'm using an MSI motherboard w/nvida 6100. I'm at a loss guys. I'm very disappointed at how brittle Ubuntu seems to be. Makes me hesitant to try and adjust anything less the whole damn thing comes crashing down.

any help would be appreciated

---

### Post by jbeiter on 2008-06-02
shameless bump but I really don't want to reload from scratch. There must be a way to fix this, or Ubuntu is no better than Windows.

---

### Post by R3VAMP3D on 2008-06-02
I think the problem might be the kernel modules being installed (Ive noticed virtualbox-ose installs new kernel data/[images]?)

---

### Post by jbeiter on 2008-06-02
I did try removing virutalbox-ose but I noticed that there are still scripts in /etc/init.d.. I don't think it was a clean removal.

My video is screwed now too.. glx doesn't work. Is there a way to re-install the kernel stuff without reinstalling the entire system?

Thanks for the response.

---

### Post by R3VAMP3D on 2008-06-02
I don't know Ubuntu internally, but for the kernel you could try ```
sudo apt-get install linux-image-2.6.22-14-generic
``` What graphics chipset do you have?

---

### Post by jbeiter on 2008-06-03
root@cracker:~# sudo apt-get install linux-image-2.6.22-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-2.6.22-14-generic

I'm going to try and perhaps find it in synaptic..


the graphics is a GeForce 6100/nForce 405. Just my luck, searches for linux AMD64 drivers on Nvidia's website comes up with nothing. I tried installing an Nvidia driver for GeForce but that didn't work well.

Out of frustration, I tried reinstalling Ubuntu from scratch. The install CD gets to a point where it complains about having no "underlying authentication for user blah blah blah" and just sits there.

This is really bad. Can anyone tell me if I might hope for better luck with Ubuntu 7.10.. or perhaps even fedora 8?

---

### Post by R3VAMP3D on 2008-06-04
If you want my honest to <insert your form of omnipotent being here> opinion, Id say downgrade to Gutsy. Im still rather upset about beta software in a LTS release. My laptop had similar problems minus the graphics issues. One day sound just stopped working and that was it. I just grabbed my Gutsy CD's and went at it. Now its running better than it was with Hardy on it. So my opinion is yeah, if gutsy was stable for you, go for it man.

---

### Post by Master Chief on 2008-06-05
virtualbox installs new kernel modules, and you should have noticed two new lines in grub at startup with the text/identifier "server" instead of "general" in the description.

Start you computer with the third (?) general option and your sound will be back!

---

