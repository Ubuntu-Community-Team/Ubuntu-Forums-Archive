---
title: "Backp software for Android worked in 20.04 but not in 22.04"
date: 2023-07-22
forum: General Help
---

### Post by Roland_Msl on 2023-07-22
I have in Perl written a software to copy files from my Android smartphone to my Ubuntu laptop.
All worked fine in Ubuntu 20.04

The access was by
/run/user/1000/gvfs/mtp:host=Xiaomi_Redmi_6_04c2b4747d31/RM64GBR6

But not in 22.04. The Android shows in Files, not like at other folders an option “Open in a terminal”.

---

### Post by TheFu on 2023-07-22
If you don't post the code, how can anyone help, assuming they can read your perl?
I suspect perl isn't really important, since if you want to copy stuff off android, why not just use **adb**?

And perhaps the version of Android would matter for this issue?  IDK.
Does the phone get discovered by **adb**?  It would show in **dmesg** output.

---

### Post by Roland_Msl on 2023-07-23
> **TheFu said:**
> If you don't post the code, how can anyone help, assuming they can read your perl?
I suspect perl isn't really important, since if you want to copy stuff off android, why not just use **adb**?

And perhaps the version of Android would matter for this issue?  IDK.
Does the phone get discovered by **adb**?  It would show in **dmesg** output.

it starts with

opendir ( DIR, "/run/user/1000/gvfs/mtp:host=Xiaomi_Redmi_6_04c2b4747d31/RM64GBR6" )

this fails in Ubuntu 22.04.2
this worked in Ubuntu 16.04, 20.04, 20.04.3

---

### Post by TheFu on 2023-07-23
Can you answer the other question?

Do you have mtp and gfvs libraries loaded? I do'nt think they are there by default.

If I told you my computer and phone won't connect over USB, what troubleshooting would you request?  That's what would be useful.  Forget the perl part. I doubt it matters.

Did you try using adb?

---

### Post by tea for one on 2023-07-23
> **Roland_Msl said:**
> But not in 22.04. The Android shows in Files, not like at other folders an option “Open in a terminal”.
For me, there is an option "Open in Terminal" in Nautilus.

Attach phone with USB cable
Android settings > Connected devices > USB > File Transfer (checked)

Open Files (Nautilus)
Select phone in left pane
Main window should show icons for [COLOR="#0000FF"]Internal shared storage[/COLOR] and, possibly, [COLOR="#0000FF"]SD card[/COLOR]
Right Click either folder icon > Open in terminal
```
edited@edited-22-04:/run/user/1000/gvfs/mtp:host=motorola_moto_g_7__plus_ZY225D2H5D/Internal shared storage$ ls
Alarms         com.musicplayer.playermusic  Movies         Podcasts
alt_autocycle  DCIM                         Music          Ringtones
Android        Download                     Notifications
bluetooth      MapsWithMe                   Pictures
edited@edited-22-04:/run/user/1000/gvfs/mtp:host=motorola_moto_g_7__plus_ZY225D2H5D/Internal shared storage$ 

```

---

### Post by Roland_Msl on 2023-07-23
> **tea for one said:**
> For me, there is an option “Open in Terminal” in Nautilus.

Attach phone with USB cable
Android settings > Connected devices > USB > File Transfer (checked)

Open Files (Nautilus)
Select phone in left pane
Main window should show icons for [COLOR=#0000FF]Internal shared storage[/COLOR] and, possibly, [COLOR=#0000FF]SD card[/COLOR]
Right Click either folder icon > Open in terminal
```
edited@edited-22-04:/run/user/1000/gvfs/mtp:host=motorola_moto_g_7__plus_ZY225D2H5D/Internal shared storage$ ls
Alarms         com.musicplayer.playermusic  Movies         Podcasts
alt_autocycle  DCIM                         Music          Ringtones
Android        Download                     Notifications
bluetooth      MapsWithMe                   Pictures
edited@edited-22-04:/run/user/1000/gvfs/mtp:host=motorola_moto_g_7__plus_ZY225D2H5D/Internal shared storage$ 

```

I see my Redmi 6 as an icon on the left. 
I see my Redmi 6 in “Files”.
But at right click is no option to “open in a terminal”.
I checked with other folders, there is always the option “open in a terminal”, but not at the USB connected Redmi 6.

---

### Post by tea for one on 2023-07-23
> **Roland_Msl said:**
> I checked with other folders, there is always the option “open in a terminal”, but not at the USB connected Redmi 6.
That's a bit disappointing.
When these odd events happen to me, I often boot up a "Try Ubuntu" live session to test.
Using 22.04 live, I can see and "open in terminal" both internal storage and SD card.
```
ubuntu@ubuntu:/run/user/999/gvfs/mtp:host=motorola_moto_g_7__plus_ZY225D2H5D/SD card$ 
```
Perhaps, try a live session or double check all the Android settings?

---

### Post by Roland_Msl on 2023-07-23
> **tea for one said:**
> That's a bit disappointing.
When these odd events happen to me, I often boot up a "Try Ubuntu" live session to test.
Using 22.04 live, I can see and "open in terminal" both internal storage and SD card.
```
ubuntu@ubuntu:/run/user/999/gvfs/mtp:host=motorola_moto_g_7__plus_ZY225D2H5D/SD card$ 
```
Perhaps, try a live session or double check all the Android settings?

My backup system for my Redmi 6 works since years. Nothing changed on the Android side.
Only I changed from my old laptop with Ubuntu 20.04.3 to my new laptop with 22.04.2.

---

### Post by Roland_Msl on 2023-07-23
> **tea for one said:**
> That's a bit disappointing.
When these odd events happen to me, I often boot up a “Try Ubuntu” live session to test.
Using 22.04 live, I can see and “open in terminal” both internal storage and SD card.
```
ubuntu@ubuntu:/run/user/999/gvfs/mtp:host=motorola_moto_g_7__plus_ZY225D2H5D/SD card$ 
```
Perhaps, try a live session or double check all the Android settings?

I purchased 2 Lenovo Thinkpad L14 Gen 2. One for me, one for my daughter Johanna.
I installed on both Ubuntu 22.04.2

I just connected my Redmi 6 to the other Thinkpad.

Surprise! Left click on the folder in “Files” and there is as usual the “Open in a terminal”.

I installed on both with a list of what to install. No idea, where the difference is.

---

