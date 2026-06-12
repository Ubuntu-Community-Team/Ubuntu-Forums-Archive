---
title: "USG CIS kills ping on 127.0.0.1"
date: 2024-01-05
forum: General Help
---

### Post by melon89 on 2024-01-05
Hey guys,


I'm playing with the USG CIS hardening in Ubuntu. 
But I have a strange problem with Ubuntu 22.04 that does not happen with 20.04. 


As soon as I finish the "sudo usg fix cis_level1_server" command, the dns resolution and ping to localhost/127.0.0.1 is broken.
For fixing the dns resolution I found some article in this forum and the dns is working fine after that.
But for some reason I can't ping my localhost:

*#PING localhost (127.0.0.1) 56(84) bytes of data.**#--- localhost ping statistics ---*
*#6 packets transmitted, 0 received, 100% packet loss, time 5119ms*


[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAggAAABFCAYAAAAvpR74AAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAA/1SURBVHhe7Z2JlaM6EEUnHlIhEgIhEMfRwXnqaaMkSgvGS7t5/5z7j5HQUqsk3IP/yX93QgghhJACs5AQQggh18YsJIQQQsi1MQsJIYQQcm3MQkIIIYRcG7OQEEIIIdfGf1huP/efH83tvi5TunFey3phnbO6W7h/Wm67e/79m 7Lervfwji3dXHXy5Qm0mZeU59xnLfSGD/Ku87q/l/Ocst1P03zfV5WZx9bv/N9TT6S wbY 89xO01hfPT/iI3PtO/KPy1St9ynsnwUtM/0s95n475pxjjhnsZ4pf0QX7PEU9J9irsSsSPuKetPyOfj/0AsfzFaxy4OHor5YAPRt11PyK8hfoDT6qTlF/Qy6LEYWgkUgXO7qfYh4ej6dVbtpkkWnONJpTb u6iNj/JXbxAWrd8zYLNTW0CkzpIPC1Kyn9jOX v6fG6H7VSOK9eH9Hm2faQiP8BC LCNEQ/VRduDDc66zLJZsesTMsfSfs7/1Lxtf/R2W7AJMeZyRr79huU4T/PvV Fy2vr4JjEDG 5jG4Rfrx/yF4kfyg2CnWRqiR8bgAUnsJh49Aah2Cycob7w A1NOkHJeHkwTW6Oafcv9dkGRZJmfkK2k3ltfKerReRM/ZfB3J9fVi fM/2Fcs3jybzRtrFAaizf0BxNZs5/9AIzsKBqzrZPtOQPfvzQAtGbj9Svg/O17Ffaw/JTv0mXz7W5nJAvbjxSDMH 0R7o1/nsZiPMz98nPp7qczIZJyyoWx2eQObzbMTPEO34NJ gHuk/mz/sUGwQWvlnRD D YuQg8QP5QZBAsY4FViJB8QEnRJ1SDaufnDRGaE2/m6uLiC3JOKTo2qHepWwIK8 udVOU7XxfcLbkiLG0/f15uf7ldNjvMYpsUhAzzlBlHYuGLFVbyFB/cHFOflNLNP M8DZ9omm/KXPHADz0QleL6AA48qiZy6wGTX7wZ/Eh6Q9TrlrsYA6/4o2qdrncfncV0zwidjW bea506vyC 5HC3/Xtbi5I7 RcZ4PRI/LXrx6cse9ClnG23PyflrPr9 /mnH/1j IuQg8QOSQ0hOjmJBDdQWyJSgQxBNOpiy5FCMc3AhMcevJLxt0fDBXtZnSB/ZCUU H90g5Dt6JXN3fgBz1OPrhOJ5ygYBc5EFprq47xJ5gdNTex47XQxwdoE/2z7Rkb/59OUIhU9AZ87uaWxZQBdjE1azH yi5oWvK7Q rBOwJeej8tUOE1tfxYbA0HPVv53M /nnf8fRj58qhS0iL/Wpsi/YL5v/wQ3CQHtCHiB wMLdcMBAbYHUweQSAx63xwAYDcABzPG7/fsNQnVRdLLLvWpDlCe3jZr8u/sPbxAUk5wGJMG/5AkC5vLgBsH9EaDIUdcj2J8MR9ideCo6q3G2feJdG4Tgk/Ea/lPa2/SPiv1297bkaOjmdRsEIc3J9pG63 S66lKJnyoVfex0ivuOzCNi2SLrayz/NPUzmL8IOUj8ACfrJ3Y4npV48mBCQMtOVgWTSyDFEwl857dLgB1q4/ceEWIB0e3wV uYowsiF6ySdEN7/CV5qgv3p3aV8XcBWSSF3vxQr5/Y4BFpmbR0H26xbi30VTp2NhcWSehiq/4fwQmNxQf9 KdHxvjSLv9XM1b/L2wfMeWPQHfHfRbAdngEHq9n0V/ 9AyLJnwujG094nbY9vP2KOxTk6NqozPy XjXMeRO8dl9fmPg/lbJmFvLv2FPrb Skfhpocd2vPMrBtdvP/9U9TPYfsj/CcnxH1yAO cB yRhPaKMCU7XpcCXAM138H6R2drnAd0GiWsbY0M7et4/AnmXnPT4CLYioaa2q7R111EP7fF1WxeUkD1cb4mwPT8kzjWbn04oHpf0GvWjWKdE0746gZV1wj4BeV1Y5Z6oRztBuVNf6NtepF/Xvil/JCwQxzdloLD/7o/shLBp9WPX7Wuf8sv 7cXRjNXIg/L5PhFPyk9q83exUbFf078nGUfHh2wYRMY415H4adOLz9Cv5sAGJLOty33BF4OPtfOPp6Wfkfa9 CHEwCwkfxkk6SPJjTiwENY3P2/kRfZ7i3xY5MzNGyHkF2IWkj/O7pEqaXPq6cHzebr9Xixf/oSGvkfIl2AWEkIIIeTamIWEEEIIuTZmISGEEEKujVlICCGEkGtjFhJCCCHk2piFhBBCCLk2ZiEhhBBCro1ZSAghhJBrYxYSQggh5NqYhYQQQgi5NmYhIYQQQq6NWUgIIYSQa2MWEkIIIeTamIWEEEIIuTZmISGEEEKujVlICCGEkGtjFhJCCCHk2piFhBBCCLk2ZiEhhBBCro1ZSAghhJBrYxYSQggh5NqYhYQQQgi5Nmbh 5nX 8/Pj O2TPY9r6Qx/rTcXPk6q/u/lHn9kH5/Ca W/ r6JYT8KczCj4HF JMJtjY yl 9QVhu6302yq/CWflfrb r24cQcjnMwo9R3yBM92X1J3l3yr8tRbKe5PS21f9I/Xq73Zcp1M 4DnU/stgvs2q70dwgLMv9lvovF4v /LJ6 Yx7XN2k lWMbkgWJ5fIuqzZ/JLsYOAJyW3N2 fznzf9oU7Gsvqqc1L lv2G2veeUJ2dX7//pn 2xieEkM9gFn6M2gK9ZMlUmLBgLfcpXCP5rrNqh3osmioBT6o9HgVbC3Brg/DzIwtj6APj6ft68/P9zts1FpRiAThzQsUm4bbKeEpeq7 mfLi/JV/U74S awuhzXn5 /Yb0V9L/mfYp9Z/zz9HxieEkDeD/yFZhZNNRkyIZ vHMRMsTnDr/sSPpOsTrF My/oM6WM7gcriJp PbhDKE2O6rzs/gDnq8UU3asED5zYIxQZF2M05lD0kX6lfXT/ESfkH7HdmAX Wfez B/xzYPw60ja0y4nzPVtPCLkoZuHHMBPs4AYhnr72IAHKveoEt1sQVbm1gOzuP7xBUMgJfMIj mLR NsbBMVh cfsd26DoDhhH7v/nn8WVMYnhJA3YxZ jFoC73/FIKcu1W5y9eGU6Ra4NT2insL32eUC4 oq4 8WpGKB7M0P9foRMx4hl5sK3QcWiJuc4EYXlWd8xTAs3wNfMZySf9B I/pr dcz7FPrv mfcj0yPiGEvBmz8M1Isuw 4iz iEsW33zxy t/kMyLE2dqKwvp7K5jwm Pr9u6hC7JO15vSb89PyzWazY/6TssNhG3KDTqW7jFa/aLzr79M Qr sYCaSyENc7K37Zfr33fv87Nr99/zz9HxieEkDdjFpIvQ59u3wEW6CMbBEIIIV HWUi CP/PHOPJ83XfW tx3NcZxj2EEEL DGYhIYQQQq6NWUgIIYSQa2MWEkIIIeTamIWEEEIIuTZmISGEEEKujVlICCGEkGuTF AtdXjPffwnc7/ln7LhTXTli3HI8ynf PcZwouHnvxPNt3bD51vf 87HN5jn frH2 OdC/XEv3X5t zT7MeeSv E1z9S5 /hI/nL/PlZ3 Pj UvvO016NejX5LW9/ R MCr 5MN1 2H3V7MdoEAxM/o6l/N 02cfRmQ9erhZ/Lq/j9NT77nyo83Nz5xg4C3IOrAk vyVc1E82T9R0o71MpL 3TqkTz99STz/p1x BvyV 1V4N/Ar86vld/j2VHz/0itXsrdgT36DzYU78lf4YMIuD747nf/Ah1xfuyA4g5KjJkFQ v3/B1TtkOCMvLfy98CTL92Nz3lCO 2j XZi3x2uztPvkAUr0qWz8O/xz/Qvz9B N2h2yniHu3wDf1EeW9rrt88WGrzj6dBSaiuf2kHJyz7gAPGtqWD9uQb0W/LPrt6JPvnLlC7H87CnA/4e9d Pfl6/t1r37BPnFuqU/empwAf1n8Cvlf6l9CzT9d J54g/I38NUZ9g9B VXw/P57Inz1G5K/Gh gV5b38143fDqP5pOL/iUo97JbbO8bnoHyP2yd8QKeilKQkdK4DpIP78R4oNbWRCRUT1E8mkNS0wAiu1u/lgxhg/lFMPr9FFs9dwpP5pGuhtQP1gXPu9/i7O1z0KTLBkZwuZI5aXy39uKSiZIa tCM15 8CLCYnzMH343Xu78/7sR24J1 rvm0fOPsmG3Thku2zEoyA/rQvOZ0c7b9hv57/9fx7xH9BzT67chfPW8L6tP4TmJcx/559Ruw3TTJvLORyr/8qopC5wbfnr1Fq/rN7uoHxRb9xTs38MlD/DEbkN UbyH j8VfFjRHWztb6WfH/RK0 6NP7oPi5yOnkQN2AfCfs4z gA7ezSJOTAFnGd1E7BxPQZwoiESLbocnnLcC8M q2Fi6I0QcStK4rjZPIHartYJjD1vbY7/F7ug7cco6mfgpdgl1fjflDP1G/cIywcOz6DGW1Ofbkq9b37GPpRc/5CYwsMF1q9uvJ1/PvbvuNun38o/UYF1k8/gL9Jyo67NmnVx fAuAp2yKJcJbNQrp3gO/PX2OY/oPx1WYykuu8lx/P588eI/JX5Yv2sfLfoP4PUdFpNYdEGvWYb5ybP8yH fXkc 0fto//4AYvnHwXlA3aASaTww6n HXFMsB6mxEE2CoJwAmX1fn2 l6L4QB78Pf4u/1Xjd/Tz/666Wjl/IccyIOyWr89 er1HftYsug5P4HyxFcN4BYt zXn2vPvMf8FLfske2KemWyf13 iosOefUbtBx34JLj37RZ/Kn81MP2nostq/u/lxwfzZ48R avyxbmI/ 3z33j8jVPps5pDAr36hOq/K1/BMfvED3ikhiAMkyseMfVwu PaIzongJxuQp31e/5IAFox5e/lgxTEUGLhLHBmPEKJ1xY6CUBB vf8UXf29/hb/Ttqxh/Qz87YRV/N R9wIDPAAj35WvVt 8DWYs/Q1j1Ck/t3Doy5I/kftItDdLAqudB/KXuXmv2Env/1/HvEf0HLPjFpaDtEPq7/SE2HPfsM2U/kiKcPyBeX57/hql5j87nynyP pb bFX7zjpPyPym/I5 7Xz34j W2Buur37CsCSE3ox9J9o1G yTm6 S/StAfmG7GOjLoJTOyNmCaOPM577wya7PSbrygUE4v73/CUgReh4T/l7 QjAeL//HPpKyvRK0 2hAO1ATimpPp8fksHZ3 Ov94/EFcoVOnm09KPrXBs4Qbw3yF fvxobDhHaol3s1/1BWrwnQ/oI83NzbOivX9 xj/Y9d/oLc1KLlPaBrd9xkFTi M0g3dG3X9//2v7dbj9mH BsCjsX5Z/Wv47ZbQ75BqRnnxH7bbGyJccRvj1/tRnxn3z WHC0b/Xy40j PB2/Vflb8qk6xIWZ/9BHX/9tCv1hs6nqe/7fjQ/ZlEbZ3ebSkr0h34n1zSw8jN7dEfJ8JAAledcWBvJq/rb mb9eDeP3SzELDwHDbzuT/FRAyFPAYzTjxEzexB/WP/PXG2D8fitmISGEEEKujVlICCGEkGtjFhJCCCHk2piFhBBCCLk2ZiEhhBBCLsu/ 38Q41tX9RQCiAAAAABJRU5ErkJggg==[/IMG]
all other pings are working fine... 

If I'm doing the same on my 20.04 version it is still working.
And based on my services which I use is this communication required.

I haven't been able to find a solution to this problem.
Does anyone have any idea how to fix this?


I checked:
- lo interface | looks fine
- sysctl ipv4.icmp settings | looks fine
- firewall not active / iptables fine

Would be grateful for further ideas
Cheers!

---

### Post by #&amp;thj^% on 2024-01-05
What is the current DNS settings now?
When i played with it I used  "1.1.1.1 and 1.0.0.1 a local DNS server (e.g. PiHole)"
```
ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.030 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.069 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.070 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.069 ms
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.067 ms
64 bytes from 127.0.0.1: icmp_seq=6 ttl=64 time=0.070 ms
^C
--- 127.0.0.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5078ms
rtt min/avg/max/mdev = 0.030/0.062/0.070/0.014 ms

```

---

### Post by melon89 on 2024-01-05
The current dns settings point to my own dns servers in the network.
And the name resolution works fine - when I ping 127.0.0.1, the dns is not needed from my point of view.
So I just focused on some issue of cis hardening that only happen in 22.04.

```
nameserver 10.30.4.2
nameserver 10.30.4.3
```

My testserver ping on hostname:
```
ping ubuntu2204
PING ubuntu2204 (10.70.250.5) 56(84) bytes of data.
64 bytes from ubuntu2204 (10.70.250.5): icmp_seq=1 ttl=64 time=0.038 ms
64 bytes from ubuntu2204 (10.70.250.5): icmp_seq=2 ttl=64 time=0.039 ms
64 bytes from ubuntu2204 (10.70.250.5): icmp_seq=3 ttl=64 time=0.020 ms
--- ubuntu2204 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 8013ms
rtt min/avg/max/mdev = 0.020/0.035/0.039/0.005 ms
```

or ping into internet:
```
ping google.de
PING google.de (142.250.185.99) 56(84) bytes of data.
64 bytes from fra16s49-in-f3.1e100.net (142.250.185.99): icmp_seq=1 ttl=118 time=22.5 ms
64 bytes from fra16s49-in-f3.1e100.net (142.250.185.99): icmp_seq=2 ttl=118 time=15.8 ms
^C
--- google.de ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 15.771/19.134/22.498/3.363 ms



```

My testserver ping on localhost:
```
ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
^C
--- 127.0.0.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2044ms
```

and of course before the usg cis command the ping on localhost was working. 
I tested it the first time with 22.04 = problem. Tested same on 20.04 = works fine. Now second test machine on 22.04 = again the problem.

---

### Post by melon89 on 2024-01-05
Sorry about that! At least I found a workaround in this thread to get it working again:
[https://ubuntuforums.org/showthread.php?t=2492542&highlight=usg](https://ubuntuforums.org/showthread.php?t=2492542&highlight=usg)

There is mention a bug who fix the DNS issue by using following:
```
[COLOR=#000000][FONT=&amp]#usg generate-fix --output fix.sh cis_level1_server[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]#sed '/nft insert rule inet filter input ip saddr 127.0.0.0\/8 counter drop/s/insert/add/' -i fix.sh[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]#bash fix.sh[/FONT][/COLOR]
```

But this will not fix the issue that I'm unable to ping 127.0.0.1.
Therefore I choice for the moment the unsecure way and deactivate the nftables service.

Probably someone will find a better solution. 
Best Regards

---

### Post by #&amp;thj^% on 2024-01-05
> **melon89 said:**
> Sorry about that! At least I found a workaround in this thread to get it working again:
[https://ubuntuforums.org/showthread.php?t=2492542&highlight=usg](https://ubuntuforums.org/showthread.php?t=2492542&highlight=usg)

There is mention a bug who fix the DNS issue by using following:
```
[COLOR=#000000][FONT=&amp]#usg generate-fix --output fix.sh cis_level1_server[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]#sed '/nft insert rule inet filter input ip saddr 127.0.0.0\/8 counter drop/s/insert/add/' -i fix.sh[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]#bash fix.sh[/FONT][/COLOR]
```

But this will not fix the issue that I'm unable to ping 127.0.0.1.
Therefore I choice for the moment the unsecure way and deactivate the nftables service.

Probably someone will find a better solution. 
Best Regards
Please file a bug against it, they claim "Fix committed and will be added to next release of usg."
If you find it different then add to this bug-report: [https://bugs.launchpad.net/usg/+bug/2039445](https://bugs.launchpad.net/usg/+bug/2039445)

---

### Post by MAFoElffen on 2024-01-05
> **melon89 said:**
> Sorry about that! At least I found a workaround in this thread to get it working again:
[https://ubuntuforums.org/showthread.php?t=2492542&highlight=usg](https://ubuntuforums.org/showthread.php?t=2492542&highlight=usg)

There is mention a bug who fix the DNS issue by using following:
```
[COLOR=#000000][FONT=&amp]#usg generate-fix --output fix.sh cis_level1_server[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]#[/FONT][/COLOR][COLOR=#ff0000]sed '/nft insert rule inet filter input ip saddr 127.0.0.0\/8 counter drop/ s/insert/add/' -i fix.sh[/COLOR]
[COLOR=#000000][FONT=&amp]#bash fix.sh[/FONT][/COLOR]
```

But this will not fix the issue that I'm unable to ping 127.0.0.1.
Therefore I choice for the moment the unsecure way and deactivate the nftables service.

Probably someone will find a better solution. 
Best Regards
Yes, you cannot ping 127.0.0.1... And?

Why would you do that?
Re: [https://www.tenable.com/audits/items/CIS_Amazon_Linux_2_v2.0.0_L1.audit:25f15ef6728c9dd4f619de3e2f0c8e16](https://www.tenable.com/audits/items/CIS_Amazon_Linux_2_v2.0.0_L1.audit:25f15ef6728c9dd4f619de3e2f0c8e16)

As explained there, that is a Security measure for those reasons. (That is normal for that.) You are chasing ghosts. 
> 
The loopback interface is the only place that loopback network  traffic should be seen, all other interfaces should ignore traffic on  this network as an anti-spoofing measure.

So pinging that address is now one of the things it is now ignoring...

That sed change on that rule... It would then fail that in the audit. You see that right?

---

### Post by melon89 on 2024-01-08
I understand tenable's statement:

"Loopback traffic is generated between processes on machine and is typically critical to operation of the system. 
The loopback interface is the only place that loopback network traffic should be seen, all other interfaces should ignore traffic on this network as an anti-spoofing measure."

But that's exactly my problem. Let's look away from the ping, the problem was that I had internal applications using the above communication. 
I thought it was related to this and after deactivating the nftable these applications worked again. 
This means that some internal processes are being blocked? Or am I seeing something wrong?

The moment I reactivate it, the application is working. 
You can try quick installation of wazuh, for example.

---

### Post by MAFoElffen on 2024-01-08
Then the only thing you would have to do to get that working again is to remove that nft rule, or to comment out that rule insertion in the fix.sh script, right?

Or to insert the rule, being more granular, so it opens the specific IP and/or port.

Here is what my cuurent rulset is, highlighting the rule that has that cranked down
```

mafoelffen@usg-cis-ws1-01:~/Scripts$ sudo nft list ruleset
table inet filter {
    chain input {
        type filter hook input priority filter; policy accept;
[COLOR=#ff0000]        ip saddr 127.0.0.0/8 counter packets 22 bytes 1360 drop
[/COLOR]        iif "lo" accept
        ip6 saddr ::1 counter packets 0 bytes 0 drop
        ip protocol tcp ct state established accept
        ip protocol udp ct state established accept
        ip protocol icmp ct state established accept
        tcp dport 53 accept
        udp dport 53 accept
    }

    chain forward {
        type filter hook forward priority filter; policy accept;
    }

    chain output {
        type filter hook output priority filter; policy accept;
        ip protocol tcp ct state established,related,new accept
        ip protocol udp ct state established,related,new accept
        ip protocol icmp ct state established,related,new accept
        tcp dport 80 accept
        tcp dport 443 accept
        udp dport 53 accept
        tcp dport 53 accept
    }
}

```
Off to work. Will look at this laters.

---

### Post by The Cog on 2024-01-08
That [COLOR="#B22222"]ip saddr 127.0.0.0/8[/COLOR] rule is bonkers. It will break soo much stuff - anything where the server wants to talk to itself, including local DNS (as you discovered), local print spooling via cups, local webserver trying to access local database, etc. etc. If you really want to keep it, preempt it with something like **[FONT=Courier New][COLOR="#FF0000"]iifname "lo" oifname "lo" accept[/COLOR][/FONT]** .
And I think that line **[FONT=Courier New][COLOR="#FF0000"]iif "lo" accept[/COLOR][/FONT]** is wrong, should be **[FONT=Courier New][COLOR="#FF0000"]iifname "lo" accept[/COLOR][/FONT]** or **[FONT=Courier New][COLOR="#FF0000"]iif 1 accept[/COLOR][/FONT]**
See [https://wiki.nftables.org/wiki-nftables/index.php/Matching_packet_metainformation](https://wiki.nftables.org/wiki-nftables/index.php/Matching_packet_metainformation)

---

### Post by MAFoElffen on 2024-01-08
@The Cog --- Someone from Canonical wrote those default rules in that script. 

The default rules first have most all ports closed off so there is no DNS. You can see where I opened up port 5 for that.

Home now. I will play with what you recommended and other to see if we can tweak this more ad get more working.

After we tweak it, I will forward the recommendations to Launchpad to tweak that script.

I see that on rule here: [https://www.tenable.com/audits/items/CIS_Amazon_Linux_2_v2.0.0_L1.audit:25f15ef6728c9dd4f619de3e2f0c8e16](https://www.tenable.com/audits/items/CIS_Amazon_Linux_2_v2.0.0_L1.audit:25f15ef6728c9dd4f619de3e2f0c8e16)

---

### Post by The Cog on 2024-01-09
Hmm. I see this in "man nftables:
>        meta iif, oif, iifname and oifname are used to match the interface a packet arrived on or is about to be sent out on.

       iif and oif are used to match on the interface index, whereas iifname and oifname are used to match on the interface name. This is not the same &#8212; assuming the rule

           filter input meta iif "foo"

       Then this rule can only be added if the interface "foo" exists. Also, the rule will continue to match even if the interface "foo" is renamed to "bar".

       This is because internally the interface index is used. In case of dynamically created interfaces, such as tun/tap or dialup interfaces (ppp for example), it might be better to use iifname or
       oifname instead.

       In these cases, the name is used so the interface doesn&#8217;t have to exist to add such a rule, it will stop matching if the interface gets renamed and it will match again in case interface gets
       deleted and later a new interface with the same name is created.
I *assume* that this means iif performs a name->index lookup as the rule is entered, and then checks the ifindex from then on. So I guess that if tun0 were to be deleted and then a new tun0 created with a different index, "iif tun0" would not recognise packets from the new tun0 interface. It's a pity the man page doesn't spell that out clearly.
A quick test here confirms that restarting openvpn does indeed change the tun1 index number. When I have time, I will test whether that affects any "iif tun1" rules. Will also test if giving iif an integer argument works. But "iif lo" should always be stable with index number 1.

---

### Post by The Cog on 2024-01-09
I've proved it with testing:
I configured an output rule and made it count some packets:
```
	chain OUTPUT {
		type filter hook output priority filter + 1; policy accept;
		oif "wgvpn" ip daddr 10.10.10.10 counter packets 2 bytes 168 accept

```
Then I restarted the vpn. "ip link " showed that the index had changed from 5 to 6, tcpdump in another window exited, and nftables showed its true colours and stopped counting the packets:
```
	chain OUTPUT {
		type filter hook output priority filter + 1; policy accept;
		oif 6 ip daddr 10.10.10.10 counter packets 2 bytes 168 accept

```
I entered same rule for iif wgvpn again (up-arrow and enter) and this created a new rule that did count subsequent packets:
In conclusion: Using "oif wgvpn" works and looks good in "nft list ruleset" until the vpn restarts.
When the interface restarts and changes its index number, "nft list ruleset" starts to show the index number for the old interface instead. No rules apply to the new interface.
If you enter a rule for an interface number that doesn't exist, the rule has no effect until the interface comes into existence, which can happen if you keep restarting a vpn intertface.

DO NOT use iif or oif for interfaces that can disappear and reappear because they use the prevailing interface index at the time the rule is entered - they do not follow the name.

---

