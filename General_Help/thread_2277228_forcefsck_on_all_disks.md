---
title: "forcefsck on all disks"
date: 2015-05-07
forum: General Help
---

### Post by zkab on 2015-05-07
I want a fschk done on all disks at reboot.
When I give  touch /forcefsck on / it will only check /dev/sda1 ... but what about the other disks ?

---

### Post by ajgreeny on 2015-05-07
Now that's an interesting question!

I don't know the answer, but just wanted to say, in case you are not aware, that you can run fsck on all partitions from a live DVD or USB, with command ```
sudo e2fsck /dev/sdx#
```and are thus able to choose any partition you want.

---

### Post by zkab on 2015-05-08
Yes - I am aware of that but the problem is that I don't get physical access to the server so easily ... that's why I want to do it with ssh.
Thanks for your input.

---

