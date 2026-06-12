---
title: "X Server Won't Start"
date: 2007-04-12
forum: General Help
---

### Post by cmat on 2007-04-12
My X Server won't start up. I've searched the forum and no results were able to resolve the problem. Google was no help either.

This is the error: "Failed to start the X server (your graphical interface). It's likely that likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

The bottom line of the error: "Fatal server error: no screens found"

Here's the catch, my system is on a wireless. It will not connect automatically to the network. There is absolutely no way it can gain internet access (as far as I know). Unless, we can get it working through command line if not  -  no apt-get. I'm using Ubuntu 7.04, it worked fine until last night after I installed updates. Not all of them were downloaded and installed though as my network went down. I installed what downloaded. That is the only thing that I can figure out that contributed to this problem. 

Anyways, I have lots of critical work to do and I'm using another computer right now. That system needs to be working as best it can, or it's back to Windows (I really don't want to do that). I am officially stuck and I need help, all I do can access it the command line.

- thank you

---

### Post by Captain Slack on 2007-04-12
I had the same problem after the updates last night.  Everything was working fine up until that point.  

I'd been in X and Switched User so my wife could so something in her account.  When I logged her out, I got a black screen with a mouse pointer.  Restarting the X-server gave me the same error you got.  Rebooting didn't help.

---

### Post by ZombiekE on 2007-04-13
> **Captain Slack said:**
> I had the same problem after the updates last night.  Everything was working fine up until that point.  

I'd been in X and Switched User so my wife could so something in her account.  When I logged her out, I got a black screen with a mouse pointer.  Restarting the X-server gave me the same error you got.  Rebooting didn't help.

I think we are on the same boat. Could you check if [my thread]("http://ubuntuforums.org/showthread.php?t=408349") sounds like the same problem? I was blaming automatix (ntfs), but maybe it was due to some update. I have linked back to this thread just in case it helps somebody help us :).

---

