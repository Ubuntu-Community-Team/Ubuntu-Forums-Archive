---
title: "Troubleshooting periods of intense resource usage and crashes"
date: 2021-04-30
forum: General Help
---

### Post by temporos on 2021-04-30
I have an AWS Lightsail instance running Ubuntu 20.04. For the most part, it's running well. But about twice a week at 3 AM, I'll get an alert email (which I don't hear, since I'm sleeping) about my instance suddenly using 100% of available CPU cycles. When I check the AWS metrics, I see that the server was at 100% CPU utilization for about an hour, but Ubuntu has crashed, and the console can't open a connection to log in. At that point, my only recourse is to force the server to reboot using the AWS tools. How do I go about troubleshooting this issue? The only thing that server is doing is running a game server for two people, and I know that neither of us are ever logged in when this happens.

That Lightsail instance has 1 GB of RAM, so it's light on memory, but every time I check **top**, the game server is using only about 400 MB. Could the sudden 100% CPU utilization be swap going crazy and crashing the system? What could cause that if no one is logged into the server? Are there system logs I could check that might tell me what's going on when this happens?

---

### Post by HermanAB on 2021-05-01
Look in the crontabs to see what is scheduled for 2 am.  Look in the system logs around that time.  Disable cron and see if the problem goes away, etc.

It probably doesn't crash.  If something uses 100% CPU then you cannot log in remotely, since sshd and the network stack are starved of resources.

---

### Post by dragonfly41 on 2021-05-01
I have read about servers and desktops being taken over for intense sessions of bitcoin mining planted in some malicious apps. Games are one likely source.
Just one idea.
Also Stacer is a nice GUI for Linux monitoring.

---

### Post by temporos on 2021-05-30
Sorry for the long delay on this thread. I needed to travel unexpectedly. Back now, though, and just in-time to catch another episode of everyone's favourite game show: *Why is my Ubuntu server not responding? *:popcorn:\\:D/=d>

Nothing was scheduled in the crontabs for 2 AM, so I installed sysstat to record system metrics. Last night, the server had another one of its CPU spikes, and when I noticed it this morning, I took some screenshots of data from the sysstat file. I'm having trouble uploading those images here, though (not sure why). Is there a trick to attaching images to these posts? When I use the Add Files > Upload option in the editor, it acts like it's uploading (the progress thing spins), but then it does nothing.

---

