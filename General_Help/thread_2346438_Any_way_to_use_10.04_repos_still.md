---
title: "Any way to use 10.04 repos still?"
date: 2016-12-14
forum: General Help
---

### Post by agrayray on 2016-12-14
I have a 10.04 virtual machine that I need to install a couple of utilities on like tree and so on...
I tried the usual change to archives trick in sources.list but it seems the archive addresses for 10.04 do not exist anymore...
Is there any url that does or is there a way to connect to a 10.04 repo for a cpl of installs?

PS - PLS dont harp on me to upgrade my Ubuntu...I have many VMs most all  on 16 etc...the VM in question tho is  a 32b development VM with all my  dev work on it since 2010..I just am looking for way to keep this VM  and install a cpl of programs I should have installed long ago...

THANKS IN ADVANCE!

---

### Post by kostkon on 2016-12-14
You need to point your sources.list to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) as described [here]("https://help.ubuntu.com/community/EOLUpgrades/#Update_sources.list"), in your case that would be:
```
deb http://old-releases.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
```

Don't forget to sudo apt-get update afterwards.

---

### Post by agrayray on 2016-12-15
I was using an incorrect url:  [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) .

Switching:
[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
  :to
[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)

Did the trick!  Thanks @Kostkon!

---

