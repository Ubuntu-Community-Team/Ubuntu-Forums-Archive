---
title: "Fresh server, slow write-speed"
date: 2018-11-05
forum: General Help
---

### Post by erickarlsso on 2018-11-05
Hi

Im running a small web/design-agency and have just purchased a rackserver (Dell R440 with 8gb ram, xeon bronze etc) for storing/sharing files, databases etc. We bought that service since it's certifed for Ubuntu ([https://certification.ubuntu.com/hardware/201709-25755/](https://certification.ubuntu.com/hardware/201709-25755/)) and it's scaling capabilities.

Now for the problem. Ive successfully installed Ubuntu and other stuff like Samba, Cups, SSH etc. But when i mount a shared folder on my macbook pro (via ethernet) and test read/write speeds i get on average 86,13Mbps write and 776,77 Mbps read speeds. However, when i ssh to the server and run ```
dd if=/dev/zero of=/srv/data1/example/testfile1 bs=8k count=10k
``` i get:

```

10240+0 poster in
10240+0 poster ut
83886080 byte (84 MB, 80 MiB) kopierade, 0,0501394 s, 1,7 GB/s

```

The network is built with cat6 cables and a gigabit switch and router. Everything else including a former "server" which is an old iMac Mini is working and the former server is so far way faster in terms of writing-speeds.

[B]Hardware:
[/B]
[LIST]
[*]SERVER | Dell EMC PowerEdge R440 (Xeon Silver, 8-cores, 16gb ram)
[*]OS DRIVE | 1x 600gb drive formatted as ext4 and mounted as / ([https://www.dell.com/sv-se/work/shop/accessories/apd/400-ajpe](https://www.dell.com/sv-se/work/shop/accessories/apd/400-ajpe))
[*]STORAGE DRIVES | 2x 2.4tb drives formatted as ext4 and mounted as /srv/data1 and /srv/data2 (non-raid) ([https://www.dell.com/sv-se/work/shop/accessories/apd/400-auvr](https://www.dell.com/sv-se/work/shop/accessories/apd/400-auvr))
[/LIST]


The installer went fine and likewise installning/configuring both Cups and Samba, which is both "working" except for the poor write-speeds. My own theory is that this has something to do with the storage-drives and the fact that they are SAS-disks, but i don't even know where to start looking for problems.

Im fairly new to the world of Linux, but im learning fast and i will try to post the logs, configs and stuff you require to help me.

---

### Post by mitesh.agrwl on 2018-11-08
Hi,

I am not an expert to the issue but had a feeling that it was related to network protocols rather than the system. Here is an article which might help you with the problem.

[https://www.helios.de/web/EN/news/AFP_vs_SMB-NFS.html](https://www.helios.de/web/EN/news/AFP_vs_SMB-NFS.html)

Hope this will help you to solve the problem.

---

### Post by TiberiusT on 2018-11-08
Do you have Windows clients using the server? If not, then use NFS instead of Samba [https://help.ubuntu.com/lts/serverguide/network-file-system.html](https://help.ubuntu.com/lts/serverguide/network-file-system.html)  For Unix OSs (Mac/Linux etc) NFS is simpler, more robust and faster than Samba. It's not that Samba is bad, its good, but NFS is better! You can run it concurrently with Samba on the server and then switch the client connection to test. You shud be getting a min reliable 100MBps throughput since this will be about the speed of the server's NIC, your 1GB network and the storage disks. 

Your write tests done locally on the server are fast because Linux  uses free RAM for caching so you are really just dumping data to RAM.  Good thread abt testing speeds here [https://askubuntu.com/questions/87035/how-to-check-hard-disk-performance](https://askubuntu.com/questions/87035/how-to-check-hard-disk-performance) .

I know nothing about Mac but I just found this [https://www.cyberciti.biz/faq/apple-mac-osx-nfs-mount-command-tutorial/](https://www.cyberciti.biz/faq/apple-mac-osx-nfs-mount-command-tutorial/) The one caveat with NFS is using it over wireless - it gets very upset with dropping connections!

 Lastly, I'd seriously also consider using ZFS instead of ext4 as the filesystem on your storage drives. [https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS) It's utterly awesome for SOHO installations. You can just set the sharenfs=on parameter and then you don't have to bother with /etc/exports and bind mounts etc

 Good luck! You've made the right decision - I've used Ubuntu Server for abt 8 years and it's been rock solid

 Rgds/T

---

