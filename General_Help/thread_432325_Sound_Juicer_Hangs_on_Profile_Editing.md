---
title: "Sound Juicer Hangs on Profile Editing"
date: 2007-05-03
forum: General Help
---

### Post by skathrein on 2007-05-03
I've seen some previous posts on this and it may just be a bug, but haven't found a definite resolution.  Can anyone help?  Here's the problem:

If I go to Sound Juicer-->Edit-->Preferences-->Edit Profiles

At this point, I can choose something such as "CD Quality, Lossy" or "CD Quality, MP3" and click Edit.  No matter what I choose, it will pull up the next window where you can edit the pipeline and other things, however, I can change nothing on this screen and can no longer close any of the sound juicer windows.  Sound juicer basically freezes and can only be closed through a force quit.  Am I missing something?

---

### Post by vaskark on 2007-05-03
I've experienced the same problem. For a workaround just open 'gnome-audio-profiles-properties' from the CLI. It doesn't freeze doing it this way, at least for me.

---

### Post by mulvila on 2007-05-05
My problem may not be related, but it seems my gnome-media all sound profiles have been somehow misplaced. This happned when updating to Edgy and remains afer a fresh install of Feisty (with old settings, though).

Would someone know where the gnome-media sound profiles such *** ogg and waw are located and how I could reset the defaults? Reinstalling the packages do not help.

Currenlty both sound-juicer and sound recoder are affected and do not work. No profiles come up in the menu.

---

### Post by ahaslam on 2007-05-06
> **vaskark said:**
> I've experienced the same problem. For a workaround just open 'gnome-audio-profiles-properties' from the CLI. It doesn't freeze doing it this way, at least for me.

Do your profiles show up in Sound Juicer & Recorder? Only a few of the defaults appear for me & custom profiles are nowhere to be seen.

---

### Post by laidback on 2007-05-06
> **vaskark said:**
> I've experienced the same problem. For a workaround just open 'gnome-audio-profiles-properties' from the CLI. It doesn't freeze doing it this way, at least for me.

Worked for me as well, many thanks.

---

### Post by ebash on 2007-05-06
I think that this is a bug with Sound Juicer, anyhow I have found a workaround. 

If you notice carefully before you can edit a profile, you will be presented with a small dialog named "Edit GNOME Audio Profiles" that shows you the existing profiles. That dialog will then open a new dialog named "Editing profile (...)", this new dialog will seem as frozen. 

In order to fix this, cycle through the existing windows of sound juicer and find the previous dialog "Edit GNOME Audio Profiles" and close it. Sound Juicer should be responsive again and you should be able to edit the sound profile.

---

### Post by mulvila on 2007-05-06
> **Anthony Haslam said:**
> Do your profiles show up in Sound Juicer & Recorder? Only a few of the defaults appear for me & custom profiles are nowhere to be seen.

The trouble started with upgrade to Edgy some 6 months back and I did not attend to it then. Now there was some MP3 profile but I deleted all and tried to start afresth, but none of the lines I have found in various forum work. 

It seems the audio profiles are stocked somewhere in  :~/.gconf/system/gstreamer directory. This is where I am stuck.

Otherwise sound works, so it is not a big issue. I was just in a mood to rip some more CDs and had found sound-juicer handy programme. Now using GRIP.

---

### Post by ricardisimo on 2007-05-22
ebash hits the nail on the head above... a second dialog opens and is active, but in the background. Close it and you're good. Annoying beyond belief.

---

