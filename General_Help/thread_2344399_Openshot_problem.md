---
title: "Openshot problem"
date: 2016-11-25
forum: General Help
---

### Post by satimis on 2016-11-25
Host - Ubuntu 16.04
Guest - Ubuntu 14.04
OpenShot 1.4.3 (running on Guest)
blender 2.76.b+dfsg0

Edit -> Preference 
Blender Executable - blender

Title -> New Animated Tile

Start "Animated Title Editor"
-> Choose a Template

The template doesn't show up on the frame, only a black screen.

Please advise how to fix the problem.  Thanks

regards
satimis

---

### Post by yancek on 2016-11-25
When I go to Select a Template, I get a pop-up indicating blender needs to be installed because I don't have it installed.  It also indicates the path to blender needs to be in the Blender Executable text box under Preferences.  If you have that done, I'm not sure what else to suggest.

---

### Post by satimis on 2016-11-25
> **yancek said:**
> When I go to Select a Template, I get a pop-up indicating blender needs to be installed because I don't have it installed.  It also indicates the path to blender needs to be in the Blender Executable text box under Preferences.  If you have that done, I'm not sure what else to suggest.
Hi,

Thanks for your response.

I solved the problem with following steps

1) Remove openshot ran
sudo apt-get purge --auto-remove openshot

2) According to following link;
[https://www.linuxforum.com/threads/openshot-video-editor-2-1.2193/](https://www.linuxforum.com/threads/openshot-video-editor-2-1.2193/)

performed following steps:
sudo add-apt-repository ppa:openshot.developers/ppa
sudo apt-get update
sudo apt-get install openshot-qt

Now OpenShot is running with Animated Title working.  But rendering is very slow, taking long time without much progress.

Guest Setting:
Base Memory - 13272 MB/32768 MB (32G RAM onboard)
4 cores (This is a 8 core machine)
Video Memory 64MB (128MB total)

satimis

---

