---
title: "Manage Nexus 6 as Media Device"
date: 2015-02-01
forum: General Help
---

### Post by bp10 on 2015-02-01
I have searched, tried many different ways to get this to work but I cannot get my Kubuntu 14.04 system to recognize my Nexus 6 as a media device.  It mounts with MTP just fine, I can manually transfer files, but the OS and the media players never see it as a media device.  I added .is_audio_device with different variations of content.  Added an audio file to my music directory.  I am at a loss.

Is there a way to do this, or are my choices to painfully manage it, or use Windows?  If you need information on my system, or config I will post as quickly as I can.  Thanks in advance.

---

### Post by TheFu on 2015-02-01
The Nexus line is limited to MTP. This is because the Android OS has the partitions mounted and as long as that is the case (which means android is booted), MTP is it.

I have a Nexus4.  If it had an external SDHC slot, then that storage could be managed like USB storage. Alas, google sucks and doesn't want us having external storage.

---

### Post by bp10 on 2015-02-01
Yes, actually all Android devices are but they can still be viewed as Media Devices.  Windows can, and automatically does.  MTP is how it is mounted to the system, I need the system to realize this is a Media Device.

---

### Post by TheFu on 2015-02-01
I haven't looked recently, but there is something in the settings which determines if it is treated like a camera or not. Could that be the setting?
Not near the nexus to check now, it's on the the other side of the compound. ;)

---

### Post by bp10 on 2015-02-01
Are you talking about where you can choose MTP vs PTP?  It is set to MTP, not the camera mode.

---

### Post by PhilGil on 2015-02-01
Do you need to do something with your Android device (such as syncing playlists) that require you to connect it as a media device? I've always found it easier to use [AirDroid]("https://play.google.com/store/apps/details?id=com.sand.airdroid&hl=en") or USB debugging to transfer media files back and forth. Using MTP just adds another layer of (in many cases) unnecessary complexity.

---

### Post by bp10 on 2015-02-02
Airdroid for me is a bandaid.  I should plug the phone in, have it recognized as a media player and have Banshee, Amarok, Clementine or any other music manager program see the device and be able to manage the music on my Nexus 6.  It works perfect on Windows, which is sad but not on Ubuntu.

I don't mind some work to make things go, but so far I can't seem to find what Ubuntu needs to see this as a Media Player.

---

### Post by TheFu on 2015-02-02
I use DLNA to handle that. Lots of DLNA apps in the store.
Don't have Windows working with DLNA - tried - never worked well.

---

