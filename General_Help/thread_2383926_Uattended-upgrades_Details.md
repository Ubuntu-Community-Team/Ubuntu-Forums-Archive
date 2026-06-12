---
title: "Uattended-upgrades Details"
date: 2018-01-31
forum: General Help
---

### Post by RogerDavis on 2018-01-31
I installed unattended-upgrades, but found major confusion in trying to work with it's intended purpose(s) and the setup files.

First, as long as Software Updater does it's job, I don't think I need anything but older kernel and related files removal. Is that correct?

I found huge difficulty in getting an understanding, line by line, of the setup files and contents. I got partway through, and found that I was unsure of what I had done. In particular it seemed that some of the lines authorized upgrades (e.g. like 16.04 to 17.04). I want to control those myself. So I used Symantic to fully remove what I had and reinstall the basic package. Afterward I ran dpkg-reconfigure --priority=low unattended-upgrades and nothing else. It's unclear if this is sufficient to deal with old kernels and associated files, or if I need to add at least "Unattended-Upgrade::Remove-Unused-Dependencies "true";" and if so, where?

Also, have I missed anything?

Is there a REALLY clear tutorial anywhere?  I've googled it, but not found anything that is as clear as I need it on these points.

Thanks!!!

---

### Post by vasa1 on 2018-01-31
See your post here: [https://ubuntuforums.org/showthread.php?t=2383285&p=13735666#post13735666](https://ubuntuforums.org/showthread.php?t=2383285&p=13735666#post13735666)

---

### Post by vasa1 on 2018-02-02
Reopened at OP's request.

---

