---
title: "How did this happened? =O"
date: 2013-05-02
forum: General Help
---

### Post by Juniorr on 2013-05-02
I was using openSUSE and switched to Ubuntu 12.04, ran some tests, installed graphics drivers and re-installed the system. Now, after a system update, Nvidia drivers were automatically installed (310-experimental). The steps I did were:

(At this stage openSUSE was installed)

* Delete partitions
* Create new partitions for the test install - 40GB for "/", 571GB for "/home"

Now with the test system installed

* Update system
* Install NVIDIA-310-Experimental
* reboot with the LiveCD and again delete and create new partitions, with the additional deletion of my home folder contents

Now, I installed the system again and for my surprise NVIDIA-310-Experimental was already installed after reboot. This bugs me because I've had problems with cfg files being re-used even after a fresh system install (you can read more about that [HERE]("https://forums.opensuse.org/english/get-technical-help-here/install-boot-login/486301-how-long-will-dd-take-1tb-drive.html#post2552680")).

---

