---
title: "VirtualBox running XP and Videora problem"
date: 2007-11-07
forum: General Help
---

### Post by Metallinut on 2007-11-07
I posted this in the VirtualBox forums, but thought I'd try my luck here, in case anyone has seen anything similar...

I ran a few searches here, but couldn't find an answer. I'm running an XP guest box inside Ubuntu 7.10 Gutsy. Here's how I've got it set up.

There's a folder in my home directory called Videos (~/Videos). I've shared this folder with the guest machine (XP). I've mapped the V: drive to this shared folder, and that works great...I can create and delete files in this directory to my heart's content from the guest.

So I put an .avi video file in the directory, and open up Videora on the guest. I tell Videora that I want to convert V:\original\video.avi into the new file V:\converted\video.mp4

It all seems to start ok, but as soon as my VirtualBox window loses focus (e.g. I go to check mail on the host machine) then Videora stops converting. It does not freeze, nor does the guest system...it just ceases to complete the conversion.

Now for the funky part. If I move the original video.avi file to the C: drive on the guest machine, and the output file also goes to the C: drive, then Videora works like a champ, whether the VirtualBox window has focus or not.

So it seems that there may be some issue of VirtualBox reading/writing to the shared folder on the host system, when VirtualBox is not the focused window.

Does this make sense? Is there any way I can fix this? I'd rather keep all my video files OFF the guest machine's virtual disk...

Thanks,

[Edit]
After some testing I think I figured out where the problem lies. If I have the source video.avi file on C: of the guest machine, and try to put the output out to V:\converted (shared directory) it craps out, leaving me to believe the problem lies in how the guest is trying to WRITE to the shared directory. Conversely, if I have the source video.avi file on the V: drive (shared directory), and the output goes to the C: drive on the guest, it works flawlessly.

So it appears that there is some issue in how the guest is writing to the shared directory, once the VirtualBox window loses focus...

---

