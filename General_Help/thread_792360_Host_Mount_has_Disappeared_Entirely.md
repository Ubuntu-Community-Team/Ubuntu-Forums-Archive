---
title: "Host Mount has Disappeared Entirely"
date: 2008-05-12
forum: General Help
---

### Post by CovertJaguar on 2008-05-12
I seem to have an odd problem. My "/host" folder has disappeared. I used to be able to access my window's files through "/host", but now it is not there anymore. I'm not sure what caused it. I recently expanded the size of my root.disk using LVPM, I'm not sure if that could have caused it. Additionally, I also installed truecrypt. I'm not sure if either of these things had anything to do with the disappearance of "/host", but I thought I would mention them.

---

### Post by ago on 2008-05-14
Well you can check in /proc/mounts to see what is actually being used.

---

### Post by CovertJaguar on 2008-05-18
/dev/sda2 /host fuseblk rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other 0 0

---

### Post by ago on 2008-05-18
note that lvpm does not support 8.04 yet. Anyway it looks like /host is mounted.

---

### Post by CovertJaguar on 2008-05-18
Mounted or not, I cannot access it.

---

### Post by ago on 2008-05-19
I am not sure what is the behavior of LVPM at the moment. Did you run it on wubi 8.04? 

You can boot with break=init (that will give you a prompt) and check the status in early boot stages.

---

