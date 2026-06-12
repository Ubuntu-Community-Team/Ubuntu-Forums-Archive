---
title: "Xubuntu laptop suddenly crashing even after reinstall"
date: 2017-07-27
forum: General Help
---

### Post by A3M0N on 2017-07-27
I bought a new laptop for work back in March. I backed up the Windows installation then installed Xubuntu. Its been running great until 2 days ago. 

The mouse pointer started to move very choppy then the system became unresponsive. I manually rebooted it and was kicked to the BusyBox prompt where I had to run fsck (countless times now). After that it kept on crashing, but would lose things like recent changes to panel configs or saved passwords after getting back into the system. One thing that was strange is that I had to log into Chrome everytime like it was the first time I ran it again. And my home directory permissions got screwed up pretty good, but got that taken care of. Eventually I could only boot to the Grub prompt, so I ran from a live USB and saw that my root partition was so messed up that GParted couldn't tell what filesystem it was. I got fsck to run on it again and got it back, but decided it was time for a reinstall. So I saved/backed up my documents and reinstalled.

I added my user packages one at a time, hoping to find the culprit, but couldn't figure it out. Now after the 3rd reinstall, I'm at a loss and need help! 

OS: Xubuntu 16.04.2
Model: Dell Inspiron i5765
PROC: AMD A9
Graphics: Radeon R5
8GB RAM / 1 TB HDD

Despite being a Linux user for years, I'm not sure how to output my system log or which one may be needed for troubleshooting. 

Thanks for any help! I really don't want to admit defeat and have to go back to Windows to get work done. Really, really, don't want that.

---

### Post by A3M0N on 2017-07-28
So I ran the Xubuntu 17.04 liveusb and it worked great. I had some work to do so I just used it for a few hours. Then I decided to go ahead and install it, the system crashed while trying to copy data to the hard drive. 

I need an operational computer for work, so I restored the Windows 10 image and it's working just fine. I really don't want to keep using it though. Maybe an update doesn't jive with the HDD and it can't write to it? The hardware definitely isn't faulty, it's gotta be something within Xubuntu. Any ideas on how to find out what?

---

