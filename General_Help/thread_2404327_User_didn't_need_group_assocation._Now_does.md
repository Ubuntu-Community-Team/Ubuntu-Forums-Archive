---
title: "User didn't need group assocation. Now does?"
date: 2018-10-22
forum: General Help
---

### Post by Tadaen_Sylvermane on 2018-10-22
16.04 LTS, No HWE

My HTPC in the living room has a Kodi user that everything runs under. I have a script restart Kodi every morning early. The server is at 33 days and change uptime. Today when it restarted Kodi there was no sound. When I checked the settings, HDMI wasn't even an option. This has been working fine the whole 33 days till today. My kodi user was only a member of it's own group. On a hunch I added the user to the video and audio groups, restarted Kodi and everything was fine. Working right now perfectly.

TLDR. Why did pulseaudio work fine with the user not being in the audio group for 30+ days, only to stop working this morning, fixed by adding user to audio group?

---

