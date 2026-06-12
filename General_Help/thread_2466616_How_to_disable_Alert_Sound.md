---
title: "How to disable Alert Sound"
date: 2021-09-01
forum: General Help
---

### Post by satimis on 2021-09-01
Hi all,

Ubuntu 20.04

For unknown cause the "sound alert" is suddenly on.  Whenever I type on keyboard or moving the mouse pointer the "alert sound" plays.  It is very strange to me.

On Terminal running;
$ gsettings set org.gnome.desktop.sound event-sounds false

unable to solve the problem

On Settings -> Sound -> Alert Sound

there is no place to disable it.

Please help.

Regards

---

### Post by cmcanulty on 2021-09-01
in Xubuntu click on 
speaker icon-audio settings-mixer-playback-system sounds 
and pull slider to zero maybe there's a similar setting in ubuntu

---

### Post by satimis on 2021-09-01
> **cmcanulty said:**
> in Xubuntu click on 
speaker icon-audio settings-mixer-playback-system sounds 
and pull slider to zero maybe there's a similar setting in ubuntu
Hi,

Thanks for your advice.

On speaker icon (on the right corner of top bar) I can pull the slider to zero then the alert sound stops.  But on playing online video there is no sound.  If pulling the slider to the right the sound of video and alter sound come out together.  It is very funny to me.

I don't know how this happen?   I haven't altered any setting on Ubuntu 20.04

Regards

---

### Post by Dennis N on 2021-09-01
The slider of the speaker icon on the top bar is not the right place.

Open **Settings > Sound** 
In **Volume Levels** Section on right pane, click the speaker icon at the right of the **System Sounds** slider. That will mute the system sounds only.

---

### Post by cmcanulty on 2021-09-01
the key is to just set "system sounds" to zero and leave other sounds alone. I am not sure where system sounds is on Ubuntu

---

### Post by satimis on 2021-09-01
> **Dennis N said:**
> The slider of the speaker icon on the top bar is not the right place.

Open **Settings > Sound** 
In **Volume Levels** Section on right pane, click the speaker icon at the right of the **System Sounds** slider. That will mute the system sounds only.
Thanks for your advice.

-> Volume Levels -> System Sounds
I couldn't select any item there.  It is very strange to me?

Regards

---

### Post by satimis on 2021-09-01
> **cmcanulty said:**
> the key is to just set "system sounds" to zero and leave other sounds alone. I am not sure where system sounds is on Ubuntu
Hi.

Settings -> Volume Level
System Sounds

But I couldn't select this item.  The O icon greyout

---

### Post by satimis on 2021-09-01
This is my first time encountering this strange thing.  When I type it will spell the character which I type.  When I move the mouse pointer over an item e.g. Setting/lock/ etc. it will sound Setting/lock/

When I hit Return key it will sound return.  Do I need to reinstall Ubuntu 20.04?

Regards

---

### Post by ajgreeny on 2021-09-01
It sounds as if you have somehow enabled the facilities that are available for those with restricted or loss of eyesight.

I'm not on my Xubuntu box at present so can not look to see what exactly it is called or how to disable it but I think you'll find it somewhere in the system settings maybe in some extra Accessibility setting.

---

### Post by satimis on 2021-09-01
> **ajgreeny said:**
> It sounds as if you have somehow enabled the facilities that are available for those with restricted or loss of eyesight.

I'm not on my Xubuntu box at present so can not look to see what exactly it is called or how to disable it but I think you'll find it somewhere in the system settings maybe in some extra Accessibility setting.
Check all items under Settings.  It seems to me no item relevant.

However
-> Sound
on the right column
Volume Levels
I can't adjust the level on all items.  However there are 2 "speech-dispat..." items and 2 VirtualBox items

---

### Post by satimis on 2021-09-02
Hi ajgreeny and all,

It is a mystery here.

Yesterday, I played here several hours and couldn't solve the problem of those sounds generated on moving the mouse pointer (including reinstalling Google Chrome).

Today I start my PC, the mentioned problem, narration sound, disappeared.  Then I test a mp3 file and a mp4 file and they work, no narration sound generated on moving the mouse pointer.

Then I start Firefox playing Youtube video.  The video work properly with sound but without narration sound.

Then I start Google Chrome, playing online video and the video work properly with sound but no narration sound.  However playing the video on Firefox becomes without sound.

Re-starting PC unable to solve problem.  Online video played on Firefox without sound but online video played on Google Chrome with sound.  However no narration sound is found on moving the mouse pointer.

The "Del" key on the keyboard doesn't work, pressing "Number Lock" key unable to solve problem.  Hitting "Del" key either typing "." (dot) or popup the "Find Window".

However
Settings -> Sound
on the right column
Volume Levels
All items unable to adjust

That is the present situation

Regards

---

