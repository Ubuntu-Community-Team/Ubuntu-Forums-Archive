---
title: "Curious results from iftop"
date: 2019-05-28
forum: General Help
---

### Post by yapidumoac on 2019-05-28
Running $iftop -t > log.text from the command line, with no browser running gives me this results. Any ideas why the computer is doing this?

> # Host name (port/service if enabled)            last 2s   last 10s   last 40s cumulative
--------------------------------------------------------------------------------------------
1 192.168.1.2  =>     4.86Kb       996b       830b     1.22KB
  104.20.16.242                                <=     18.9Kb     3.79Kb     3.16Kb     4.74KB

2 192.168.1.2                                =>     1.90Kb       618b       515b       773B
  rpz-public-resolver1.rrdns.pch.net        <=     3.08Kb     1.01Kb       859b     1.26KB

3 192.168.1.2                                =>     1.86Kb       382b       318b       477B
  a2-22-135-12.deploy.static.akamaitechno    <=     2.18Kb       446b       371b       557B

4 192.168.1.2                                =>       252b        50b        42b        63B
  rdns.dynect.net                            <=     1.05Kb       214b       179b       268B

5 192.168.1.2                                =>         0b        83b        69b       104B
  ec2-3-215-156-85.compute-1.amazonaws.co    <=         0b       166b       139b       208B

6 192.168.1.2                                =>         0b        61b        51b        76B
  enterprise.frmug.org                        <=         0b        61b        51b        76B

7 192.168.1.2                                =>       248b        50b        41b        62B
  resolver1.opendns.com                        <=       312b        62b        52b        78B

Ubuntu 16.04 LTS

and when I run fast.com from Knoppix I get about 16mbps while from the installed system I get about 7.5mbps

---

