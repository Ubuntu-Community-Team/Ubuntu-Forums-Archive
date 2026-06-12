---
title: "Strange error in apt-get update even using the default sources.list"
date: 2019-07-31
forum: General Help
---

### Post by jiang765 on 2019-07-31
I am using Unbuntu 16.04 LTS. Here is what my terminal shows:

```

$ sudo apt-get update

Hit:1 http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu xenial InRelease
Hit:2 http://archive.ubuntu.com/ubuntu xenial InRelease  
Hit:3 http://archive.ubuntu.com/ubuntu xenial-security InRelease
Hit:4 http://archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:5 http://packages.ros.org/ros/ubuntu xenial InRelease                   
Reading package lists... Done
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease  Unable to find expected entry 'http://us.archive.ubuntu.com/ubuntu//source/Sources' in Release file (Wrong sources.list entry or malformed file)
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Here is my sources.list:
```

###### Ubuntu Main Repos
deb http://archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse

###### Ubuntu Update Repos
deb http://archive.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse

```

No matter how I change the sources.list, even using the default sources.list, the same error always exists.

Hope someone can save me! 

Thank you very much!

---

### Post by Bashing-om on 2019-08-01
jiang765; Hello

Check the 3rd party directory ? /etc/apt/sources.list.d/

Maybe the malformation is there ?

Also check that there is not a malformed entry for foreign-architectures.
```

dpkg --print-foreign-architectures

```

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

