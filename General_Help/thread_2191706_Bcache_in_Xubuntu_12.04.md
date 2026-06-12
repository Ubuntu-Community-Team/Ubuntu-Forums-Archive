---
title: "Bcache in Xubuntu 12.04"
date: 2013-12-04
forum: General Help
---

### Post by dannyboy79 on 2013-12-04
I am attempting to install bcache-tools in Xubuntu 12.04.3. I know I need kernel 3.10 or later so I am already running that kernel but when I try to add the ppa for the bcache-tools software to convert my root filesystem to bcache I get the following errors
sudo add-apt-repository ppa:g2p/storage && sudo apt-get update
```
W: Failed to fetch http://ppa.launchpad.net/g2p/storage/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/g2p/storage/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/g2p/storage/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```
So it appears like these packages may not be available for precise, is there anyway to install these packages in precise? Later on in this guide [https://github.com/g2p/blocks](https://github.com/g2p/blocks) it suggests using raring but I want to stick with an LTS release which is currently 12.04. 

Any help would be appreciated as I'd really like to try out bcache with my ocz synapse caching ssd to cache either my / or /home partitions

---

### Post by dannyboy79 on 2013-12-06
bump

---

### Post by dannyboy79 on 2013-12-08
well, since i was having issues running 3.10 kernel in xubuntu, weird controller mapping issues etc etc, and the fact that bcache ppa doesn't exist for Precise, i gave up trying to get bcache working. I instead went with flashcache ([http://ubuntuforums.org/showthread.php?t=2179297](http://ubuntuforums.org/showthread.php?t=2179297)), to cache my entire /home partition and let me say, IT'S AWESOME! Here's some initial write tests using dd
```
time sh -c "dd if=/dev/zero of=/home/ubu/test.tmp bs=4k count=1000000 && sync"
```
1000000+0 records in
1000000+0 records out
4096000000 bytes (4.1 GB) copied, 9.34889 s, **438 MB/s**

and writing to my / partition 
```
time sh -c "dd if=/dev/zero of=/test.tmp bs=4k count=1000000 && sync"
```
1000000+0 records in
1000000+0 records out
4096000000 bytes (4.1 GB) copied, 56.8478 s, 72.1 MB/s

I'm very impressed with flashcache and my OCZ Synapse cache ssd.

---

