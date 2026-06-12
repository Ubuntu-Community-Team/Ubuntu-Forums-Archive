---
title: "Resize root partition from live cd?"
date: 2006-10-13
forum: General Help
---

### Post by stiankarlsen on 2006-10-13
Okay, so I've been looking around the forums, however I haven't found a real answer to this question.

Here's my situation, I have a 200GB HD that has been parted into a swap partition, and the rest of it is ext3, with dapper installed on it. What I want to do is resize the ext3 partition, shrink it down to 20GB or something, and have my dapper installation on that, then I want to create a new partition out of the restoring space on the HD, and use it for storage and stuff like that.

My problem is that it seems I can't resize the partition when the OS is running on it, obviously. So what I'm wondering is, would it work/be safe to boot the computer with a live cd, and use Gparted to resize the disc, or would that mess up the OS in some way?

---

### Post by Kateikyoushi on 2006-10-13
You can do it from the live cd, and it won't mess up your install.
As always, backing up important data before you begin is a good idea.

---

### Post by galileon on 2006-10-13
ive done it loads of time, (im the kind to install loads of different distros to try out), and ive not had problems yet...but Kateikyoushi is right, backup first if you have any important data...

---

### Post by stiankarlsen on 2006-10-21
works like a charm, yes.

---

