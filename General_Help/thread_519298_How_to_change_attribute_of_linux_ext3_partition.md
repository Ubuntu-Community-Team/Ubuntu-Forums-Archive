---
title: "How to change attribute of linux ext3 partition?"
date: 2007-08-06
forum: General Help
---

### Post by chunchengch on 2007-08-06
I modified my /etc/fstab to make a ext3 partition (/dev/sda5) with user privilege instead of root privilege, however, it is always with the root privilege, [COLOR="Red"]so I can not copy/erase files or directories by drag-and-drop[/COLOR], would someone please tell me how to change the attribute of this ext3 partition (/dev/sda5)? thanks a lot!


proc /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=f922bb42-5f35-4a01-afa2-cc8b4425eb91 / ext3 defaults,errors=remount-ro 0 1

# Entry for /dev/sda5 :
[COLOR="Red"]**UUID=e353c52d-a9f2-447c-b172-9ab11aec8bdc /media/sda5 ext3 user,rw,sync 0 1**[/COLOR]

---

### Post by merlinus on 2007-08-06
For read-write-execute privileges:

```

sudo chmod -R 775 /media/sda5

```-merlin

---

