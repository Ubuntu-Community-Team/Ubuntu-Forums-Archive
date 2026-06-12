---
title: "Boot failure on Ubuntu 14.04"
date: 2014-07-18
forum: General Help
---

### Post by bencouve on 2014-07-18
Hi experts. 

I need help to re-boot my laptop. I have tried a few things but cannot seem to get this to work. This is what I have done so far.

sudo fdisk -lu
sudo mkdir /mnt/work
sudo mount /dev/sda1 /mnt/work
ls -la /mnt/work/boot  // This returned no data
sudo umount /mnt/work

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update && sudo apt-get install -y boot-repair && boot-repai
//this returned 
Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
and
ubuntu@ubuntu:~$ Boot-Repair
Boot-Repair: command not found

I have the iso on CD so can run from CD.

Please help. Thanks in advance.

---

### Post by kc1di on 2014-07-18
down load boot repair from [here.]("https://help.ubuntu.com/community/Boot-Repair")
remove the PPA it no longer works.

---

