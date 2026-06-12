---
title: "Changing partitions using Gparted"
date: 2007-07-27
forum: General Help
---

### Post by Ozor Mox on 2007-07-27
I have an external hard drive and I'd like to do something with it that I haven't done before. It is 250 GB and is formatted as ext3, and contains a backup of my main folder totalling 25.1 GB. I want to change it from

```
|--------------ext3-----------------|
```

to

```
|---------ext3-------| |--fat32---|
```

using Gparted so that I can temporarily backup some files from a Windows computer to the compatible partition while it is formatted. Once the files are copied back, I want to delete the partition and make the whole thing ext3 again?

Is this possible with Gparted, and am I likely to mess up whatever is on the ext3 partition by messing around with its size or will it remain untouched?

---

### Post by merlinus on 2007-07-27
If you install the ifs drivers, you can write from windows to ext3 with no problems.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

-merlin

---

### Post by mikewhatever on 2007-07-27
You should be able to resize the ext3 partition and create the FAT32, but there is a better solution for your particular purpose. Install [fs-driver]("http://www.fs-driver.org/") and you'd be able to copy stuff from windows to ext3.

---

### Post by Ozor Mox on 2007-07-27
Thanks I will do that instead :)

---

