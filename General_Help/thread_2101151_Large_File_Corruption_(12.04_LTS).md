---
title: "Large File Corruption (12.04 LTS)"
date: 2013-01-03
forum: General Help
---

### Post by WhiskeyAlpha on 2013-01-03
Hi,

I'm experiencing an issue with large files becoming corrupted.

I use Ubuntu 12.04 LTS (all updates applied) on a PC that I use almost exclusively as a file server. It has a 6 x 2TB RAID5 array (mdadm), with a single EXT4 partition, which I use to store all my movies/music etc. I use samba to share the directories to the various devices that I use to stream the media at home.

Recently, I have noticed that some large videos (15GB-40GB) that I have copied over via samba have become corrupted, introducing glitches and artefacts into the image.  

Using md5sum to compare an original and a copied file, I can see that this corruption also occurs with local copies (i.e. not just via samba):

```
1647f56723006cb7af115084fe85d877  Avatar (2009) [Extended Collector's Edition].mkv
c247efa233f0651b5d57d0fc1cc7ac40  Avatar (2009) [Extended Collector's Edition] (copy).mkv
```

Smart tools show no issue with any of the drives in the RAID array.

With the corruption occurring locally, would it be fair to assume that my problem is either:
A) the RAID array (mdadm)
B) the filesystem (EXT4)

Can anybody suggest some troubleshooting steps which might help identify the cause?

Thanks,

WhiskeyAlpha

---

### Post by ibjsb4 on 2013-01-04
Seen this?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Large+File+Corruption+ext+4&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Large+File+Corruption+ext+4&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by WhiskeyAlpha on 2013-01-04
> **ibjsb4 said:**
> Seen this?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Large+File+Corruption+ext+4&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Large+File+Corruption+ext+4&as_qdr=all&sa=Google+Search&lang=en)

Thanks ibjsb4,

Yes, I was aware that there was a known issue with EXT4 partitions losing/corrupting data but as far as I'm aware, this would historically require power cuts (or hard power downs) and in the more recent examples, was only exposed by frequent restarts, when using one of the most recent stable kernels.

I restart the system maybe 6 times a year to apply updates and I've never had a power cut in my current property.

The corruption can be seen simply by copying a file locally and then using md5sum to compare it to the original (with no crash/power cut/restart in-between), which suggests a somewhat different issue to the one mentioned in the links provided.

Thanks,

WhiskeyAlpha

---

