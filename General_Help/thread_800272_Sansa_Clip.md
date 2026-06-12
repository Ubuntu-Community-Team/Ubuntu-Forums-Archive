---
title: "Sansa Clip"
date: 2008-05-19
forum: General Help
---

### Post by sscfirst on 2008-05-19
Hi all,

I am having trouble mounting Sansa Clip 2 GB mp3 player. It connects via USB, and unlike with older versions, no icon is showing up on desktop. There were some suggestions of unplugging USB mouse to make ubuntu realize that there is another USB device, but that did not work either. I also tried lsusb, and I get the following output:

Bus 003 Device 026: ID 0781:7432 SanDisk Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000

Obviously, the Sansa Clip device is there connected to the USB, but it fails to put a  icon for it on the desktop, or mount it elsewhere that I know of.

I did get the icon on the desktop once, and was able to browse through the players files, however, I dont know why it worked that time, but I cannot get it to work anymore. The mp3 player is working since I can use it on other computers. I am wondering if anyone had any solutions for this other than the unplugging and plugging in the mouse, since that dosent seem to work..

Thanks
sscfirst

---

### Post by sscfirst on 2008-05-19
Something I forgot to add is that I searched mtp, and installed mtp-tools using synaptic since some forum said I should, but I dont think that has helped either.

Cheers
sscfirst.

---

### Post by aysiu on 2008-05-19
Maybe on the Sansa Clip itself make sure you're using the MSC mode instead of MTP or Auto-Detect?

I have a Sansa Clip and haven't had this problem, so it may, as you've considered, have something to do with other USB devices or some other configuration problem.

---

### Post by sscfirst on 2008-05-19
> **aysiu said:**
> Maybe on the Sansa Clip itself make sure you're using the MSC mode instead of MTP or Auto-Detect?


I cant find any option to choose between MTP, MSC or Auto-Detect? How do I go about doing that on the player. Also, if you could tell me what version number you have for your device under: Settings>System Info>Version.

IN the mean time, I am going to see if I can find a firmware upgrade for my Sansa Clip itself. Right now its on version V01.01.11A.

Thanks for the reply.

Cheers
sscfirst.

---

### Post by aysiu on 2008-05-19
I'm V01.01.18A

If you go to Settings > USB Mode, you can select MSC (instead of MTP or Auto-Detect).

---

### Post by sscfirst on 2008-05-19
I did a firmware upgrade, but still, with the USB mode changed to MSC or autodetect, it has not worked :(

Atleast for this reason, I got a firmware upgrade done, lol

Cheers
sscfirst.

---

### Post by aysiu on 2008-05-19
I know this sounds dumb, but have you tried a simple reboot (of Ubuntu, not the Sansa Clip)?

---

### Post by G@B0 on 2008-05-20
Well.  

So when it was connected I accidentaly pressed the center button and suddenly it was shown an icon on the desktop like a removable drive.

The USB mode is set on automatically and you just have to press the center button after connecting the device to the computer and it will suddenly appear as a removable drive.

Try this. I want to confirm if this works exactly as I say.

It was not even recognized on my laptop even on lsusb command but after pressing the center button it was recognized.

G@B0

---

### Post by drachenstern on 2008-05-21
Not mine, but I didn't install any particular libs.  Thoughts?

Obv I have the same problem as others, has anyone filed a bug-report?

---

### Post by G@B0 on 2008-05-21
Ok here is the correct procedure.
First, turn on the mp3 player(sansa clip),
go to Settings > USB Mode > and change Auto Detect to MSC

Now connect the device to the computer.
It will not show as a removable drive unless you run this command:
```
lsusb
```

After running that command on the terminal, wait 5 seconds and it will be shown in the desktop as a removable drive.

Hope this works for you

---

### Post by aysiu on 2008-05-21
If you create an empty file called *.is_audio_player* in the top-level directory of the Sansa Clip, you should be able to drag and drop songs to it through Rhythmbox.

---

### Post by G@B0 on 2008-05-21
Worked like a charm.

Thx

---

### Post by Enigmacat on 2008-11-05
I have tried everything. I have gone to the Settings section of my Sansa but I have not found a selection that allows me to change it to USB. I did install the mtp-tools and I can see the device when I run the lsusb command. What else do I need to do. Keep in mind that I have tried all of the things previously posted, well all the things that I could try, anyway.

---

### Post by Low-key Lyesmith on 2009-01-17
> **aysiu said:**
> If you create an empty file called *.is_audio_player* in the top-level directory of the Sansa Clip, you should be able to drag and drop songs to it through Rhythmbox.
How do you create such a file if you cannot see the device?
Thanks
ciao

---

### Post by aysiu on 2009-01-17
> **Low-key Lyesmith said:**
> How do you create such a file if you cannot see the device?
Thanks
ciao
Disconnect the Sansa from the computer.

Turn it on

In the settings, change the USB mode to MSC (instead of Auto or MTP)

Then plug it back into the computer

---

### Post by Low-key Lyesmith on 2009-01-24
Now I see the device: I think the trick is
update software as described
turn USB mode into MSC
enter in the terminal window and type lsusb
It would look as if it was not connected but you will then see the icon on the desktop.
Now with places I entered the device and created .is_audio_file directoy.
Anyway I cannot drag and drop from rithmbox
can anyone help?

ciao

---

### Post by mpiroc on 2009-12-06
I also had this problem, and was able to fix it by switching the mode to MSC.

I'm a little confused about this, though. I never had to change the mode before. As recently as the Karmic Beta I recall it working perfectly. Is a fix in the works?

---

### Post by psychosibes on 2010-01-14
Hi all,

my missus and i both have sansa clips and have had issues mounting them onto our Dell XPS M1330 and Dell Mini 9. We have changed the setting on the clip to MSC, followed the mounting instructions on the sansa website, but we rarely get them to mount successfully. typing lsusb in the terminal does not show the device.
What we have found, AND IT WORKS every time for us is to plug the clip into a USB port, and restart the computer. The clip charges and mounts successfully. Its not the most convenient way to mount, but at least it works. Hope this helps some of you at least.

---

### Post by naina on 2010-02-16
hye,
      i have the same problem changing USB mode to MSC mode cuz by g9 on settings i don't find such option! tell me what should i do????
thanks
naina

---

### Post by naina on 2010-02-20
> **sscfirst said:**
> Something I forgot to add is that I searched mtp, and installed mtp-tools using synaptic since some forum said I should, but I dont think that has helped either.

Cheers
sscfirst.
i was having the same problem but the thing i did, i just changed ma USB cable and it worked...probably it can help to solve your problem

---

### Post by lilkdub503 on 2010-04-02
I just bought a Sansa Clip+, and I have Karmic. I plug the device in, and it says it's charging/connecting, but never shows up in my computer. And it also doesn't charge all the way up, even though it's been charging for quite a while now (6+ hours.) Help me please!

Oh, and I already ran the ls command, and it doesn't show up.

---

### Post by yellowbean on 2010-04-06
I've got a new Sansa Clip that I'm sure was showing up fine the first time I plugged it in, but tonight (2nd time) it wasn't. lsusb showed the device fine. After reading this thread and switching to MSC mode, still nothing. I decided to try a logout/login and that did the trick. Seems that sometimes things just get into a bad state, I hate rebooting though so I'm glad the logout did the trick.

---

### Post by curioususer on 2010-06-12
Same problem.  In 9.10 my Sansa clip worked great.  Now with 10.04 it isn't recognized.  I changed the mode to MSC on the device itself.  lsusb doesn't even see it anymore.

---

### Post by playing_with_matches on 2010-06-14
This isn't just an issue with the Sansa Clip.  I have a Jensen MP3 player, and the same EXACT thing is happening, except I can't switch it to MTP mode.  

Problem never existed in Karmic, only in Lucid.  Any advice?

---

### Post by curioususer on 2010-06-14
Heh, wait for Maverick Meerkat to be released?

---

### Post by playing_with_matches on 2010-06-15
So, I fixed the problem for my MP3 player (yay!), and hopefully it'll work for the Sansa and your guys issue as well!

Apparently there's a bug in a library.  

What I did:

1. Remove package libmtp8 (installed on all Lucid Lynx by default) This may uninstall Rhythmbox-plugins as well, don't worry about it for now.

2.Goto [http://packages.ubuntu.com/karmic/libmtp8](http://packages.ubuntu.com/karmic/libmtp8) and install the old version of libmtp8

3. Reboot, and try it now.

4. I re-installed the rhythmbox-plugins but under Rhythmbox made sure to go under  Edit->Plugins and make sure that MTP Portable Players is disabled.  

This worked for me!

---

