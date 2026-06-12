---
title: "Limit Internet Data Transfer - Daily/Hourly"
date: 2013-05-14
forum: General Help
---

### Post by Alsanh on 2013-05-14
I want to Limit the Max Gb/s of data transferred every hour and every day. What application would be suited for that?

Thanks!
-Alsanh

---

### Post by moody_mark on 2013-05-15
Good question, you are probably looking at a tool which will shut off the interface if the useage reaches a certain amount. I think you might have to write a script for that, however you could look at this post here: [http://ubuntuforums.org/showthread.php?t=1231690](http://ubuntuforums.org/showthread.php?t=1231690)

For monitoring I can reccommend "vnstat" which gives some good command line output, for example:

[FONT=Courier New]$ vnstat -i eth1
Database updated: Wed May 15 10:03:12 2013

   eth1 since 09/08/11

          rx:  130.25 GiB      tx:  78.82 GiB      total:  209.06 GiB

   monthly
                     rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
       Apr '13      5.30 GiB |    8.47 GiB |   13.76 GiB |   44.54 kbit/s
       May '13      5.06 GiB |    1.82 GiB |    6.87 GiB |   46.29 kbit/s
     ------------------------+-------------+-------------+---------------
     estimated     10.88 GiB |    3.90 GiB |   14.78 GiB |

   daily
                     rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
     yesterday      1.20 GiB |  114.71 MiB |    1.32 GiB |  127.68 kbit/s
         today     14.90 MiB |    7.20 MiB |   22.10 MiB |    5.00 kbit/s
     ------------------------+-------------+-------------+---------------
     estimated        33 MiB |      16 MiB |      49 MiB |
[/FONT]

---

