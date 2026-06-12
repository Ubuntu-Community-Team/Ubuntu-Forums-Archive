---
title: "cgroups v2 not throttling io as expected"
date: 2019-01-31
forum: General Help
---

### Post by sand7000 on 2019-01-31
On this page:

[https://facebookmicrosites.github.io/cgroup2/docs/io-controller.html](https://facebookmicrosites.github.io/cgroup2/docs/io-controller.html)

it says:
> 
cgroup1 accounts for and controls only direct IOs, i.e.,  filesystem metadata IOs (both read and write), and buffered reads. This  leaves other types of IOs, such as buffered IO (which is often the  majority in many use cases), unaccounted for and uncontrollable.
cgroup2 allows comprehensive control and accounting of **all**  IOs per-cgroup: buffered, filesystem metadata, swap, and direct IOs,  making IO control a far more effective component of a resource  utilization strategy.


So I made an Ubuntu 18.04.1 VM under virtualbox and I am trying to play with cgroup v2.  So far I added GRUB_CMDLINE_LINUX_DEFAULT="cgroup_no_v1=all" to /etc/default/grub and then ran update-grub and rebooted.  Then I ran the following test:

```

# root@ubuntu-VirtualBox:/home/ubuntu# dd if=/dev/zero of=~/test-file bs=512M count=1
1+0 records in
1+0 records out
536870912 bytes (537 MB, 512 MiB) copied, 0.696432 s, 771 MB/s
# mkdir /cgroup2
# mount -t cgroup2 nodev /cgroup2
# cd /cgroup2
# echo "+io" > cgroup.subtree_control
# mkdir cg2
# cat /proc/partitions
major minor  #blocks  name
   7        0      35472 loop0
   7        1       2376 loop1
   7        2      88964 loop2
   7        3      14840 loop3
   7        4     144260 loop4
   7        5      14852 loop5
   7        6      13300 loop6
   7        7       3796 loop7
  11        0    1048575 sr0
   8        0   83886080 sda
   8        1   83884032 sda1
   7        8       3788 loop8
   7        9      35368 loop9
   7       10      13300 loop10
   7       11     144040 loop11
   7       12       2300 loop12
   7       13      93256 loop13
# echo "8:0 wbps=1048576" > cg2/io.max
# mkdir /cgroup2
# mount -t cgroup2 nodev /cgroup2
# cd /cgroup2
# echo "+io" > cgroup.subtree_control
# mkdir cg2
# echo "8:0 wbps=1048576" > cg2/io.max
# echo $$ > cg2/cgroup.procs
# dd if=/dev/zero of=~/test-file bs=512M count=1
1+0 records in
1+0 records out
536870912 bytes (537 MB, 512 MiB) copied, 0.675306 s, 795 MB/s

```

but the IO throttling seems to have had no effect.  What am I missing?

---

