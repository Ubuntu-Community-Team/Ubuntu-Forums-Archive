---
title: "Thunderbird 2 upgrade nothing works now"
date: 2007-07-11
forum: General Help
---

### Post by ibob on 2007-07-11
Hi,

I have followed the instructions on the wiki here to upgrade Thunderbird 1.5 to Thunderbird 2. [https://wiki.ubuntu.com/ThunderbirdNewVersion](https://wiki.ubuntu.com/ThunderbirdNewVersion).   Now neither the old or new Thunderbird will start and I really need to get my emails back:

Here is what I get then trying to launch thunderbird: 

james@james-ubuntu-laptop$ mozilla-thunderbird
run-mozilla.sh: Cannot execute /opt/thunderbird/mozilla-thunderbird-bin.
james@james-ubuntu-laptop$ 

Can anyone tell me how to reverse the steps? which were:
sudo dpkg-divert --divert /usr/bin/mozilla-thunderbird.ubuntu --rename /usr/bin/mozilla-thunderbird 
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/mozilla-thunderbird
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird

Thanks,

James

---

### Post by ibob on 2007-07-11
HI,

I have sorted this problem. Just to confirm what steps I took to reverse the instructions.  I deleted the softlinks to the software and removed the dpkd-divert using the command:

sudo dpkg-divert --rename --remove /usr/bin/mozilla-thunderbird

This sorted the whole problem.
Yours,

James

---

