---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2016-05-20
forum: General Help
---

### Post by abcuser on 2016-05-20
On Ubuntu 14.04 LTS I have executed the following command:
```
sudo apt-get update && sudo apt-get -y dist-upgrade
```
I am updating the system in this way year after year without a problem. But now bellow error appears:
```

Reading package lists... Done                                                  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  binutils
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/2120 kB of archives.
After this operation, 8192 B of additional disk space will be used.
(Reading database ... 432747 files and directories currently installed.)
Preparing to unpack .../binutils_2.24-5ubuntu14.1_i386.deb ...
Unpacking binutils (2.24-5ubuntu14.1) over (2.24-5ubuntu14) ...
dpkg: error processing archive /var/cache/apt/archives/binutils_2.24-5ubuntu14.1_i386.deb (--unpack):
 unable to install new version of `/usr/bin/c++filt': Device or resource busy
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/binutils_2.24-5ubuntu14.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have check the web for several solutions but non of it is exactly like mine.
I have had some PPAs installed (I remove them, because no longer needed), but problem still is not solved.

Any idea how to fix this problem?

---

### Post by user1397 on 2016-05-20
Have you tried running ```
sudo apt-get -f install
```

Just as random maintenance, I would also run:
```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by abcuser on 2016-05-20
Already tried that and tried it now again and does not help. The same error.

---

### Post by user1397 on 2016-05-20
Are you running multiple package management apps at once?  Like software center, synaptic, apt-get inside a terminal, etc?

---

### Post by abcuser on 2016-05-21
@user1397, no I am not running multiple update software. Just for test I have started Synaptic and apt-get from terminal at the same time and there is different error in this case:
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
My problem from first post is not the problem above of having multiple package update software running at the same time.

Any other idea?

---

### Post by user1397 on 2016-05-21
Found this, may help: [http://askubuntu.com/questions/688338/e-sub-process-usr-bin-dpkg-returned-an-error-code-1-related-to-google-chrom](http://askubuntu.com/questions/688338/e-sub-process-usr-bin-dpkg-returned-an-error-code-1-related-to-google-chrom)

---

### Post by abcuser on 2016-05-21
@user1397, I have already tried that and several other tricks on the web, but non of them solves my problem always getting this "Device or resource busy" error when updating.

---

