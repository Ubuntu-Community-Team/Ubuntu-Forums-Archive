---
title: "Filesystems tuning"
date: 2014-05-03
forum: General Help
---

### Post by sagsaw-sawant on 2014-05-03
What are the filesystem mount defaults for 14.04?

Its just mentions defaults in mtab/fstab.

Is relatime recommended? Does it break any programs like email clients and BACKUP?

What other tuning can be done for ext4 filesystem so that system startup and in general speed is increased?

---

### Post by cariboo on 2014-05-03
Seeing as this is a support question, moved to General Help.

---

### Post by Impavidus on 2014-05-04
According to **man fstab**```

              **defaults**
                     use default options: rw, suid, dev, exec,  auto,  nouser,
                     and async.
```
The ***atime** options can be used to reduce writes, which is useful on devices with low write speed compared to read speed or limited write cycles (like SSDs). Also, some applications may need it. Default options are fine most of the time, but I don't know your specific case. From **man mount**```
       **relatime**
              Update inode access times relative to  modify  or  change  time.
              Access time is only updated if the previous access time was ear&#8208;
              lier than the current modify or change time. (Similar  to  noat&#8208;
              ime,  but  doesn't break mutt or other applications that need to
              know if a file has been read since the last time  it  was  modi&#8208;
              fied.)

              Since Linux 2.6.30, the kernel defaults to the behavior provided
              by this option (unless noatime was  specified), and the stricta&#8208;
              time  option  is  required  to  obtain traditional semantics. In
              addition, since Linux 2.6.30, the file's  last  access  time  is
              always  updated  if  it  is more than 1 day old.
```So it seems default already.

---

### Post by sagsaw-sawant on 2014-05-05
@**I**[**[COLOR=#000000]mpavidus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1417721") ... Will chk and get  back ... so all the defaults rw, suid, dev, exec,  auto,  nouser,                      and async are included? I doubt about async

---

