---
title: "Apache is slow..."
date: 2006-08-31
forum: General Help
---

### Post by Gipetto on 2006-08-31
I've got an install of 6.06 server and apache is being terribly slow. I'm not that great at troubleshooting linux so I have no idea where to start. This is just my test server so fortunately i'm not doing this in production, right? ;)

So, if I do top while a request is happening I see multiple instances of Apache showing up which I believe is normal, but it takes upwards of 15 seconds to load pages wether they're plain HTML or PHP/MySQL. Some apache threads take 50-60% of processor power and some even hit 80-90%. Something is struggling and I don't know what. 

Pretty much all I have on this machine is the LAMP install with a few other components. I've tried doing a CGI setup to see if that was any faster but its just as slow as the apache module.

SMB is fast when browsing directories, SSH is plenty fast.

When I connect to a remote machine via the server's mysql client the responses are fast.

i just don't know where to look...

Any help is appreciated.

Thanks.

---

### Post by mssever on 2006-08-31
Are there any errors in the logs in /var/log/apache or /var/log? I suspect that there is a problem somewhere with your Apache configuration, but it's hard to say without knowing more.

---

### Post by Gipetto on 2006-08-31
I see no errors in the logs. I have custom logging set up and get no errors in the general apache2 log nor in my sites rotated log files.

I went ahead and checked all the logs in /var/log and found no oddities in any of them.

---

### Post by mssever on 2006-08-31
Was Apache fast at one time on that install?

---

### Post by Gipetto on 2006-08-31
No. Never has been.

---

### Post by mssever on 2006-09-01
hmm...

Are you connecting to the server from the local machine by using [http://localhost]("http://localhost?")? If not, try that and see if it makes a difference.

---

### Post by Gipetto on 2006-09-01
Access from Localhost is fast, though I checked this after turning off some services like dialup and raid services (as well as a couple of others - a co-worker linux geek helped) and we also set noatime in the fstab.

It is a bit faster now both remote and from curl & links on the server but there's still a bit of a lag.

One oddity I just noticed was that PHP reports a 4 second load time on some pages that take 10+ seconds to load. So it seems that though PHP is running a bit slow as well its actually building the pages faster than Apache is sending them out.

I should also note that the website code running on a production server is fast, and that loading the site from the remote web host is faster than loading it from the test server which is local - actually running on the same switch as my machine, so there's not subnetting issues inbetween.

---

### Post by mssever on 2006-09-01
The fact that Apache is fast when accessed from localhost--and the 4 second PHP time--suggests to me that your bottleneck isn't Apache but something in the networking stack or hardware. I would suggest two things: First, use the Listen directive to explicitly bind apache to 127.0.0.1:80 and your server's IP(s):80. Next, try pinging your server--and let the ping go on for a while. My guess is that you'll notice some dropped packets.

My first suspicion is some bit of network hardware. Apache runs fine for most people, so I don't think it's software--unless it's software that doesn't play nice with particular hardware.

I realize that some protocols (SSH, SMB, etc.) work normally. But I believe that http is less fault-tolerant than most.

---

### Post by Gipetto on 2006-09-01
Oh, man... we did some more diagnostics on the machine and found the CPU fan was dead. One good thing about old machines is that they won't seize without a cpu fan.

Replacing the CPU module by scavenging the "recycle" pile got me a similar CPU but with a noisy fan but a working machine.

Now, when my page tells me a 4 second page time it really is a 4 second page time. Now I just have to figure out the 3 second difference between the test server and the production server. Its not processor speed as the old test server was 233mhz and was faster than this one that is 500mhz. Gotta love the frankenputers.

---

### Post by David Corrales on 2006-09-02
Maybe Apache is doing reverse DNS queries which would of course slow things down.

---

### Post by Gipetto on 2006-09-02
David - that was actually one of my first thoughts as well... but it is not on.

---

### Post by David Corrales on 2006-09-02
Maybe a different kernel? Server vs Desktop kernel?

---

