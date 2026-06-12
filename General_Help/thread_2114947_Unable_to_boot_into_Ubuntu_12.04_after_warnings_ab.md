---
title: "Unable to boot into Ubuntu 12.04 after warnings about the filesystem being read-only"
date: 2013-02-11
forum: General Help
---

### Post by drewnoakes on 2013-02-11
My Dell XPS15 laptop has Ubuntu alongside Win8 (using WUBI).

Earlier today my desktop started freezing up and things were misbehaving. I managed to shut down, restart and things looked ok. Since then, things have deteriorated and now I cannot boot into Ubuntu -- I just see a purple screen after some messages that flicker on the screen so quickly that I cannot read them.

I've booted into the Ubuntu 12.04 live CD but at this point am not sure what the best approach is. I am not that familiar with Linux filesystems.

I have attached the output of [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

All advice appreciated.

**EDIT** A more detailed output from BootInfo is available here: [http://paste.ubuntu.com/1637083/](http://paste.ubuntu.com/1637083/)

---

### Post by bcbc on 2013-02-11
I would start by running 'chkdsk /f' from Windows.
Then follow up with an fsck on the root.disk.

The order is important. Chkdsk first.

Do you need instructions for either of these?
1. Here's how to chkdsk: [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html) (just look at the bit about chkdsk since your root.disk isn't missing)
2. Here's how to fsck. Boot your live USB, mount the windows partition, then fsck the root.disk:
```
sudo mkdir /media/win
sudo mount /dev/sda3 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
```

---

### Post by drewnoakes on 2013-02-11
Thanks very much @bcbc,

A lot of errors were found and, apparently fixed. I'm pasting this here before I reboot and lose most of my state.

This is the complete output of the fsck operation:

[http://pastebin.com/ZfzwDq7V](http://pastebin.com/ZfzwDq7V)

Running fsck a second time shows no errors.

What's more I successfully mounted the Wubi root.disk file and can see my data in there. Phew!

```

sudo mkdir /media/win
sudo mount /dev/sda3 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
sudo mkdir /vdisk
sudo mount -o loop /media/win/ubuntu/disks/root.disk /vdisk
cd /vdisk
ls

```

Now I'll try to reboot...

---

### Post by drewnoakes on 2013-02-11
And it's working after the reboot. Thanks again, @bcbc. I really appreciate you taking the time to help me out with this. I hope others find this record useful in future too.

---

