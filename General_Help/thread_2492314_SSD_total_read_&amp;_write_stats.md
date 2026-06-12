---
title: "SSD total read &amp; write stats"
date: 2023-11-07
forum: General Help
---

### Post by julian-g71 on 2023-11-07
Hi - is anyone able to help suggest a command or file that details the total amount of data written to or read from an SSD over its lifetime? I'm sure I've seen one that provides this in a human readable format but for the life of me cannot remember it so I know it exists.

I already know about the following but its 100% not these that I am thinking of right now.

cat /sys/fs/ext4/<device>/lifetime_write_kbytes

smartctl -a /dev/<device>

hdparm -I /dev/<device>

The command or file I found previously provided a load of SSD information along with something like this:

Total data written : 7936GB
Total data read : 3726GB

as an example, the wording may not be 100% accurate but it was the fact the figures were given as GB without the need to perform any kind of calculation on them.

And these are all 20.04 & 22.04 LTS serverrs.

Any help would be greatly appreciated.

---

### Post by TheFu on 2023-11-07
```
sudo nvme smart-log /dev/nvme0
...
data_units_read                     : 12,284,877
data_units_written                  : 66,829,169
host_read_commands                  : 159,898,261
host_write_commands                 : 1,449,781,642
...
power_cycles                        : 27
power_on_hours                      : 2,549

```

---

### Post by dragonfly41 on 2023-11-07
I see that Crucial.com offers a tool but it only runs on Windows.
I might dual-boot  into Windows to try it out.

[https://www.crucial.com/support/storage-executive](https://www.crucial.com/support/storage-executive)

---

### Post by julian-g71 on 2023-11-13
Thanks, the command I used displayed the read / write stats in a nice human readable format and it was a command already bundled with the Ubuntu install I'm sure. I just can't for the life of me remember the command and we have several hundred machines running so no idea which one I ran this on now.

I knew I should have a made a note of the command at the time, oh well.

---

### Post by dragonfly41 on 2023-11-13
Suggestion .. Open Phind.com in browser and query ..

"Ubuntu command to read SSD read & write statistics in a human readable form."

---

### Post by MAFoElffen on 2023-11-14
But TheFu gave an answer. That can also be done with smarmontools, and hdparm...

---

### Post by julian-g71 on 2023-11-14
I know and in my original post I'd already mentioned both those commands and more, but it's not those I am thinking of. Just to be clear I was looking on a server I look after, one of several hundred and I got looking at disk stats and I remember there was either a command or file that I looked at that provided disk stats but I distinctly remember it gave the total read / write stats in a really nice format. So unlike smartmontools or hdparam.

I'll probably stumble across it again at some random point in time.

---

