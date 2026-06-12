---
title: "Gnome-Schedule on 16.04"
date: 2016-05-17
forum: General Help
---

### Post by b18b on 2016-05-17
Has anyone successfully installed gnome-schedule on 16.04?  There are missing python dependencies that I cannot get around.

Thanks.

---

### Post by krash1220 on 2016-07-20
Download python-support_1.0.15_all.deb  from [https://launchpad.net/ubuntu/xenial/+package/python-support](https://launchpad.net/ubuntu/xenial/+package/python-support) and gnome-schedule_2.1.1-4_all.deb from [http://packages.ubuntu.com/wily/all/gnome-schedule/download](http://packages.ubuntu.com/wily/all/gnome-schedule/download). Install python-support first and then gnome-schedule.

Also if you install gebi it will install deb files for you and download and install dependencies as well.

---

### Post by mcman56 on 2017-04-13
python-support_1.0.15_all.deb is no longer at that location.  It shows as deleted. I downloaded synaptic package manager. "sudo apt install synaptic".  This then allowed me to load python-support and gnome-schedule.  It also automatically loaded some other dependencies.  All works well.  Under system tools, it shows up as Scheduled Tasks.

---

