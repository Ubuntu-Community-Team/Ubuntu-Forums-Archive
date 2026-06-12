---
title: "No package header"
date: 2013-02-19
forum: General Help
---

### Post by cabinetman on 2013-02-19
After running  sudo apt-get install -f
I get this

 Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

Ubuntu 12.04

---

### Post by schragge on 2013-02-19
```

sudo rm var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multive*
sudo apt-get update

```

---

### Post by 2F4U on 2013-02-19
Solution to this problem can be found here:
[http://www.ihaveapc.com/2011/05/how-to-fix-problem-with-mergelist-varlibaptlists-error-in-ubuntu-11-04/](http://www.ihaveapc.com/2011/05/how-to-fix-problem-with-mergelist-varlibaptlists-error-in-ubuntu-11-04/)
[http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)

---

### Post by cabinetman on 2013-02-19
> **schragge said:**
> ```

sudo rm var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multive*
sudo apt-get update

```

Thanks for you reply
I got 
 cannot remove `var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multive*': No such file or directory

But this worked 
[http://www.ihaveapc.com/2011/05/how-to-fix-problem-with-mergelist-varlibaptlists-error-in-ubuntu-11-04/](http://www.ihaveapc.com/2011/05/how-to-fix-problem-with-mergelist-varlibaptlists-error-in-ubuntu-11-04/)

---

### Post by cabinetman on 2013-02-19
> **2F4U said:**
> Solution to this problem can be found here:
[http://www.ihaveapc.com/2011/05/how-to-fix-problem-with-mergelist-varlibaptlists-error-in-ubuntu-11-04/](http://www.ihaveapc.com/2011/05/how-to-fix-problem-with-mergelist-varlibaptlists-error-in-ubuntu-11-04/)
[http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)

Thank you it worked.

---

