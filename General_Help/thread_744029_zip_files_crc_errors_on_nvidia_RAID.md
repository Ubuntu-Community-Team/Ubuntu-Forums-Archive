---
title: "zip files crc errors on nvidia RAID"
date: 2008-04-03
forum: General Help
---

### Post by raharsha on 2008-04-03
Hi,

I am a long time ubuntu user. I recently installed Gutsy on a machine having Nvidia RAID using the instructions found at [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) . Everything is working fine except zip files. I get random CRC errors in them. This happens with zip, jar, tar, etc. i.e. any kind of compressed files. I tried searching the forums in vain. I tried to isolate the problem, but it happens randomly. 2 out of 3 times, I can successfully create zip file and test it with unzip -t to check for CRC errors. When we are dealing with a lot of zip and jar files, this creates a problem because of these random failures. Please help me. 

Thanks
Harsha

---

### Post by raharsha on 2008-04-03
I see the following logs in the /var/log/messages file

Apr  3 09:38:28 user kernel: [   38.890375] sda: rw=0, want=371149706, limit=312581808
Apr  3 09:38:28 user kernel: [   38.890377] attempt to access beyond end of device

---

