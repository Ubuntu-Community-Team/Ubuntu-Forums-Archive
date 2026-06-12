---
title: "How to: Allow all users the ability to read/write to Internal HDD"
date: 2020-11-08
forum: General Help
---

### Post by dhavalbbhatt2 on 2020-11-08
Hello all,
I have an internal HDD that is separate from the main hard drive, that I am using to store data files. Other thing to note, my son and I, we share the computer from time to time, although, he uses it the most and does not log out (we typically just switch between users).

The issue for both of us is that, when he does not log out completely, I can't read/write to the internal HDD (the same is true when I don't log out and he tries to use the computer using his user ID by "switching" users).

The question then is, how do I ensure that we both (or any other user that we may decide to add later down the line) can read/write to the internal HDD without the other person logging out completely. I should also note that the drive does mount for both users (meaning, the OS does recognize the drive when either one of us logs in).

 I have the following entry in my /etc/fstab

LABEL=INTHDD /mnt/INTHDD auto nosuid,nodev,nofail,x-gvfs-show 0 0

Please let me know if any other information is required (I am using Ubuntu 20.04).

Thanks,
DB

---

### Post by SeijiSensei on 2020-11-08
Create a group for you and your son. Then make all the files readable/writable by the group. You can also set the "setgid" bit so that files written by either of you can be accessed by the other.

```
sudo addgroup family
sudo adduser dad family
sudo adduser son family
cd /mnt
sudo chmod -R g+rws INTHDD

```

---

