---
title: "Can't output sound via HDMI"
date: 2014-09-14
forum: General Help
---

### Post by someone2352 on 2014-09-14
Hi,
When I'm connected to HDMI, I can't see the TV in the output sound devices.
Anyone knows how to fix it? I've already tried to upgrade my kernel and it hasn't help.

---

### Post by dave131 on 2014-09-14
Are you using an AMD video adapter or an AMD processor withe the built-in gpu?

---

### Post by someone2352 on 2014-09-14
Not that I'm aware of. How can I check it?

---

### Post by dave131 on 2014-09-14
Open a terminal window via  ctrl/alt/t

type:

lspci | grep VGA

Post the line that is output back here in a reply.

---

### Post by someone2352 on 2014-09-14
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)

---

### Post by dave131 on 2014-09-14
Sorry - I don't about the problem with the Intel GPU's - I just have a personal experience with that problem and AMD only.

I hope someone comes along that can help you.

---

### Post by dave131 on 2014-09-14
I did find this thread - it's for the previous release though so I don't know if it applies to 14.xx or not.

[http://askubuntu.com/questions/285624/ubuntu-13-04-not-detect-the-hdmi-sound-output](http://askubuntu.com/questions/285624/ubuntu-13-04-not-detect-the-hdmi-sound-output)

I haven't done what is in that thread or I would have posted instructions here.  I hope it can be of some help.  Please post back with any questions, problems, results, etc..

---

### Post by nerdtron on 2014-09-14
In the sound settings, you can choose which device to output sound from. Maybe the chosen device is the internal sound card. Try changing it to HDMI to direct the sound in the HDMI output.

---

### Post by sammiev on 2014-09-14
> **nerdtron said:**
> In the sound settings, you can choose which device to output sound from. Maybe the chosen device is the internal sound card. Try changing it to HDMI to direct the sound in the HDMI output.

+1 - I need to do this each time I move my laptop from device to device.

---

### Post by someone2352 on 2014-09-14
> **dave131 said:**
> I did find this thread - it's for the previous release though so I don't know if it applies to 14.xx or not.

[http://askubuntu.com/questions/285624/ubuntu-13-04-not-detect-the-hdmi-sound-output](http://askubuntu.com/questions/285624/ubuntu-13-04-not-detect-the-hdmi-sound-output)

I haven't done what is in that thread or I would have posted instructions here.  I hope it can be of some help.  Please post back with any questions, problems, results, etc..
I already tried their suggestions, and it didn't help.


> **nerdtron said:**
> In the sound settings, you can choose which  device to output sound from. Maybe the chosen device is the internal  sound card. Try changing it to HDMI to direct the sound in the HDMI  output.


I don't have the HDMI output in the sound settings. That is the whole point.

---

### Post by sammiev on 2014-09-14
Do you have the output turned on in your Bois?
I hook up my HDMI output before I boot my Laptop.

---

### Post by someone2352 on 2014-09-14
> **sammiev said:**
> Do you have the output turned on in your Bois?
I hook up my HDMI output before I boot my Laptop.

How do I check this?

---

### Post by sammiev on 2014-09-14
On my laptop I press F2 on boot to enter into my bios. Then I have external display on auto-detect.

---

### Post by someone2352 on 2014-09-14
> **sammiev said:**
> On my laptop I press F2 on boot to enter into my bios. Then I have external display on auto-detect.

Not display. I'm talking about sound.

---

### Post by dave131 on 2014-09-15
I've also been searching but so far haven't found a similar option for Intel, but for my AMD processor I had the exact same problem - video but no sound via HDMI and no HDMI sound option on the selection screen.  I searched around a lot and stumbled on to an option (I *think* it was a boot option) of radeon-sound=1 or something like that (I don't have that system anymore).  I've been searching for an option of something like intel-sound=1 or snd-intel-hdmi=1 - things like that, but I haven't found anything yet.  I'll keep searching but no promises I'll find something like that.

---

### Post by dave131 on 2014-09-15
I did find something that may be helpful. it was in [this]("http://ubuntuforums.org/showthread.php?t=2091459") thread.  It is for 12.04, but it may be what you need:

> I had the same problem when first using HDMI. 
[INDENT] Got video but no audio. I solved it by installing Pulse Audio Volume Control which gave me the HDMI audio options needed. 				
[/INDENT]

---

### Post by pqwoerituytrueiwoq on 2014-09-15
are you looking in the right place of the sound settings
run/open [FONT=courier new]pavucontrol[/FONT] (volume icon -> sound settings)
go to the configuration tab (the last one)
change it to something with hdmi that looks appropriate
go to the output devices tab (3ed on from the left)
make sure it is not muted or anything like that
check the payback tab for your application, ensure it is using the audio device you selected earlier
when you are done with hdmi you will need to switch back to analog output

---

### Post by dave131 on 2014-09-15
Perhaps you should post the output of the following:

(open a terminal window - ctrl/alt/t)

aplay -l <press enter>

Post the output back in a reply surrounded by the code tags.  See if you see a HDMI sound device listed there.

In the same reply, post back the output of the following surrounded by code tags:

lspci -v | grep -A7 -i "audio" <press enter>
[COLOR=#0000ff][I]
EDIT:  Perhaps a little explanation is in order for the above statement:

lspci itself will list all the devices on the computers PCI bus. the "-v" option as shown means "verbose", so it shows more information for each device.

The "|" directs the output to the next command - in this case "grep".

I don't know what else grep might be able to do, but I use it for searching for a string. The above uses 2 options:
-A7 means to list 7 lines after the text is found
-i means ignore case

The "audio" is the string to match to. 

So the statement says to give an extended list (7 lines) of the pci devices that have the word audio in them, regardless of the case or mix of case in the word audio.

[/I][/COLOR]

---

