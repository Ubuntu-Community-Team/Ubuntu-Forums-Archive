---
title: "My Solution: Hardy 8.04 and Bluetooth headsets"
date: 2008-05-08
forum: General Help
---

### Post by psyke777 on 2008-05-08
Notes: These instructions work for 32-bit Ubuntu. (64-bit needs more work by someone with a 64-bit system. See the 4th post below this.)

1) make sure linux-ubuntu-modules-(kernel version)-generic, bluetooth, bluez-audio, bluez-gnome and bluez-utils are installed
2) uninstall or do not install bluetooth-alsa or bluez-btsco

3) Make sure your bluetooth hub is plugged in and working
$ **hciconfig -a**
```

hci0:   Type: USB
        BD Address: 11:11:11:11:11:11 ACL MTU: 678:8 SCO MTU: 48:10
        UP RUNNING PSCAN
        RX bytes:3935493 acl:271 sco:76851 events:660 errors:0
        TX bytes:3437929 acl:264 sco:67270 commands:223 errors:0
        Features: 0xbf 0xfe 0x8d 0x78 0x08 0x18 0x00 0x00
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
        Link policy: RSWITCH HOLD SNIFF PARK
        Link mode: SLAVE ACCEPT
        Name: 'dell-0'
        Class: 0x08010c
        Service Classes: Capturing
        Device Class: Computer, Laptop
        HCI Ver: 1.2 (0x2) HCI Rev: 0x1fe LMP Ver: 1.2 (0x2) LMP Subver: 0x1fe
        Manufacturer: Integrated System Solution Corp. (57)

```
4) discover your headset address by putting the headset in discoverable mode then using the command:
$ **sudo hcitool scan**
```

Scanning ...
        xx:xx:xx:xx:xx:xx       BT Headset-F

```
5) Add .asoundrc file to your home directory
6) In it put:
```

pcm.bluetooth {
  type bluetooth
  device xx:xx:xx:xx:xx:xx
  profile "auto"
}

```
where xx:xx:xx:xx:xx:xx is the address of your head set above.


7) enable bluetooth sound on bluetooth hub
$ **sudo hciconfig hci0 voice 0x0060**

8) Check bluetooth Audio service is running
right click the bluetooth icon in your Notification Area 
click Preferences / Services Tab
make sure Audio service is running
close it

9) load bluetooth SCO drivers
$ **sudo modprobe snd_bt_sco**
$ **sudo modprobe sco**
You might want to put these in /etc/modules

10) turn on the headset and hit volume up on the headset which should cause your PC to ask for the passkey to pair with the headset

11) check bluetooth sees the head set and has realised it is for audio
right click the bluetooth icon in your Notification Area
click Preferences / Services Tab
select 'Audio service' and your headset should be listed below

12) Check bluetooth headset is seen by ALSA
$ **sudo cat /proc/asound/cards**
```

 0 [I82801CAICH3   ]: ICH - Intel 82801CA-ICH3
                      Intel 82801CA-ICH3 with CS4205 at irq 5
 1 [Headset        ]: Bluetooth SCO - BT Headset
                      BT Headset 1

```
13) adjust volumes for headset
$ **alsamixer -c1**
where 1 means card 1 listed above. Yours may be different.

14) Testing
$ **arecord -D bluetooth -f s16_LE test.wav**
talk for 10 seconds into the headset then press ctrl-C (note it might take a few seconds to start recording)
$ **aplay -D bluetooth -f S16_LE test.wav**
Playing WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 8000 Hz, Mono

15) in your software such as skype choose the device called 'bluetooth' which is the pcm.bluetooth name used in .asoundrc

I still have problems sometimes... bad recordings, error messages in the logs etc. But it works. Perhaps someone can add this in a more accessable place once it has been verified that it works. Some of my steps may be superfluous but I wanted to get the info out there.

It might be neccessary sometimes to remove the headset from the Bluetooth Manager and have it re-add itself by pressing Volume up.

---

### Post by Permafrost91 on 2008-05-09
This works! Unfortunately, Ekiga still can't use my device. It finds it but says it can't read/write to the device.

---

### Post by psyke777 on 2008-05-09
> **Permafrost91 said:**
> This works! Unfortunately, Ekiga still can't use my device. It finds it but says it can't read/write to the device.

This might help?

[https://bugs.launchpad.net/ubuntu/+source/ekiga/+bug/178555](https://bugs.launchpad.net/ubuntu/+source/ekiga/+bug/178555)

---

### Post by mhnagaoka on 2008-05-10
Works for me on Skype. Thanks a lot! I've been struggling with this for quite some time.

---

### Post by pangloss on 2008-05-10
Even following these instructions, Skype audio with my bluetooth headset doesn't work:

```
ALSA lib ../../../src/pcm/pcm_params.c:2135:(snd_pcm_hw_refine_slave) Slave PCM not usable
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
```

I assume this is because I am running 32-bit Skype on Hardy 64-bit.

Searching packages.ubuntu.com for libasound_module_pcm_bluetooth.so returned bluez-audio. I grabbed the deb for i386 and copied libasound_module_pcm_bluetooth.so to /usr/lib32/alsa-lib/ and now audio works-sort of. The sound quality is poor: crackling and static. I also still see the following output:
```
ALSA lib ../../../src/pcm/pcm_params.c:2135:(snd_pcm_hw_refine_slave) Slave PCM not usable
ALSA lib ../../../src/pcm/pcm_params.c:2135:(snd_pcm_hw_refine_slave) Slave PCM not usable
```

I think it's quite a shame that there are so many hurdles to getting a bluetooth headset & Skype to work with Ubuntu. Any suggestions on getting Bluetooth headset + Skype + Ubuntu 8.05 amd64 working better?

---

### Post by gattopi on 2008-05-10
Thanks the Blue Audio is go..
But Skype have error: Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so

Help me Bye

---

### Post by psyke777 on 2008-05-11
> **gattopi said:**
> Thanks the Blue Audio is go..
But Skype have error: Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so

Help me Bye

I will assume you are using 64-bit. See the post above yours. I use 32-bit and so I cannot help you.

---

### Post by gattopi on 2008-05-11
Yes I use Ubuntu 64..
Only skype is not works](*,)

---

### Post by damis648 on 2008-05-11
I think it is much simpler to go into Bluez preferences and then click the services tab, enable audio service and click add at the bottom? Maybe just me...

---

### Post by Gizmonty on 2008-05-12
It seems like far more work than it should be but it works and I am very grateful. Thankyou.

---

### Post by ghuqu on 2008-05-13
Alright I did as instructed and so far so good until I tested it. When I input $ arecord -D bluetooth -f s16_LE test.wav 
I received this; Recording WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 8000 Hz, Mono
Warning: rate is not accurate (requested = 8000Hz, got = 16000Hz)
         please, try the plug plugin (-Dplug:bluetooth)

What does this mean?

---

### Post by mhnagaoka on 2008-05-14
> **damis648 said:**
> I think it is much simpler to go into Bluez preferences and then click the services tab, enable audio service and click add at the bottom? Maybe just me...

Yeah, I think you're right. At least it worked for me without loading the kernel modules, etc. But if I don't do all the steps, I can't see the BT device on the mixer screen.

---

### Post by tarekeldeeb on 2008-05-16
Hello,

Is the OPPOSITE scenario possible?
Making Ubuntu act as a headset for my nokia ? I want to make my phone calls while not holding my mobile cell nor leaving my laptop ..

Is it possible?

---

### Post by imagia on 2008-05-17
Thanks for this. I can at last get the Bluetooth option in Skype, but I can't get any input or output working. Still, closer than before!

---

### Post by kepreon on 2008-05-17
I got my Plantronics Voyager 510 to work fine with Skype 2 beta under Ubuntu Hardy x64.  Thanks to psyke777 and pangloss -- I, however, did not have the problems that pangloss had with the 32 bit libraries.  I copied in the shared libraries like they said, but I don't get the same error message.  I get:

ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL bluetooth

Both audio in and audio out work fine despite the error, however, using the pcm device created in .asoundrc, so no complaints here.

---

### Post by priegog on 2008-05-17
Wow, this seems unnecesarily complicated. Since Feisty (I think) I've been able to do this graphically with an application called [Blueman.]("http://blueman.tuxfamily.org/") There was also another app one member from these forums wrote JUST for headsets for which I can't remember the name, since I replaced it with blueman, but it existed. Just checked his site but he recently changed it so the page is broken. So all of you go check these out.

---

### Post by wieman01 on 2008-05-17
Worked like a charm. You are my hero! Recording quality isn't the best, but so be it! Big thank you!

---

### Post by Permafrost91 on 2008-05-17
prigog: are you referring to gbtsco? None of the sco tools work with Hardy because the whole bluetooth framework has apparently been changed (I've tried and someone else had also mentioned to not use gbtsco et al.). It seems that the solution presented in this thread works for Skype but not for Gnome in general. I'm assuming the problem actually lies with PulseAudio and not the bluetooth implementation itself.

---

### Post by priegog on 2008-05-17
> **Permafrost91 said:**
> prigog: are you referring to gbtsco? None of the sco tools work with Hardy because the whole bluetooth framework has apparently been changed (I've tried and someone else had also mentioned to not use gbtsco et al.). It seems that the solution presented in this thread works for Skype but not for Gnome in general. I'm assuming the problem actually lies with PulseAudio and not the bluetooth implementation itself.

Yes, it was gtbsco. Hmm, that's odd that blueman stil works for me then. Maybe I did some tweaking that resided in my home folder and so it got preserved tru the upgrade? Anyways I can still skype and also listen to stereo music with amarok (taht one requires a bit more config). I found the original thread where we sorted this stuff out, [check it out.]("http://ubuntuforums.org/showpost.php?p=3794607&postcount=11") It's tailored to make stereo bluetooth work, but it made the skype bluetooth entry permanent as a nice secondary effect. Worth a shot in my opinion.

---

### Post by Permafrost91 on 2008-05-17
thanks priegog! I've done that but Ekiga still doesn't want to work (which is what I really meant by "Gnome in general" earlier). I don't use my BT headset for anything else so I guess I'm stuck for now until Ekiga recognizes PulseAudio ...

---

### Post by yadayada2 on 2008-05-17
Hi, 

I don't know what I'm doing wrong. I followed the instructions from the first post. I also did in combination with blueman. So, I can connect the headset. It's listed as device under audio services. Even in ALSA and skype it is recognized.

Anyway, I don't get any sound from or to the headphone. Not even with the commands from the first post (arecord and so on).

I am using Hardy 8.04 on a 64 bit base.

Please help me.

---

### Post by imagia on 2008-05-18
Well, a little bit further along now. Using Blueman I can get Skype to give me audio output, but it won't accept input. When I try to add audio input service for my headset in Blueman, it tells me that's not supported. A blatant lie because it works in Vista!

---

### Post by harperd on 2008-05-18
Just joining the thread. I followed the instructions and Skype just hangs in the options menu when I select audio. When I delete/rename asoundrc, Skype comes back again. Using Zaapa ZA-BT06A1 headset


Contents of asoundrc

pcm.bluetooth {
 type bluetooth
 device 00:11:B1:09:96:AC
 profile "auto"
}

The device ID is correct

Thanks

---

### Post by harperd on 2008-05-18
Seems I spoke too soon. My device ID was not correct. I installed Blueman - looks usefull. I set Skype audio options to bluetooth and sound in works intermittently - the device keeps disconnecting.

---

### Post by sinnerou on 2008-05-21
This is pretty much what I did to get my plantronics 590 headset working but it interferes with my bluetooth mouse anyone know a fix? (floating mouse, sound stops etc)

Thanks

---

### Post by pbhill on 2008-05-21
I'm beginning to see why Bill Gates is so wealthy...
I would *pay* right now to get Bluetooth to work in Ubuntu!

---

### Post by hihihi on 2008-05-24
i would pay to, hahaha,
but luckily i am not married nor have a girl-friend and i can take my time to get to understand how bluetooth works in linux.
and thanks to all those who write their solutions and how tos,
thanks,
it is kind of working,
xubuntu 8.04 64bit on sony vaio fz31m, BT-headset: Iqua BHS-603

THX

---

### Post by priegog on 2008-05-24
to all of you who have been complaining about my solution involving blueman and that other file that goes in /home... You're right, I can't get skype to work with it either now that I'm on Hardy. Maybe we could solve this in this thread?

---

### Post by blom on 2008-05-26
Yeah, everything worked fine for me in Gutsy - didn't even have to do much to get it going.... Nothing works since the upgrade though, very frustrating as I had jut finished mouthing off to a windows user who had loads of difficulty with BT and XP...
I can certainly see the device when it's in pairing mode, it just wont pair (using the GUI's)

[edit]  Well, I've made some progress, turns out this was partly my fault.  I'd disabled the bluetooth-manager as a startup program (in "Sessions"), and starting it manually doesn't seem to be very useful.

So now no software complains and I appear to have a successful pairing, but I can only hear stuff, when I record into the mic I just get noise out the other end... Looking at that seperately

---

### Post by GerryLight on 2008-05-29
> **sinnerou said:**
> This is pretty much what I did to get my plantronics 590 headset working but it interferes with my bluetooth mouse anyone know a fix? (floating mouse, sound stops etc)

Thanks

I have a Plantronics 590E in combination with an Apple Mighty Mouse and had stuttering sound, too, when the mouse was switched on. I solved this by changing two items in my /etc/bluetooth/hcid.conf: line "lm accept" into "lm master" and removed the entry "rswitch" in the line "lp ..." (link policy). Have a look at my complete hcid.conf [http://ubuntuusers.de/paste/226656/]("http://ubuntuusers.de/paste/226656/") in the german ubuntu forum. Good Luck!

---

### Post by ian.d.rossi on 2008-05-30
Thank you so much for this. I love Hardy and it's the best distro ever. The only thing (critical thing) I couldn't do was use Skype. I use it for all of my business calling. Being able to use my BT headset solved the problem. I also would like to see this process made easier by the Ubuntu team.

Thanks again.

-Ian

---

### Post by secr3tuprising on 2008-06-03
I just spent a few minutes tweaking the FossWire script for connecting bluetooth headphones and it should help people out who are having some issues. 
It is specifically for Ubuntu Hardy Heron 8.04 LTS 64bit.

After extracting run
```
sh bluetooth_skype_ubuntu64bit.sh
```
and all the 32bit libraries for skype will be downloaded and installed and will also pair your headset automatically with a python script.

This also fixes the libasound_module_pcm_bluetooth.so issue by copying that file to the correct directory

---

### Post by bin-da on 2008-06-05
I've followed your instructions (removed bluetooth-alsa, etc.) but I cannot use Skype and so on. headset is paired with my computer. it seems that connection is OK - when I try to make a call, it beeps and i hear noise but it doesn't work - Skype tells me that there are problems with my audio.
I also tried aplay / arecord - always get the same error:

```
ALSA lib pcm_bluetooth.c:460:(bluetooth_hsp_hw_params) BT_SETCONFIGURATION failed : Input/output error(5) 
```

any ideas?

---

### Post by BigPingu on 2008-06-08
Thanks a lot for your script secr3tuprising.
It works great :-)

Bye
BigPingu

---

### Post by Zer0Nin3r on 2008-06-09
> **psyke777 said:**
> 2) uninstall or do not install bluetooth-alsa or bluez-btsco

Why don't you want bluetooh-alsa or bluez-btsco installed?  Do those two packages not function properly, or do they need more development?

---

### Post by raymondvillain on 2008-06-09
I would like to try the solution posted by psyke777 4 weeks ago.

If I open a terminal and type hciconfig -a hci0 the machine tells me

"Can't get device info:  no such device"

I have bluetooth, bluez-audio, bluez-gnome and bluez-utils installed.  Neither bluetooth-alsa nor bluez-btsco are installed.

I did install blueman but it doen't do a thing.

Any suggestions?

---

### Post by sravi_in on 2008-06-10
I followed the instructions above to setup skype and music player correctly. But the issue is now only one application is able to use bluetooth device exclusively.

So if I am listening to music in amarok, i won't be able to open kaffine or i will miss incoming skype call. Kaffine says the device is busy and cannot use it. Skype says failure to caputre audio.

Is there any solution for this?

---

### Post by secr3tuprising on 2008-06-11
> **Zer0Nin3r said:**
> Why don't you want bluetooh-alsa or bluez-btsco installed?  Do those two packages not function properly, or do they need more development?

bluetooth-alsa comes with Hardy 8.04 by default, as well as all the other bluez-utils and whatnot 

> **sravi_in said:**
> I followed the instructions above to setup skype and music player correctly. But the issue is now only one application is able to use bluetooth device exclusively.

So if I am listening to music in amarok, i won't be able to open kaffine or i will miss incoming skype call. Kaffine says the device is busy and cannot use it. Skype says failure to caputre audio.

Is there any solution for this?

As far as I know, you can only have one configured at a time.. I know it sucks, but we're definitely making progress.. I got around this by having 2 different bluetooth devices which i connect and configure separately.

---

### Post by g3k on 2008-06-11
I have followed the directions several times, have gotten the headset to pair and even beep when I begin to do a test record so I know there is a connection.

However it does not record anything and when I try to play something back through the headset the capslock and scroll lock lights on my keyboard begin to blink and I am unable to input anything from mouse or keyboard and must force the laptop to power down.

This happens both within Skype and other programs.

I am using a Targus USB dongle (MBT-1203) and a LG HBM-750 Headset.

Are either of these not compatible with sound on Ubuntu or am I not doing something correctly?

---

### Post by TechnoChick on 2008-06-12
I spent way too much time getting my bluetooth headphones to work on Ubuntu 7.10. Thanks to this thread I was finally successful. I used blueman 0.3 and a variant of the .asoundrc file. :)

For other reasons I upgraded to Ubuntu 8.04. The upgrade went smoothly, and I could still get my headphones to "connect", but Rhythmbox always sent its audio to my speakers, not my headphones. :(

I upgraded to blueman 0.5 (see [http://blueman.tuxfamily.org](http://blueman.tuxfamily.org) and select "downloads" for apt-get instructions). Unfortunately that didn't fix my problem.

Then I found [http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices). This site describes how to direct the audio output of each of the popular players.

For example, to send the Rhythmbox output to the bluetooth headphones:

gconftool -t string -s /system/gstreamer/0.10/default/musicaudiosink "alsasink device=bluetooth"

To send it to the speakers:

gconftool -t string -s /system/gstreamer/0.10/default/musicaudiosink "autoaudiosink"

These commands are pretty cryptic so I made a couple of scripts.

Under 7.10 I didn't have to do this. By using this .asoundrc:

pcm.!default {
  type bluetooth
}

my system would autodetect whether or not my headphones were connected and choose between the speakers and headphones accordingly. Now I have to explicitly execute the desired script before cranking up Rhythmbox.

I'm now using this .asoundrc:

pcm.bluetooth {
  type bluetooth
  device XX:XX:XX:XX:XX:XX
}

I'm too tired to determine which .asoundrc is best. But I'm happy to report my headphones are working!  :lol:

Hope this will prove helpful.

---

### Post by secr3tuprising on 2008-06-15
> **TechnoChick said:**
> 
For other reasons I upgraded to Ubuntu 8.04. The upgrade went smoothly, and I could still get my headphones to "connect", but Rhythmbox always sent its audio to my speakers, not my headphones. :(

Then I found [http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices). This site describes how to direct the audio output of each of the popular players.

There's a site that made this really easy,
[http://fosswire.com/2008/01/11/a2dp-stereo-linux/](http://fosswire.com/2008/01/11/a2dp-stereo-linux/)
the scripts are already there if you don't want to re-create them

---

### Post by benpage26 on 2008-06-15
I followed the steps up to the part where you say to press the volume key to make the device pair.

I cannot get my device to pair at all, no matter what i have tried.
I am using a 'Jawbone' There is no volume key, but i set it into pairing mode, and it will show up on gnome's bluetooth applet, when i click connect an OBEX error occurs
```
Couldn't display "obex://[00:0D:3C:6B:75:3C]/".
Error: Host down
Please select another viewer and try again.

```

I have installed "gnome-vfs-obexftp" as suggested in some places, but it has not helped, can anyone help me to pair my device?

---

### Post by nathan.devuono on 2008-06-18
I followed your walkthrough in 8.04 x64 and it worked perfectly! Kudos!

---

### Post by cutl4ss on 2008-06-18
Hello

My headset works with your Howto, at least with programs that use alsa...
But it didn't work with Teamspeak (that uses oss), did anonye a solution to use teamspeak with a bluetooth headset in hardy?

Greetz

(sorry for my bad english...)

---

### Post by Cain67 on 2008-06-18
hello there.

iv just purchases icombi bluetooth headphones with built in mic.
however, when i check under bluetooth setting, they only appeared under input, but not in audio.

it all seemed to work, up untill the following:

> 
 a builtrecord -D bluetooth -f s16_LE test.wav
ALSA lib pcm_bluetooth.c:1553:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
arecord: main:546: audio open error: Input/output error


if there is anyone that can help it would be muchly appreciated.

was i supposed to create the .asoundrc?
but yes, please help!!!!

PLEASE!!!
thanks

---

### Post by Cain67 on 2008-06-18
hello there.

iv just purchases icombi bluetooth headphones with built in mic.
however, when i check under bluetooth setting, they only appeared under input, but not in audio.

it all seemed to work, up untill the following:


> a builtrecord -D bluetooth -f s16_LE test.wav
ALSA lib pcm_bluetooth.c:1553bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
arecord: main:546: audio open error: Input/output error
if there is anyone that can help it would be muchly appreciated.


was i supposed to create the .asoundrc?
but yes, please help!!!!

PLEASE!!!
thanks

---

### Post by blackdalek on 2008-06-19
I can get as far as this step...
> 10) turn on the headset and hit volume up on the headset which should cause your PC to ask for the passkey to pair with the headset

Then I can't work out how to turn on the headset and the PC does not ask for any passkey.
I am using a BTune bluetooth headset. I can put it into discoverable mode... and the little light flashes, and the bluetooth dongle plugged into the computer can "see" it, but I have no idea how to turn the thing on. The only buttons on the headset are A phone logo, A "play/pause" symbol, a "next/previous track" button and a "volume up/down" button.
The instructions for the headset are not helpful don't offer any suggestions for turning them on.
I have no idea who the manufacturer is for these headphones. The thing looks like this [http://www.gtmall.com.au/catalogue/btune-bluetooth-headphones-p-483.html](http://www.gtmall.com.au/catalogue/btune-bluetooth-headphones-p-483.html)
I can't find the manufacturer's website.
If anyone else has one and knows how to make it turn on, I would be very grateful.

---

### Post by philidox on 2008-06-20
> **blackdalek said:**
> I can get as far as this step...

Then I can't work out how to turn on the headset and the PC does not ask for any passkey.
I am using a BTune bluetooth headset. I can put it into discoverable mode... and the little light flashes, and the bluetooth dongle plugged into the computer can "see" it, but I have no idea how to turn the thing on. The only buttons on the headset are A phone logo, A "play/pause" symbol, a "next/previous track" button and a "volume up/down" button.
The instructions for the headset are not helpful don't offer any suggestions for turning them on.
I have no idea who the manufacturer is for these headphones. The thing looks like this [http://www.gtmall.com.au/catalogue/btune-bluetooth-headphones-p-483.html](http://www.gtmall.com.au/catalogue/btune-bluetooth-headphones-p-483.html)
I can't find the manufacturer's website.
If anyone else has one and knows how to make it turn on, I would be very grateful.

Great instructions but I'm am having the same exact issue as I have quoted please help

---

### Post by blackdalek on 2008-06-24
> **blackdalek said:**
> I can get as far as this step...

Then I can't work out how to turn on the headset and the PC does not ask for any passkey.
I am using a BTune bluetooth headset. I can put it into discoverable mode... and the little light flashes, and the bluetooth dongle plugged into the computer can "see" it, but I have no idea how to turn the thing on. The only buttons on the headset are A phone logo, A "play/pause" symbol, a "next/previous track" button and a "volume up/down" button.
The instructions for the headset are not helpful don't offer any suggestions for turning them on.
I have no idea who the manufacturer is for these headphones. The thing looks like this [http://www.gtmall.com.au/catalogue/btune-bluetooth-headphones-p-483.html](http://www.gtmall.com.au/catalogue/btune-bluetooth-headphones-p-483.html)
I can't find the manufacturer's website.
If anyone else has one and knows how to make it turn on, I would be very grateful.

I've since tested these headphones on Windows and Mac and even though they ask for a passkey and pair with the device successfully, they do not work despite the claim on the packaging that they can be paired with any bluetooth device. I can only get these headphones to work with mobile phones, so I have given up trying to use them with a PC. They just generate an error on the Mac everytime the Mac tries to send sound to them.
I have instead chosen to go the dongle route and purchased the type with the dongle that plugs into the headphones out socket. Simple and it works.

---

### Post by waldeck on 2008-06-30
> **gattopi said:**
> Yes I use Ubuntu 64..
Only skype is not works](*,)

Hi gattopi,

Unless you have a particular reason to use the 64-bit version of Ubuntu, I would recommend going back to the 32-bit version, even if you have 64-bit processor. I don't think this sould create any noticeable performance issues and it should be compatible throughout.

Unfortunately, my Motorola HS820 is still not working. Everything seems to be ok, it connects and so, the modules are loaded, alsa configs are in place, etc, but nothing comes in or out the headset :-(

Cheers,
Waldeck

---

### Post by sparks40 on 2008-07-05
Which sound card are you using??

---

### Post by basicuser on 2008-07-10
This is frustrating...

I followed your steps to the letter but when I get to stage 14, I get no recording.

When I try to pair the headphones with my laptop, I get the "couldn't display obex://" message.

Please help

---

### Post by raymondvillain on 2008-07-16
If I type

hciconfig -a

I get the following output:

hci0:	Type: USB
	BD Address: 00:02:76:0D:3F:4F ACL MTU: 1017:8 SCO MTU: 64:0
	UP RUNNING 
	RX bytes:279 acl:0 sco:0 events:39 errors:0
	TX bytes:454 acl:0 sco:0 commands:39 errors:0
	Features: 0xff 0xff 0x8d 0xfe 0x9b 0xf9 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
Can't read local name on hci0: Input/output error (5)

Any idea why this is so?

Using Rocketfish bluetooth keyboard and mouse, both work.  Mouse wheel does not function.  Using an insignia bluetooth headset, supposed to be a2dp compliant.

---

### Post by evertmantel on 2008-07-28
After: arecord -D bluetooth -f s16_LE test.wav
I get an error. Even so, if i do <cntrl-c> the headset looses it's bluetooth conntection. If I leave it be then after some 20/30 secs i get an error.
> Recording WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 8000 Hz, Mono
ALSA lib pcm_bluetooth.c:460:(bluetooth_hsp_hw_params) BT_SETCONFIGURATION failed : Input/output error(5)
arecord: set_params:962: Unable to install hw params:
ACCESS:  RW_INTERLEAVED
FORMAT:  S16_LE
SUBFORMAT:  STD
SAMPLE_BITS: 16
FRAME_BITS: 16
CHANNELS: 1
RATE: 8000
PERIOD_TIME: 125000
PERIOD_SIZE: 1000
PERIOD_BYTES: 2000
PERIODS: 4
BUFFER_TIME: 500000
BUFFER_SIZE: 4000
BUFFER_BYTES: 8000
TICK_TIME: [0 0]


I think it is a problem with alsa.. the stream is not recognized as a valid audio stream. Does anyone have an idea how to configure?
I'm using a two-way head set and intend to use it for skype, mainly.

---

### Post by evertmantel on 2008-07-29
And it all works perfectly under 2.6.22.14-generic! which is a gutsy release, if I'm not mistaken, but not under anything newer!!!

took me 3 days to figure that one out!

---

### Post by yipperzz on 2008-07-29
> **g3k said:**
> I have followed the directions several times, have gotten the headset to pair and even beep when I begin to do a test record so I know there is a connection.

However it does not record anything and when I try to play something back through the headset the capslock and scroll lock lights on my keyboard begin to blink and I am unable to input anything from mouse or keyboard and must force the laptop to power down.

This happens both within Skype and other programs.

I am using a Targus USB dongle (MBT-1203) and a LG HBM-750 Headset.

Are either of these not compatible with sound on Ubuntu or am I not doing something correctly?

I don't know if you figured it out yet or not, but I had the same problem.  Whenever outputting any sound to the BT headset, my caps lock and scroll lock lights would flash too.  From what i found, it was going into kernel panic?  But I was using an old generic Broadcom dongle  that I got from work which is definitely 1.1.  I picked up a cheap 2.0 adapter today and plugged it in and it now works.  I searched the forums and it looks like one other person had the same issue.  So hopefully that helps.

And thanks to the OP for the post.  I got my headset working with skype now also.

---

### Post by fmorales on 2008-07-30
Hi all.. the instruction are greate but i also have problems with skype

I'm running Hardy on kernel 2.6.24-19-generic and I just re-installed skype Version 2.0.0.72. Reading the requierments at the skype page it says libasound2 1.0.12 and I have installed libasound2 1.0.15.

I think that there is where all the problem arises because of the diferent libasound2 versions. Because my bluetooth (Motorola HT820)headset works fine with the rest of the applications.

Do you think a downgrade to libasound2 1.0.12 resolve the issue?

Das anyone know if skype plans to release a new version supporting libasound2 1.0.15.

---

### Post by fmorales on 2008-08-01
Hi all I finally resolved the problem I finally got my bluetooth Motorola ht820 headset working.

What I did was
I installed the latest version of skype (I do not think this resolves te issue)

Hardy by default comes with pulseaudio I removed pulseaudio with:

 sudo apt-get remove libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter

And maked shure that I had alsa running by installing alsa-base libalsaplayer0 and bluetooth-alsa.

I had followed all the instructions on this thread. My .asoundrc is exactly as the one in this thread.

Hope to be of help.

---

### Post by Vlad Savchenkov on 2008-08-05
Hello there.
(IMHO A2DP is kind of thing that should be working by default, to start with, but still...)

I'm running Hardy Heren 32 bit, with an USB Bluetooth dongle working properly (file sharing tested). I am currently trying to make it work with my Sony DR-BT50 headsets (tested with cell phone).
_What's done so far:_

1) I followed the instructions from the first post carefully, but I could only get as far as
> 10) turn on the headset and hit volume up on the headset which should cause your PC to ask for the passkey to pair with the headset
Not only volume up, but any button just didn't do. I also tried enabling pairing mode, but it didn't do as well. Then I rebooted and tried again, with no effect at all.

2) Then I installed blueman and tried it. Headphones were detected and paired, but it wasn't able to connect them for audio saying simply "not supported"
Again, any possible and impossible actions (including reboot) were taken, with no effect at all. It was just "not supported".

3) Finally, I tried the script from [http://fosswire.com/2008/01/11/a2dp-stereo-linux/](http://fosswire.com/2008/01/11/a2dp-stereo-linux/) which I was suprisingly able to make "work". But it "works" only with gstreamer (I couldn't make neither VLC nor mplayer work with it, which I need badly, and it doesn't play other sounds: system sounds, games sounds, Flash sounds and so on, which are also needed, just not so desperately), and, even where it works, the quality of sound is... ahem... it's just unbearably horrible.

Please sorry my lack of patience, but I'm not any kind of programmer or geek or whatever, I don't understand all those drivers and interfaces, I just want it to work.
_I beg for your help!_

Of course I'll provide any additional info or dumps or whatever, if needed.

---

### Post by Vlad Savchenkov on 2008-08-05
Well, it always happens this way: I've spent _an hour_ struggling to make anything work, then I give up and post here, and _next minute_ I miraculously find this:
[http://ubuntuforums.org/showthread.php?t=520515&highlight=bt50&page=2](http://ubuntuforums.org/showthread.php?t=520515&highlight=bt50&page=2)
...and this:
[http://wiki.bluez.org/wiki/HOWTO/AudioDevices#SupportedPlayers](http://wiki.bluez.org/wiki/HOWTO/AudioDevices#SupportedPlayers)
...after which everything suddenly begins to work just fine.
Well, not just "fine", there are still some things to complain (not just ALL sound is redirected to headphones, but only from selected applications, and it takes no less than 8 mouseclicks to switch between wired and wireless sound output), but I'm already happy that my favourite SMPlayer works just fine, allowing me to listen music (including web-radio) and to watch videos without any more problems!
And, yes, sound quality is superb! :)

For all who still have any problems I recommend above-mentioned links (especially, the second one).

---

### Post by longman on 2008-08-07
Hello!

Unfortunately the instructions don't help me to make the headset working, though i have a feeling i am half way there.

I have a Motorola H555 headset and i suppose it should be working, eventually. I got it paired to my computer and it's listed among audio devices.

But when i try "arecord" step it doesn't record anything, but as soon as i press Ctrl-C it looses connection and devices quits. I have to connect it again then. There is no sound file created.

If i try to use Skype with BT headset Testing Call returns "Problem with audio device". Then at first console binded to Ctrl-Alt-F1 i get constantly appearing messages like: "hci_scodata_packet: hci0 SCO packet for unknown connection handle".

Has anyone expereinced such behaviour and is there a way to manage with it? Until now, for some 3 years i've been a happy Ubuntu user, but this problem really makes me upset.

Cheers.

---

### Post by alexeix on 2008-08-08
I'm still unable to get my Plantronics M3000 working with Ubuntu via Bluetooth and in fact, most Bluetooth items seem to have some degree of problem in connecting.

I found a related bug which had been reported a while ago, but can't locate the link now.

Can anyone tell me how to identify which version of Ubuntu is running?  I can't remember if it's 64 bit or not...

---

### Post by alexeix on 2008-08-08
Found the links to the problem I was thinking of...this is the "couldn't display obex" error.


bug report
[https://bugs.launchpad.net/bugs/159887](https://bugs.launchpad.net/bugs/159887)

Thread
[http://ubuntuforums.org/showthread.php?t=791943](http://ubuntuforums.org/showthread.php?t=791943)

---

### Post by thesoffish on 2008-08-09
I finally got my headset to connect all right, but it is having some weird issues with aplay and still doesn't work with Skype.

arecord -D bluetooth -f s16_le test.wav and aplay -D bluetooth -f s16_le test.wav both work as expected, but when I try aplay with a different file it doesn't work:

```
thesoffish@Alice:~$ aplay -D bluetooth -f s16_le /usr/share/sounds/login.wav
Playing WAVE '/usr/share/sounds/login.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
aplay: set_params:906: Channels count non available

```

Does anyone know more about this error message/how to resolve it?

And can anyone tell me what the difference is between snd-bt-sco and snd_bt_sco, or is one of those a typo? I tried removing the snd-bt-sco module, and got the same results as above for both of the aplay tests (test.wav working, login.wav not); however, when I try setting Skype input/output to 'bluetooth,' it gives me 'Problem with Audio Playback/Problem with Audio Capture;' this is with snd-bt-sco enabled. But when I remove it, Skype then works with its i/o set to 'bluetooth,' except that the headset itself doesn't work; rather, it just uses the default laptop speakers and mic.

Regardless of what Skype's settings are, my syslog gives me

```
Aug  8 20:38:33 Alice kernel: [ 9268.550241] snd-bt-sco: playback_open
Aug  8 20:38:33 Alice kernel: [ 9268.550371] snd-bt-sco: capture_open
Aug  8 20:38:33 Alice kernel: [ 9268.550529] snd-bt-sco: playback_open
Aug  8 20:38:33 Alice kernel: [ 9268.550682] snd-bt-sco: capture_open
Aug  8 20:38:34 Alice kernel: [ 9268.839278] snd-bt-sco: playback_open
Aug  8 20:38:34 Alice kernel: [ 9268.839721] snd-bt-sco: capture_open
Aug  8 20:38:34 Alice kernel: [ 9268.840248] snd-bt-sco: playback_open
Aug  8 20:38:34 Alice kernel: [ 9268.840708] snd-bt-sco: capture_open
Aug  8 20:38:35 Alice kernel: [ 9269.177956] snd-bt-sco: playback_open
Aug  8 20:38:35 Alice kernel: [ 9269.178592] snd-bt-sco: capture_open
Aug  8 20:38:35 Alice kernel: [ 9269.179254] snd-bt-sco: playback_open
Aug  8 20:38:35 Alice kernel: [ 9269.180113] snd-bt-sco: capture_open
Aug  8 20:38:38 Alice kernel: [ 9272.023820] snd-bt-sco: playback_open

```

etc. intermittently throughout the call, but when snd-bt-sco is removed it does not do this, yet Skype itself still works (but not the headset).

I might be going in a completely wrong direction with this; if so I apologize for all the useless information. I just want to get the headset (a Jabra BT160) working with Skype and figure out what's going on with aplay, so any help would be greatly appreciated! Although, if it can magically start working with Skype while the aplay thing remains a mystery I won't complain :)

Edit: forgot to mention I am using Hardy 64-bit. I did try putting libasound_module_pcm_bluetooth.so into my lib32 folder, but that had no effect on Skype, and made the arecord/aplay test.wav just play a bunch of static.

Edit again: apparently with the libasound libraries in the lib32 folder aplay of an old version of test.wav works; it is only when I record it again it becomes static.

---

### Post by bailewen on 2008-08-15
I haven't even been able to get that far with Hardy.

omar@omar-laptop:~$ hciconfig -a
hci0:	Type: USB
	BD Address: 00:0A:3A:82:40:11 ACL MTU: 1021:8 SCO MTU: 64:1
	UP RUNNING 
	RX bytes:427 acl:0 sco:0 events:63 errors:0
	TX bytes:4411 acl:0 sco:0 commands:63 errors:0
	Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x79 0x83
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
Can't read local name on hci0: Input/output error (5)


What's with the "Can't read local name on HC0:" ?

---

### Post by thesoffish on 2008-08-15
I have been attempting to route Skype through PulseAudio and set up the headset to work with that; I will post a more detailed procedure once I get it working, but so far it at least looks promising.

I think one of my main problems is that my headset can only handle a sampling rate of 8000 Hz, and has major issues with anything above that. Is there a way I can configure Skype to output at this rate? Or, failing that, could I force PulseAudio or some other intermediate layer to format Skype's output as something my headset can handle?

---

### Post by bailewen on 2008-08-15
> **damis648 said:**
> I think it is much simpler to go into Bluez preferences and then click the services tab, enable audio service and click add at the bottom? Maybe just me...

On mine there is no "add" button on it. There's a window labeled "bonded devices" but the only two choices are "delete" and "disconnect". Nothing that says "add". :confused:

---

### Post by hunter186 on 2008-08-15
I think I'm almost there.  I followed the directions in the first post.  I can record and play back sound.  Skype can recognize and use the headset (a Cardo S-800).

When I try a test Skype call, the audio drops out within 30 seconds.  Once (out of maybe 30 attempts) I was able to record test audio and hear the beginning of the playback.  Then the audio dropped.  If I try to make another test call after this, Skype states that there was a problem with the audio device.  I generally have to delete the headset from the bluetooth device list and restart Skype to try again.

Any ideas?  Really banging my head against the wall on this one.

---

### Post by DarchAengel on 2008-08-15
I don't know what to do anymore.  No matter what I do I can't get past step 9.  Every time I try to do sudo modprobe snd_bt_sco I get the following error:

```

FATAL: Error inserting snd_bt_sco (/lib/modules/2.6.24-19-generic/ubuntu/snd-bt-sco.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

When I run dmesg I get this towards the end of the output:

```

[ 1377.748401] snd_bt_sco: disagrees about version of symbol snd_pcm_new
[ 1377.748421] snd_bt_sco: Unknown symbol snd_pcm_new
[ 1377.749032] snd_bt_sco: disagrees about version of symbol snd_pcm_lib_ioctl
[ 1377.749037] snd_bt_sco: Unknown symbol snd_pcm_lib_ioctl
[ 1377.749543] snd_bt_sco: disagrees about version of symbol snd_pcm_set_ops
[ 1377.749550] snd_bt_sco: Unknown symbol snd_pcm_set_ops
[ 1377.749753] snd_bt_sco: disagrees about version of symbol snd_pcm_period_elapsed
[ 1377.749788] snd_bt_sco: Unknown symbol snd_pcm_period_elapsed
[ 1392.593283] snd_bt_sco: disagrees about version of symbol snd_pcm_new
[ 1392.593304] snd_bt_sco: Unknown symbol snd_pcm_new
[ 1392.594025] snd_bt_sco: disagrees about version of symbol snd_pcm_lib_ioctl
[ 1392.594034] snd_bt_sco: Unknown symbol snd_pcm_lib_ioctl
[ 1392.594449] snd_bt_sco: disagrees about version of symbol snd_pcm_set_ops
[ 1392.594453] snd_bt_sco: Unknown symbol snd_pcm_set_ops
[ 1392.594651] snd_bt_sco: disagrees about version of symbol snd_pcm_period_elapsed
[ 1392.594656] snd_bt_sco: Unknown symbol snd_pcm_period_elapsed
[ 1751.164079] snd_bt_sco: disagrees about version of symbol snd_pcm_new
[ 1751.164099] snd_bt_sco: Unknown symbol snd_pcm_new
[ 1751.164717] snd_bt_sco: disagrees about version of symbol snd_pcm_lib_ioctl
[ 1751.164722] snd_bt_sco: Unknown symbol snd_pcm_lib_ioctl
[ 1751.165176] snd_bt_sco: disagrees about version of symbol snd_pcm_set_ops
[ 1751.165180] snd_bt_sco: Unknown symbol snd_pcm_set_ops
[ 1751.165475] snd_bt_sco: disagrees about version of symbol snd_pcm_period_elapsed
[ 1751.165482] snd_bt_sco: Unknown symbol snd_pcm_period_elapsed

```

How can I fix this,please?

---

### Post by Havel on 2008-08-18
Hunter186

I have the exact same problem you have. I did what the first post says.

When I go in Skype sound settings I can choose Bluetooth. The sound test works, but the call test does'nt work...it starts, but it is rapidly interrupted. If I try a real call, it is interrupted a soon as someone answers the call.

Frustrating!

I will try the Skype Forum...will let you know if I get something there. I'm close to returning the headset back to the store.

---

### Post by hunter186 on 2008-08-19
Havel,

Good to know I'm not alone.  I'm in the process of moving to Korea, so I'll probably be occupied for the next couple days.  Hoping to tackle this problem over there.  Good luck on the Skype forums.  I'll post again as soon as I have more info.

I have noticed that dmesg shows this output:  
```
[ 1269.377906] snd-bt-sco: playback_open
[ 1269.379250] snd-bt-sco: capture_open
[ 1269.576699] snd-bt-sco: playback_open
[ 1269.577806] snd-bt-sco: capture_open
[ 1269.579144] snd-bt-sco: playback_open
[ 1269.580931] snd-bt-sco: capture_open
[ 1270.051332] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 342
[ 1271.719298] snd-bt-sco: playback_open
[ 1271.720769] snd-bt-sco: capture_open
[ 1271.722632] snd-bt-sco: playback_open
[ 1271.724713] snd-bt-sco: capture_open
[ 1271.726785] snd-bt-sco: playback_open
[ 1271.728155] snd-bt-sco: capture_open
[ 1271.729775] snd-bt-sco: playback_open
[ 1271.731328] snd-bt-sco: capture_open
[ 1280.002587] snd-bt-sco: playback_open
[ 1280.003504] snd-bt-sco: capture_open
[ 1280.004938] snd-bt-sco: playback_open
[ 1280.006320] snd-bt-sco: capture_open
[ 1280.008070] snd-bt-sco: playback_open
[ 1280.009145] snd-bt-sco: capture_open
[ 1280.010521] snd-bt-sco: playback_open
[ 1280.011833] snd-bt-sco: capture_open
[ 1280.041070] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1
[ 1284.257626] snd-bt-sco: playback_open
[ 1284.258825] snd-bt-sco: capture_open
[ 1284.260317] snd-bt-sco: playback_open
[ 1284.262196] snd-bt-sco: capture_open
[ 1284.264324] snd-bt-sco: playback_open
[ 1284.265492] snd-bt-sco: capture_open
[ 1284.267090] snd-bt-sco: playback_open
[ 1284.268537] snd-bt-sco: capture_open

```

Not sure what it means yet.  Maybe someone smarter than myself has some input.

---

### Post by digimark on 2008-08-21
HI,

Progress! I can run the arecord and a play and get white noise in my earpiece!!! however I cant hear the recording! running alsamixer and the mic part is at 00 and wont let me increase volume?

Also despite this i should get something in Skype and although I can see the device in the sounds config in skype it doesnt work - just keeps saying 'problem with Audio playback' - it works fine onthe main laptop speakers and mic.....

any thoughts?

/M

---

### Post by eljenso on 2008-08-24
I followed the instructions step by step, and it works. Thanks a lot! However, since I changed my bluetooth device, I have not been able to play back to my headset anymore...

I can still record voice, e.g. with arecord, and also play the recorded file with aplay on my notebook speakers. If I try to play the same file on my headset, the headset turns on, but the file will not be played. The headset remains turned on until I kill aplay...

Any ideas what's going wrong? Has anybody had (and maybe solved) the same problem? Thanks for any replies.

---

### Post by kcallis on 2008-08-28
Since I am not a Skype user, I don't know if this is a problem because using the bluetooth headset will only work with skype or if I am having some other issues.

I am using a Plantronics Voyager 520, and my VOIP client is Xten. When I go to the audio wizard, it only recognizes the built-in hardware, and there is not option to point toward the BT headset. So is the problem because of the client or did I miss a step in setup.

I am using blueman to manange the BT connection...

I fired up Xten softphone, and when I went to the audio wizard, it doesn't allow me to change any of the devices (microphone or speaker). Looks like I am stuck using a wired headphone/mic and get rid of the bluetooth option altogether...

**** The adventure continues:

Digging around, I realized that possibly Xten didn't know how to play nicely with bluetooth, so I moved to twinkle (which can be found in the repositories). It does recognize bluetooth devices, and I was almost ready to dance a jig. Of course, when I fire up twinkle, it says it is not able to access to access the bluetooth device:

Thu 00:53:44
Critical: Opening ALSA driver failed: snd_pcm_hw_params_any failed: Invalid argument

Any suggestions on how to get that working?

---

### Post by dayzman on 2008-09-09
> **kcallis said:**
> Of course, when I fire up twinkle, it says it is not able to access to access the bluetooth device:

Thu 00:53:44
Critical: Opening ALSA driver failed: snd_pcm_hw_params_any failed: Invalid argument

Any suggestions on how to get that working?

I'm having this problem as well. Any help will be appreciated.

---

### Post by farbird on 2008-09-10
using hardy..

when i reach the part to do
 pactl load-module module-alsa-sink device=bluetooth

it says
 Failure: Module initalization failed

when doing 
 aplay -D bluetooth -f s16_le /usr/share/sounds/login.wav 
it says
 ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM bluetooth
 aplay: main:546: audio open error: No such file or directory


Seems hardy is poor in dealing with bluetooth headset.
Is there no easy way?

Windows is a lot easier..

---

### Post by chiefofthejojos on 2008-09-18
> **secr3tuprising said:**
> There's a site that made this really easy,
[http://fosswire.com/2008/01/11/a2dp-stereo-linux/](http://fosswire.com/2008/01/11/a2dp-stereo-linux/)
the scripts are already there if you don't want to re-create them

I must agree!  I tried some of the other stuff mentioned and it was needlessly difficult.  Why not just use a pre-made script which does it all?  I feel it is my duty as an ubuntero to help others find the method which "just works".  Not only am I listening to my music on my headset, but I can also control playback with the buttons on it.
Something I am having a harder time with, however, is thanking secr3tuprising here.  Can anyone explain to me how I can do that?
Thanks,
Brad

---

### Post by fh_scott on 2008-09-24
> **eljenso said:**
> I followed the instructions step by step, and it works. Thanks a lot! However, since I changed my bluetooth device, I have not been able to play back to my headset anymore...

I can still record voice, e.g. with arecord, and also play the recorded file with aplay on my notebook speakers. If I try to play the same file on my headset, the headset turns on, but the file will not be played. The headset remains turned on until I kill aplay...

Any ideas what's going wrong? Has anybody had (and maybe solved) the same problem? Thanks for any replies.

I have two headsets. Plantronics 510 and Jawbone2.  The Plantronics works perfectly, the Jawbone2 behaves like yours.

This behavior is identical on my x86 and x64 systems.

No idea.

-scott

---

### Post by art_erickson on 2008-10-02
Is there an undo script to go with this?

---

### Post by coskierken on 2008-10-04
ok, got the device (plantronics 510) seen and paired.  how do I get sound to it?  Newbie here!  Thanks in advance.

---

### Post by art_erickson on 2008-10-05
I just manually removed anything I could remember installing - bluetooth, Bluz, anything to do with sound like pulse audio, ad nauseum.

I'm hoping 8.10 fixes all this natively.

Meanwhile I'll evaluate some hardware that allegedly lets me use my cordless phone with Skype - not elegant, but if it works what can I say.

So very interesting what works 'out of the box' and what doesn't with the various OSes.

---

### Post by rkn5555 on 2008-11-17
i followed all the steps. at  step #10. when pressing volume up. to get it to ask for pin. that never worked.
i even tried the bluez-pin in address name etc. it did ask me for pin to connect. but that wasnt doing anything. 

and in my sound config. i did change vol and mic for the device.

when i finally got the system to ask ME. for the pin.
it was when i did the test at step #14.

worked great. 
staticy in the test. ill recharge headset a little more thry and tweak.

thanks for this tutorial!!

---

### Post by alexeix on 2008-11-18
The Bluetooth problems still exist in 8.10, although in a slightly different form.

The end result is the same though; it seems people are having problems connecting Bluetooth headsets.

See...

[http://ubuntuforums.org/showthread.php?t=968005&page=2](http://ubuntuforums.org/showthread.php?t=968005&page=2)

:(

---

### Post by |Eric| on 2008-12-12
hi good help was able to pair my Cardo S2 headset still trying to get sound 
i would like to note that if you get the folloing error just do a hcitool hciX up 

error:
$ sudo hciconfig hci0 -a
hci0:	Type: USB
	BD Address: xxxxxxxxx ACL MTU: 1021:8 SCO MTU: 64:1
	UP RUNNING 
	RX bytes:381 acl:0 sco:0 events:52 errors:0
	TX bytes:2148 acl:0 sco:0 commands:52 errors:0
	Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x79 0x83
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
Can't read local name on hci0: Input/output error (5)<<<<<<<<<<<

---

### Post by ScottyP on 2009-01-03
> **digimark said:**
> HI,

Progress! I can run the arecord and a play and get white noise in my earpiece!!! however I cant hear the recording! running alsamixer and the mic part is at 00 and wont let me increase volume?

Also despite this i should get something in Skype and although I can see the device in the sounds config in skype it doesnt work - just keeps saying 'problem with Audio playback' - it works fine onthe main laptop speakers and mic.....

any thoughts?

/M

> **eljenso said:**
> I followed the instructions step by step, and it works. Thanks a lot! However, since I changed my bluetooth device, I have not been able to play back to my headset anymore...

I can still record voice, e.g. with arecord, and also play the recorded file with aplay on my notebook speakers. If I try to play the same file on my headset, the headset turns on, but the file will not be played. The headset remains turned on until I kill aplay...

Any ideas what's going wrong? Has anybody had (and maybe solved) the same problem? Thanks for any replies.

> **fh_scott said:**
> I have two headsets. Plantronics 510 and Jawbone2.  The Plantronics works perfectly, the Jawbone2 behaves like yours.

This behavior is identical on my x86 and x64 systems.

No idea.

-scott

Same problem here! I can record just fine and play it back on my desktop speakers, but I can't hear anything through my headset except dead air.

I used this walkthrough to hook up this headset to my laptop yesterday and it worked great. Thanks!

-Scott

---

### Post by ALittleSlow on 2009-02-16
> **ghuqu said:**
> Alright I did as instructed and so far so good until I tested it. When I input $ arecord -D bluetooth -f s16_LE test.wav 
I received this; Recording WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 8000 Hz, Mono
Warning: rate is not accurate (requested = 8000Hz, got = 16000Hz)
         please, try the plug plugin (-Dplug:bluetooth)

What does this mean?

I think it means your headset doesn't support the default rate of 8000Hz. Try 

$ arecord -D bluetooth -r 16000 -f s16_LE test.wav

Hope this helps.

---

### Post by eljenso on 2009-04-04
Hi there

I still haven't solved my problem yet:

> **eljenso said:**
> I can still record voice, e.g. with arecord, and also play the recorded file with aplay on my notebook speakers. If I try to play the same file on my headset, the headset turns on, but the file will not be played. The headset remains turned on until I kill aplay...

I have no clue what's going wrong and would still be grateful for any hints. If I type 'hciconfig -a', I get this output:

hci0:   Type: USB
        BD Address: XXXXXXXXXX ACL MTU: 1017:8 SCO MTU: 64:0
        UP RUNNING PSCAN ISCAN
        RX bytes:1329619 acl:254 sco:25853 events:284 errors:0
        TX bytes:6141 acl:220 sco:0 commands:127 errors:0
        Features: 0xff 0xff 0x8d 0xfe 0x9b 0xf9 0x00 0x80
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
        Link policy: HOLD SNIFF PARK
        Link mode: ACCEPT MASTER
        Name: 'T1000-2'
        Class: 0x0800ca
        Service Classes: Capturing
        Device Class: Miscellaneous,
        HCI Ver: 2.0 (0x3) HCI Rev: 0x403d LMP Ver: 2.0 (0x3) LMP Subver: 0x430e
        Manufacturer: Broadcom Corporation (15)

Does anyone see anything that could bge wrong here? Thanx a lot in advance for any replies!

---

### Post by eljenso on 2009-05-14
Hi there,

has anybody tried this installation on Jaunty 9.04? I have recently upgraded from Hardy to Jaunty and there I am struggling with this step:

> **psyke777 said:**
> 9) load bluetooth SCO drivers
$ **sudo modprobe snd_bt_sco**
$ **sudo modprobe sco**
You might want to put these in /etc/modules

Apparently, these drivers do not exist anymore in jaunty. Does anyone know whether any other drivers replace them? Maybe someone knows how to get a bluetooth headset running with Skype in a different way? Thanx a lot in advance for your answer!

---

### Post by kcallis on 2009-05-14
> **eljenso said:**
> Hi there,

has anybody tried this installation on Jaunty 9.04? I have recently upgraded from Hardy to Jaunty and there I am struggling with this step:



Apparently, these drivers do not exist anymore in jaunty. Does anyone know whether any other drivers replace them? Maybe someone knows how to get a bluetooth headset running with Skype in a different way? Thanx a lot in advance for your answer!

I actually got my headset working with Skype, but the person on the other end said all he could hear was static... I guess I will look at that issue later.

---

### Post by kepreon on 2009-05-14
I haven't tried this specifically with Skype, but got a bluetooth headset to work with Ekiga earlier today: [http://ubuntuforums.org/showthread.php?t=1152229](http://ubuntuforums.org/showthread.php?t=1152229).  Much more point and click (after you upgrade the relevant packages)

I know Skype doesn't recognize PulseAudio, but you can go from there and interface with ALSA.

---

### Post by Wolle69 on 2009-09-02
Hi kepreon,

I managed to get Skype working very well with this thread (Thanks a lot to all of you!), after investigating for several days. Just a minute ago, I shared my way in a German forum in order to help others.

Unfortunately I don't get Ekiga working with my headset, which was my primary purpose. Starting a test  call on sip:10005@sipgate.de (my VoIP provider) seems to work, Ekiga doesn't report any errors, just the headset stays quiet, headset microphone doesn't either seem to work.

The link you provided deals with a2dp, but I thought that would be used for stereo headset usage (one way!) instead of mono but 2-way?! Is that really what I should try in order to get Ekiga working?!

Could you please explain, how you got Ekiga working with your bluetooth headset?

Ekiga console output is:
```
ALSA lib pcm_params.c:2135:(snd1_pcm_hw_refine_slave) Slave PCM not usable
Cannot initialize hardware parameter structure Invalid argumentCannot set access type Invalid argumentCannot set sample format Invalid argumentCannot set channel count Invalid argumentCannot set sample rate Invalid argumentCannot set period size Invalid argumentCannot set periods to Invalid argumentCannot set buffer_time to  50 ms Invalid argumentCannot set period_time to 10 ms   Invalid argumentCannot set parameters Invalid argument
```

Cheers
Wolle

P.S.: My setup:
-Ubuntu-64 with 2.6.24-24-generic kernel
-Skype 2.0.0.72
-Pulseaudio running
-Headset seems to work via ALSA
-solved skype problem simply  by getting libasound_module_pcm_bluetooth.so and libasound_module_ctl_bluetooth.so from the i386-package of bluez-audio and stored them in /usr/lib32/alsa-lib

---

### Post by aniketvb on 2009-09-02
Why dont you try the new skype beta version 2.1 . It has native support for pulseaudio.

---

### Post by alexeix on 2009-09-02
I bought a new Nokia headset and installed the latest Skype Beta (after a fresh install of Jaunty).

I finally managed to get Skype working with the bluetooth headset, but there seems to be a delay in the sound transmission.

I need to do some further testing to check if it was just a one-off.

It's a real shame this kind of thing doesn't just work out of the box, like with OSX...
There are clearly problems using Bluetooth devices with Ubuntu, but the issue doesn't appear to be getting much priority.

---

### Post by Wolle69 on 2009-09-03
> **aniketvb said:**
> Why dont you try the new skype beta version 2.1 . It has native support for pulseaudio.

Because:
1. Skype 2.0.0.72 works very well for me!
2. The new Skype isn't in the repos and it's a beta version. Installing such software always causes a lot of huddle!
**3. I don't want to use Skype! My primary goal is to use a VoIP client like Twinkle or Ekiga!!!** This was just testing. I've got no regular phone number yet, so my grandfather (e.g.) can't call me. VoIP is a good solution in such cases, but I need to get the softphone software working with the headset. Using the softphone software with a cable mic and phones works perfectly!
4. By the way: Skype is proprietary software... ;)

> There are clearly problems using Bluetooth devices with Ubuntu, but the issue doesn't appear to be getting much priority.     It's always very important to have a distinct phrasing of problems in order to get a useful solution. In my case, bluetooth worked very well and out of the box! The problem getting Skype to work was a problem related to ALSA-libs (32bit/64bit incompatibility). The problem I've got with Twinkle/Ekiga also seems to be related to ALSA - not to bluetooth...

Cheers
Wolle

---

### Post by alexeix on 2009-09-17
Well I still have this problem with delayed audio in Skype.

Whether it's down to Bluetooth or Pulseaudio, I don't know (although most likely you're right and it's the latter).

However, the fact is, this just doesn't work in a usable way.

In Windows 7, once I updated the Bluetooth drivers, bingo, no problems, no audio delays!
Likewise in OSX.
I like to use Ubuntu and think it's a great OS with lots of potential, but it has to be easy to do things or there's just no point using it.

How do I log this as a bug and if I do, is it likely to be given any kind of priority?
I ask this because I've noticed various similar bugs which haven't been addressed.

---

### Post by trifgabi on 2010-06-11
Hello.
I am having some problems with the Motorola S805 headphones in Lucid Lynx. Pairing and connecting works fine. Disconnecting and audio do not work. 
Any advice where to start the troubleshooting?


Nevermind! After deleting the device and re-adding it a few times it finally started working.

---

