---
title: "Mounting questions (loop and noload)"
date: 2016-05-30
forum: General Help
---

### Post by insane9 on 2016-05-30
Hi all,

I have a 10gb dd file which I tried mounting as read only. I used the following command:

```
sudo mount -o loop,noexec,ro file.dd /mnt/file
```

and it didn't work. I ran '```
dmesg | tail
```' and saw the following:

```
[ 3091.778058] EXT4-fs (loop1): write access unavailable, cannot proceed
[ 3184.711078] EXT4-fs (loop1): mounting ext3 file system using the ext4 subsystem
[ 3184.711673] EXT4-fs (loop1): mounted filesystem without journal. Opts: noload
```


So then, after a bit of google-fu, I managed to find out that I could use the 'noload' command. I used this:

```
sudo mount -o loop,noexec,**noload**,ro file.dd /mnt/file
```

and it loaded the filesystem to /mnt/file.

Can someone please answer the following:

1) What exactly does noload do in lamens terms? I read that it doesn't load the linux journal? What does that mean?
2) If I had both filesystems mounted and shut down my machine, would it corrupt the dd files? Am I best running umount /dev/loop0 after use?

Thanks!

---

