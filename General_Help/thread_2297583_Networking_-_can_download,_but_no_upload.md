---
title: "Networking - can download, but no upload"
date: 2015-10-05
forum: General Help
---

### Post by james_farrell2 on 2015-10-05
I turned on the machine one day and some websites would load others not. SSH wouldn't work, gmail wouldn't work.

So I opened the my ftp client and tried to upload something and it stopped at 0.1 complete.

Pulled out some hair.

Solved the issue by plugging a network cable into the thing.

That worked for 4 days.

But now I have the exact same problem!!!

Is there some sort of upload port that could be closed or something? 

Any idea how I can debug this issue?

---

### Post by SeijiSensei on 2015-10-05
First, let's test connectivity.  Open a terminal with Ctrl-Alt-T and type the command
```
ping -c 5 8.8.8.8
```

You should see something like
```

$ ping -c 5 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=58 time=18.7 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=58 time=18.1 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=58 time=18.0 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=58 time=18.0 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=58 time=18.0 ms

--- 8.8.8.8 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 5000ms

```
If you cannot ping the server, then first try rebooting your router by turning off its power, waiting thirty seconds, and turning it back on.  If that doesn't solve the problem, call your ISP.

If you run torrents, that can knock some routers offline.

---

### Post by james_farrell2 on 2015-10-05
Thanks for your reply....

I ran the ping and I get the same results as you. I don't run torrents...

---

### Post by SeijiSensei on 2015-10-06
You need to talk to your ISP.  You obviously have connectivity.

One thing you can try is running a test from speedtest.net. That tests both upload and download speeds.  If they both look correct, then there is some other problem.  If the upload test is sluggish or fails, calling the ISP is the next step.

---

### Post by james_farrell2 on 2015-10-06
Upload is working on all other computers in the house, it's just my linux box that's not working....

---

### Post by james_farrell2 on 2015-10-06
I tried running a speed test, and it just failes when it gets to the upload test...

---

