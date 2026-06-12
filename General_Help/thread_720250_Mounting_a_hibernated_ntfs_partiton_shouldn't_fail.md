---
title: "Mounting a hibernated ntfs partiton shouldn't fail!"
date: 2008-03-10
forum: General Help
---

### Post by mahy on 2008-03-10
Hi y'all,

this has been a bit of nuissance to me for some time already. I UNDERSTAND that ntfs-3g CANNOT mount a ntfs partition with hibernated Windows in r/w mode. That's prefectly OK. However, why should it fail completely? Why on Earth it can't simply mount the partition in read-only mode as an automatic fallback?? Read-only access is still far better than no access at all. Nowadays, i have to manually execute command 

```
mount -r -t ntfs /dev/sda1 /media/sda1
```

whenever i leave my windows hibernated. All i ask for is this command to be executed automatically at boot time as soon as the mounting utility discovers that windows is hibernated.

I sincerely hope this feature will be introduced in future releases of Ubuntu.

---

### Post by Rocket2DMn on 2008-03-10
Is the drive listed in your fstab file?  Post it here
```
cat /etc/fstab
sudo fdisk -l
```

---

