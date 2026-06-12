---
title: "unable to mount windows partitions any longer"
date: 2008-02-05
forum: General Help
---

### Post by SBFC on 2008-02-05
Hello everyone. I recently replaced all of my hardware save my drives and graphics card. I just noticed that I am no longer able to mount my windows partitions.The entries are still in my fstab file...

```

# /dev/sda1
UUID=20F43F37F43F0F12 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=F4582FAE582F6F14 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=FE18D7B818D76E61 /media/sda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

```

But when I run 'sudo mount -a' I receive the following:

```

Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0


```

Not sure what the difference between ntfs and ntfs-3g is...and I don't want to do anything til I have a better understanding for fear I will damage the partitions.

Any help is greatly appreciated.

---

### Post by jan quark on 2008-02-05
ntfs-3g is a driver to be able to read and write to ntfs formated partitions

[http://www.ntfs-3g.org/index.html](http://www.ntfs-3g.org/index.html)

do you have a dual boot with windows?

f yes try to boot into windows and shutdown safely, making sure there are no error warnings in winows

---

### Post by SBFC on 2008-02-05
Thanks a lot! Apparently Windows didn't have a clean shutdown process...I had no idea that would lock up the partitions like that.

---

