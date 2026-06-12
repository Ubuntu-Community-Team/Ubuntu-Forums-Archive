---
title: "thunderbird - unable to use wave file for new email message arrival"
date: 2008-06-19
forum: General Help
---

### Post by wandalalakers on 2008-06-19
Thunderbird version 2.0.0.14 (20080505)
Kubuntu 8.04

When I import a wav file to be used for a new email message sound, thunderbird
locks up.  I've tried two different wave files.  I'm able to play these wave
files using Amarok so they wave files do work just not when trying to import
and play them using Thunderbird.

Steps to reproduce error:
1.open thunderbird, edit, preferences, general
2.play a sound, use the following sound file
3. browse, open, play and thunderbird locks up

Results:  
thunderbird locks up every time steps 1-3 are done

When sending myself an email to test and see if the sounds works, thunderbird
causes the operating system to not respond.  I have to right click on the
thunderbird program and terminate the session.

By the way, I've even tried wave files that are included with kubuntu.
I've tried more than one wave file.
I always get the same result.
I've also tried these wave files that come with kubuntu: 
kde_startup.wav and kde_logout.wav
It also seems like only .wav files are accepted for import into thunderbird.  The program doesn't seem to use *.ogg files.
I've attached kde_startup.zip and kde_logout.zip for you guys to try. 

Note: Can you guys please reply to this Mozilla bug report that I created if you are having the same problem with thunderbird?
[https://bugzilla.mozilla.org/show_bug.cgi?id=440310](https://bugzilla.mozilla.org/show_bug.cgi?id=440310)

Thx!

---

### Post by manfer on 2008-06-20
It works perfect on ubuntu.

Are you running any player at the same time when the problem happens, e.g. rhythmbox?

Why don't you try configuring thunderbird to use system default sound for incoming mail instead? It is in the same place in thunderbird. Maybe no conflicts that way.

Configure the system sound for incoming mail where you configure system sounds in kde control panel.

---

### Post by wandalalakers on 2008-06-20
Nothing else is using sound when I try to play a sound when new email arrives.  Seems like other folks have posted this problem about thunderbird.
The default setting is "default system sound for new mail".  I'll try telling kde to use a certain sound for thunderbird.  Thx.

Update:  here is a problem.  

I want to use a custom wave file my my incoming thunderbird email.  I just wanted to test a wave file that comes with kubuntu to verify that it's not my yabba.wav sound file causing the problem.  I have a yabba.wav file (Fred Flintstone) that I used to use with outlook express for windows xp when new mail arrived.  I just mentioned kde_startup.zip and kde_logout.zip because every has those wave files if they have kde/kubuntu.  This way everyone could see what happens when they try a wave file using my method.  I'm back to square one because I want to use my yabba.wav or some other wave file that doesn't come with kde/kubuntu.  Thx for responding though.

Update again: I'm trying the kmail option and using my yabba.wav file.  I'm modify the execute a path part and put thunderbird email info there and see if that works.  Thx again.

Update again: since this option is for kmail it didnt' work.  I tried the following: (print screen is attached)
Hopefully the Mozilla folks will fix this option for linux.  One of their techs said it works for xp and I told him I'm using linux.
I could care less about the xp version.  Long live kubuntu and down with xp and vista!
Although, I do recommend Firefox and Thunderbird to my friends and family using xp.

Similar posts for other folks having problems playing custom wav files using thunderbird:
[https://bugzilla.mozilla.org/buglist.cgi?quicksearch=wav+file](https://bugzilla.mozilla.org/buglist.cgi?quicksearch=wav+file)
Mine is the number one listed last.
The other folks didn't list the steps to produce their problem though.
It looks like the kde control panel is good for wav or ogg files that come with kde/kubuntu and kde/kubuntu apps.  If you want this to apply to a third party program, it's harder to get working using the control panel.

I tried using my sound file another way and I still don't get sound with an incoming email.

---

### Post by wandalalakers on 2008-06-20
Manfer, just to make sure we are on the same page, you have tried my steps 1-3 using ubuntu and thunderbird and you are able to play an sound for incoming thunderbird email?  Thx again for responding.

Can someone using kubuntu and thunderbird test this for me using these steps:

1.open thunderbird, edit, preferences, general
2.play a sound, use the following sound file
3. browse, open, play and thunderbird locks up

Results:
thunderbird locks up every time steps 1-3 are done

I'm using:
Thunderbird version 2.0.0.14 (20080505)
Kubuntu 8.04

---

### Post by manfer on 2008-06-20
Yes, I did those steps but as I said in previous message on ubuntu hardy, not kubuntu. It works fine. My Thunderbird version is the same 2.0.0.14.

That's why I am not sure it is a thunderbird issue. It could be related with sound system.

---

### Post by wandalalakers on 2008-06-20
Thx again.

I tried the following suggestion per this post and thunderbird still locks up when I get an incoming email.  I tried the add-on "mailbox alert".

[http://ubuntuforums.org/archive/index.php/t-237909.html](http://ubuntuforums.org/archive/index.php/t-237909.html)

[https://addons.mozilla.org/en-US/thunderbird/search?q=mailbox+alert&cat=all](https://addons.mozilla.org/en-US/thunderbird/search?q=mailbox+alert&cat=all)

---

### Post by davidpeace on 2008-07-03
About the wav files: how come some will play in the system sounds or the new mail sound (I use Seamonkey) and others won't? And how do I open the file up to check for differences...?

---

### Post by wandalalakers on 2008-07-06
More info about two desktops that I have posted this problem on:

I just tried on another pc with kubuntu 8.04 and thunderbird version 2.0.0.14
(20080505).  My secondary pc is able to play sound.  My primary pc has an Asus
motherboard and an onboard sound card.
My secondary pc has an Acer motherboard and an onboard sound card.

When doing a aplay -l from terminal I get this about my audio:

Asus motherboard
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Acer motherboard
**** List of PLAYBACK Hardware Devices ****
card 0: V8233A [VIA 8233A], device 0: VIA 8233A [VIA 8233A]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I don't have another desktop that uses HDA or has a Realtek ALC662 chipset for the sound.  Maybe this problem only occurs with sound cards that use HDA or a sound card that uses the Realtek ALC662 chipset but I'm not sure.

Anyone happen to use thunderbird and have a Realtek ALC662 sound card?  If so, can you please see if you have this problem also?

---

### Post by thane1 on 2009-02-15
Got it after a lot of searches and trying a few programs suggested by others.  Thunderbird does indeed seem to be very choosy as suggested with regards to the sampling rate it will play.  Started with  a .wav file having a modest size of 72KB (6 seconds total), mono, 11025Hz and uncompressed 8 bit PCM audio, which wouldn't play as it turns out due strictly to the sample rate.  My system: Ubuntu 8.10 and using Thunderbird 2.0.0.19 .  After trial and error here is the order in which things were done to get a successful result.  Downloaded [COLOR="Red"]Audacity[/COLOR] from the Ubuntu Synaptic repositories.  Open from [COLOR="Red"]Applications – Sound and Video – Audacity[/COLOR].  Close the notification msg on top of Audacity workspace, click [COLOR="Red"]file, open[/COLOR] and [COLOR="Red"]browse[/COLOR] to load your desired soundfile.   In the [COLOR="Red"]project rate[/COLOR] box at the bottom my 11025 value showed up in the box.  Open the box and select [COLOR="Red"]22050[/COLOR].  Next your file needs to be saved at this sample rate.  However it seems, that although you can save directly, the only way to make the saved version useable by Thunderbird is to use the [COLOR="Red"]file – export[/COLOR] function from the top menu list.  Save the file in the directory of your choosing by exporting and close out Audacity.  In the Ubuntu Top Menu, select [COLOR="Red"]System – Preferences – Sound – Sounds – Desktop/New Email[/COLOR] and click on the [COLOR="Red"]default[/COLOR] sound setting.  Choose [COLOR="Red"]custom[/COLOR] and [COLOR="Red"]browse[/COLOR] to your new sound file's directory and select your sound.  When done, close out this feature and start up Thunderbird.  On the top menu click [COLOR="Red"]edit – preferences[/COLOR]  and under the [COLOR="Red"]general[/COLOR] heading in [COLOR="Red"]when new mail arrives[/COLOR], enable [COLOR="Red"]play a sound[/COLOR] and [COLOR="Red"]use the following soundfile[/COLOR].  [COLOR="Red"]Browse[/COLOR] to your soundfile's directory, select your file, close out this feature and send yourself a test email (not sure if I restarted Tbird first or not).  If all went well I think it should work for you.  Cheers.[COLOR="Red"][/COLOR]

---

### Post by zuerston on 2009-06-20
These 2 will work in Thunderbird,seems some are not even wav files,just labled so,
.

---

