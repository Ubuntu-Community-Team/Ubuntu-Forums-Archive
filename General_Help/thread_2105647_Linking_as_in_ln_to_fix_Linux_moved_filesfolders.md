---
title: "Linking as in ln to fix Linux moved files/folders"
date: 2013-01-16
forum: General Help
---

### Post by Mark_in_Hollywood on 2013-01-16
Precise Pangolin ver. 12.04 LTS.

I found what may be a fix for a problem I'm having with a tv tuner. While I'm not a command line scaredy-cat, I am having some qualms about the fix I see. That's on page 17 of a forum post, viz.:

[Linux DVB driver = success]("http://www.silicondust.com/forum/viewtopic.php?t=9153&postdays=0&postorder=asc&start=240")

There the discussion revolves around folders and files that were moved to new locations or reverting to an earlier version than the current one. For me that is: uname -r returns: 3.2.0-35-generic-pae.

To complicate my problem even more, I'm not sure why DVB matters. I live in the US and have ATSC. So if you know all the tech terms, you know what I mean by complicate. The network manager/tools cannot locate the device. 

Can someone knowledgeable about the moving of the video drivers from one folder to another guess when the fix would be put right? I would rather update than mess with existing files myself. And once the fix is in, what happens to the code if I do edit my OS? Will the two come to conflict with each other? And if you can, would what has happened to these files cause the tuner, which connects to the computer via ethernet cable, to be not found by the OS?

As for reverting to a working version of the kernel: Some years ago, my video card went bad. My motherboard had an internal video and rather than do without for two weeks while EVGA inspected and sent a new card, I switched the BIOS to internal video. Once that was done, GRUB would not show at boot time. With some help, these forums, I was able to fix that. But once the video card was re-installed, GRUB would no longer change back to the screen where modifications and reversions can be seen. So that's not a good option for me.

Lastly, I don't understand whether, if I were to make the edits if that means 

1 - uninstalling the MythTV packages I have installed.
2 - making the command line changes
3 - re-installing the MythTV packages

because I don't yet have the files/folders that MythTV is supposed to install because the kernel maintainers have moved stuff about.

Even attempting to install the dkms packages returns:

ERROR: Module dvb_hdhomerun does not exist in /proc/modules 
ERROR: Module dvb_hdhomerun_fe does not exist in /proc/modules 
ERROR: Module dvb_hdhomerun_core does not exist in /proc/modules

so I'm very, very confused as to how to proceed. Or even if to proceed. 

By example: 

mark@Lexington-19:~$ grep -i dvb /var/log/messages
grep: /var/log/messages: No such file or directory

Thank you for your time in reading about this mess.

---

