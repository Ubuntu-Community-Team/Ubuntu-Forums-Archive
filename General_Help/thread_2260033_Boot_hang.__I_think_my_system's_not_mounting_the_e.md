---
title: "Boot hang.  I think my system's not mounting the encrypted partition correctly"
date: 2015-01-08
forum: General Help
---

### Post by Brent_Moran on 2015-01-08
Howdy.

Ubuntu 14.10 running on a Dell XPS 13.  I think everything's up-to-date.

I shutdown for a flight, and when I tried to boot my system at the other side, it's hanging while the dots scroll.  Pressing 'down' to see the console while it does this shows:
```

/scripts/local-top/cryptroot: line1: can't open/dev/mapper/ubuntu--vg-root: no such file

```
as the relevant error (I think).

Trying to boot in recovery mode shows:
```

/proc/self/fd/9: 3: /proc/self/fd/9: grep: Input/output error
plymouth: error while loading shared librariaes: libply.so.4: cannot open shared object file: Input/output error

```
as the relevant error.

Note that these code snippets are not copy-pasted, but recreated from pictures I took with my phone of the screent during boot.

Here's a link to the pics of the console screens at the respective hangs:

[http://imgur.com/a/dpN2R](http://imgur.com/a/dpN2R)

First is the screen when attempting to boot in recovery mode, the second is the attempt to boot in normal mode.

I can boot from my Ubuntu 14.10 usb just fine (currently am).  When booted from here, I can mount ubuntu--vg-root using cryptsetup, and all the usual files appear to be there.  I did some filesystem repair with fsck -a, but to no avail.

I suppose I could copy those and reinstall, but I really don't want to resetup my work environment, since I'm on the road right now.

Any help would be super awesome.

Thanks!

---

### Post by oldfred on 2015-01-08
I do not know encryption.
But my try a full e2fsck, I think fsck just sees if error flag has been set.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Brent_Moran on 2015-01-08
The output is:
```

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/mapper/ubuntu--vg-root 
                                                                               
      462842 inodes used (6.38%, out of 7249920)
         611 non-contiguous files (0.1%)
         752 non-contiguous directories (0.2%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 409935/236/1
     4735423 blocks used (16.34%, out of 28981248)
           0 bad blocks
           1 large file

      344799 regular files
       48099 directories
          57 character device files
          25 block device files
           0 fifos
        1208 links
       69850 symbolic links (52577 fast symbolic links)
           3 sockets
------------
      464041 files

```
This seems ok.  It didn't ask if I wanted to fix anything

---

### Post by oldfred on 2015-01-09
Not sure why it cannot find root in the LVM.

Since it is reporting inode issues, I would run the second e2fsck fix.

---

