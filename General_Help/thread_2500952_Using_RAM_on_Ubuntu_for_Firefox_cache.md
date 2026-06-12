---
title: "Using RAM on Ubuntu for Firefox cache"
date: 2024-09-17
forum: General Help
---

### Post by ash92 on 2024-09-17
Hi,

I am using "Ubuntu 22.04.5 LTS". I want to use the RAM for cached files by Firefox browser (version 130.0 (64-bit)). I setup "*browser.cache.disk.parent_directory*" in Firefox to *"/run/user/1001"* but it didn't use it. Then I tried giving it a value "*/dev/shm"*, then also the size of cache is zero. What could be the reason. Is it a permissions issue. The User ID 1001 has permission to access both those directories AFAIK. The cache works if I don't set value for the *parent_directory* setting.
How can I get this to work? I didn't want to create a Ramdisk. Can I possibly use "*/run/user/1001*" or "*/dev/shm"* as temp space?

Regards
Amal

---

### Post by ActionParsnip on 2024-09-17
I've had a startup script that made a folder and chown'd it to my user, then a symlink for the browser cache to this folder. Worked OK. The folder creation needs adding to the startup because it live in RAM so is lost at power off.

---

### Post by ActionParsnip on 2024-09-17
Make the folder in
```

/tmp

```
(I assume you don't have /tmp mounted to a file system on your disk)

---

### Post by ash92 on 2024-09-17
Thanks for your prompt replies. **I don't think /tmp is mapped to RAM or any other writable directories except the two I mentioned**. Here is the output of *df -h*.
 
```

Filesystem              Size  Used Avail Use% Mounted on
tmpfs                  1.6G  3.0M  1.6G   1%     /run
efivarfs                438K  193K  241K  45%    /sys/firmware/efi/efivars
/dev/nvme0n1p3           460G  219G  218G  51%   /
tmpfs                   7.7G  2.5G  5.3G  33%     /dev/shm
tmpfs                   5.0M  4.0K  5.0M   1%      /run/lock
/dev/nvme0n1p1           896M   72M  825M   8%     /boot/efi
tmpfs                   1.6G  1.7M  1.6G   1%      /run/user/1001

```

I thought /dev/shm is a good option as it has over 5Gb RAM free. Even /run/user/1001 has 1.5 Gb free.

---

### Post by ActionParsnip on 2024-09-17
> **ash92 said:**
> Thanks for your prompt replies. **I don't think /tmp is mapped to RAM or any other writable directories except the two I mentioned**. Here is the output of *df -h*.
 
```

Filesystem              Size  Used Avail Use% Mounted on
tmpfs                  1.6G  3.0M  1.6G   1%     /run
efivarfs                438K  193K  241K  45%    /sys/firmware/efi/efivars
/dev/nvme0n1p3           460G  219G  218G  51%   /
tmpfs                   7.7G  2.5G  5.3G  33%     /dev/shm
tmpfs                   5.0M  4.0K  5.0M   1%      /run/lock
/dev/nvme0n1p1           896M   72M  825M   8%     /boot/efi
tmpfs                   1.6G  1.7M  1.6G   1%      /run/user/1001

```

I thought /dev/shm is a good option as it has over 5Gb RAM free. Even /run/user/1001 has 1.5 Gb free.

/run/user/1001/cache sounds sensible to me. You will need to make the folder after each boot.

---

