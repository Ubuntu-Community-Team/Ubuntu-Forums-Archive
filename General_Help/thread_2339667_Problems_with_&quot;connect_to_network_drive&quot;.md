---
title: "Problems with &quot;connect to network drive&quot;"
date: 2016-10-11
forum: General Help
---

### Post by gde061-www on 2016-10-11
I had this same problem with 14.04 for many years - mounting a network drive from my local network smb server will throw various errors when trying to actually access the files.  This only happens when using the "connect to" in unity.  The drive is mounted.  It can be browsed.  But the file contents are not accessible - either to applications like Rythmbox or even base file operations like copy & paste.  The errors thrown are something like "Counldn't start playback (Null)".  

The work around I found for 14.04 was to have the drive mounted at startup, using some fstab config files that I already forgot how they work.  That system was an Edge E530 with the plain vanilla Ubuntu 14.04 LTS

Anyway, I recently started setting up a new machine for myself (a Thinkpad L560) with Mate 16.04 LTS.  It has the same exact behavior.  I cannot believe that I have more functional ability to map network resources to smb: server in Windows than I do in Linux.  I am about to get a new NAS and that will be the final step to debunking whether or not the issue is with my server... 

But I just felt like posting this information again - I think I posted the same question for the E530 - to see whether any progress has been made on finding a way to  dynamically map to network shares without having to set them up at startup.  My work-around has been to use FTP, which my NAS also supports.

---

