---
title: "No sound please help"
date: 2020-11-03
forum: General Help
---

### Post by adricen on 2020-11-03
After installing Ubuntu 20.04.1 on a fresh install it seams that I don't have sound

I tryed to reinstall alsa and used pavucontrol but it don't do anything
Can anyone help me figure out a solution ?


Thanks

Adricen

---

### Post by HermanAB on 2020-11-04
Usually, all that you need to do it turn the volume up and toggle all available switches in pavucontrol, until you find the magical one.

---

### Post by adricen on 2020-11-04
I tried to install the last vesion of alsa firmware from the main site with no success...
[http://diffusionht.blogspot.com/2012/08/asus-p8z77-v-intel-audio-ubuntu-no-sound.html](http://diffusionht.blogspot.com/2012/08/asus-p8z77-v-intel-audio-ubuntu-no-sound.html)

Still digging

---

### Post by adricen on 2020-11-04
Hey @[**[COLOR=#000000]HermanAB[/COLOR]**]("https://ubuntuforums.org/member.php?u=44990"),

Thanks for taking car.
the thing is in pavucontrol I just have 1 audio output. It seams that it detect sound played by my web browser but nothing comes out of my board.

I have an Asus motherboard model P8Z77-V LK with back and front sound output and input.
pavucontrol doesn't detect any mic input also...

---

### Post by CelticWarrior on 2020-11-04
Some blog post from 8 years ago certainly isn't the solution. Is this even your hardware or just the first thing you googled?

---

### Post by adricen on 2020-11-04
I tryed this at first :
[https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/](https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/)

and then tryed : [URL="https://help.ubuntu.com/stable/ubuntu-help/sound-nosound.html.en"]https://help.ubuntu.com/stable/ubuntu-help/sound-nosound.html.en

[/URL]and at last reinstall alsa firmware (solution from 2012... which is old indeed)

---

### Post by HermanAB on 2020-11-04
Try running *alsamixer* and see what it says.

---

### Post by adricen on 2020-11-04
I setted everything at the maximum with no result...

Thanks

---

### Post by HermanAB on 2020-11-05
OK, the trouble is that GUI programs are cool when everything works, but they do not provide error messages.  To really figure out what is going wrong, you got to use the command line and then google the errors.

Here are a few more pointers:
The *lsmod* command will list all the device drivers.  You can load a new driver with *rmmod *and *insmod*.  With that, you can figure out whether you have the correct sound device driver loaded, kill it and restart it and look at the errors without having to reboot all the time.

With *alsamixer*, you can set the volume and toggle the switches.

With *sox*, you can generate a tone and try to hear it on the speaker.

Eventualy, some error message should give you a clue, which you can then google to drill down into the problem.

---

### Post by adricen on 2020-11-05
Thanks for those infos Herman,

I checked if indeed some things were wrong.
The thing is in alsamixer I can find Two audio card, the 0 is for HD intel PCH and 1 for HDA Nvidia which is I guess for HDMI output.
The thing is in my sound system settings I only have 1 choice of output which is Digital outpu (S/PDIF) - intern audio...

I then tryed to find something around HD Intel PCH and tryed this fix : [https://www.linuxuprising.com/2018/06/fix-no-sound-dummy-output-issue-in.html](https://www.linuxuprising.com/2018/06/fix-no-sound-dummy-output-issue-in.html)
with no success...

---

### Post by adricen on 2020-11-05
It seams that the front headphone plug is w<orking but not the one at the back...
So I have some sound after all but not everywhere... if I may

---

### Post by yaminb on 2020-11-05
Not sure if it's related, but I had some output device detection issues after upgrading to 20.10 from 20.04.

Generally speaking, if I do a 'pulseaudio -k' and wait like 10 seconds, it re-detects all output devices properly.

Also, I like to install this: [https://extensions.gnome.org/extension/906/sound-output-device-chooser/](https://extensions.gnome.org/extension/906/sound-output-device-chooser/) to make sure my audio output is set properly.

---

### Post by HermanAB on 2020-11-05
This is a desktop computer?  Check whether the plate with connectors at the back is actually connected to the MB.  It may just be a dummy.

---

### Post by istvan5 on 2020-11-05
My experiences.

I had problems with the Audio too, but I solved so far.

After boot / reboot Ubuntu, I was not predictable if I will have a sound or its a "dummy output" (means: no sound) under the Pulse Audio Radiobutton in the Volume settings.
I tried to change
/etc/default/grub
/etc/modules
sudo systemctl status systemd-modules-load.service
sudo systemctl restart systemd-modules-load.service
and so and so

Nothing really worked. Once, after plug out the audio connector, the sound come back. I found the problem.

I can select the output device with **pavucontrol** (i my case pavucontrol-qt.
There, under "Input Devices", I had to activate "Profile" checkbox, 
there is a list of unavailable and available outputs ( I see always 1 / 2 / 3 working output devices)
(I use a notebook in a docking station, and 2 displays)
immediately after changing the device there, the sound works, the device in the Volume Control menü switch from "dummy output" to the name of the device.
I am not sure, can be it will block each other if the Volume Menu Window is opened, I had a problem, so I
switch off the Volume Menu Windows before I do anything in Pavucontrol. 
When I shut down and boot Ubuntu, It can be that the sound switch from one device to another, maybe again dummy output (I still dont know why Ubuntu switch),
but I can correct the problem in pavucontrol without logoff or reboot.

Ubuntu 20.04.1 LTS (Focal Fossa) 
Audio:   Intel Cannon Lake PCH cAVS vendor: CLEVO/KAPOK driver: snd_hda_intel

---

### Post by istvan5 on 2020-11-05
cool, this here [https://askubuntu.com/questions/1114750/how-can-i-enforce-an-audio-profile](https://askubuntu.com/questions/1114750/how-can-i-enforce-an-audio-profile)
will hopefully help me to solve the "Pulse Audio" switch automatically problem. I will try to change /[COLOR=#DAD7D2][FONT=Consolas]etc/pulse/default.pa[/FONT][/COLOR]

---

### Post by badazdz on 2020-11-05
I have updated to ubuntu 20.10 and sound is also not working for me.
However here is a workaround which works [https://www.kubuntuforums.net/showthread.php/76776-Greeting-Groovy-Gorilla-Kubuntu-20-10?p=441199&viewfull=1#post441199](https://www.kubuntuforums.net/showthread.php/76776-Greeting-Groovy-Gorilla-Kubuntu-20-10?p=441199&viewfull=1#post441199)

---

