---
title: "Large transfers over the Internet stalling."
date: 2021-04-02
forum: General Help
---

### Post by rsteinmetz70112 on 2021-04-02
I am attempting to create an offsite repository of the data on a number of servers in two office locations. The total amount of data is 1.5TB on 5 different computers 3-500GB on each machine. This is not a backup but more of an archive in case of emergency. Years ago our main computers were in an office in New Orleans after Katrina and we had to mount a "rescue mission" to retrieve them. That eventually worked out fine, however the computers might have been damaged so I've been working to create an automatic archive. I have one both offices data in each office and that has been the case for a while this is an additional layer of insurance. This is also in addition to the versioned backups we have on each site.

I have set up a computer at a third site and have been working to replicate all of the data there. I chose to use rsync so I could run periodic crontabs to update the information and resume transfers if they failed. I believe that should be sufficient for our purposes, one of the offices has already been transferred without problems and the crontabs are keeping it up to date.  However I've run into a problem with initial copies on the other office. The transfered archive keep stalling after what looks like a random amount of time.  I can log into both ends at the same time and see what is going on. Neither computer is heavily loaded and the transfers run at a good rate but after a time simply stop sending data. There is no error message it just stops sending or receiving data. I can stop the interrupt the transfer and restart it but it eventually dies again. The office that has been transfered uses the same ISP as the archive site (Comcast) the office that is stalling uses ATT Fiber.

Any ideas how I can determine what is causing the transfers to stop?

---

### Post by SeijiSensei on 2021-04-02
Do you use the "-v" option in rsync to get a list of the transferred files? Does the failing transfer always hang at the same file, or does it happen randomly?

---

### Post by HermanAB on 2021-04-03
Rsync has a bandwidth parameter.  Slowing it down a bit can prevent complete stalls in my experience.

Also check your equipment ethernet ports for packet errors indicative of hardware failures or bad cables.

---

### Post by rsteinmetz70112 on 2021-04-03
> **SeijiSensei said:**
> Do you use the "-v" option in rsync to get a list of the transferred files? Does the failing transfer always hang at the same file, or does it happen randomly?

I use the -v parameter when I'm doing it from the command line but not in the crontabs. Both stall.  When it stalls if I simply run the same command again it picks up with untransfered files.

---

### Post by rsteinmetz70112 on 2021-04-03
> **HermanAB said:**
> Rsync has a bandwidth parameter.  Slowing it down a bit can prevent complete stalls in my experience.

Also check your equipment ethernet ports for packet errors indicative of hardware failures or bad cables.


I'll try reducing the bandwidth, that may also prevent rsync from taking over the connections and slowing other traffic.

I don't think it is the local network since I've been able to make large transfers from other locations. I have no indication that the location I'm having issues with is behaving badly. It actually has more bandwith than the local connection.

---

### Post by HermanAB on 2021-04-03
The programs ifconfig or ip can show you whether there are packet errors (bad HW).

---

### Post by rsteinmetz70112 on 2021-04-04
I tried reducing the bandwidth and that didn't help, it just slowed down the transfers.

I don't see a problem at this end ifconfig is showing zero errors , of course the problem could be upstream from my computer. It's possible the remote site has some issues. I can login in there and try to see.

---

### Post by rsteinmetz70112 on 2021-04-06
I've now gotten a new error:

```
rsync -avz user@remote.domain.com:/files /backups/remote/
...
packet_write_wait: Connection to XX.XX.XX.XX port 22: Broken pipe
rsync: connection unexpectedly closed (12610026455 bytes received so far) [receiver]
rsync error: error in rsync protocol data stream (code 12) at io.c(235) [receiver=3.1.2]
rsync: connection unexpectedly closed (1381386 bytes received so far) [generator]
rsync error: unexplained error (code 255) at io.c(235) [generator=3.1.2]
```

---

### Post by HermanAB on 2021-04-06
It looks like packets are getting dropped somewhere along the line.

You need to devise a script that will watch rsync and if necessary, kill it and restart it.

---

### Post by rsteinmetz70112 on 2021-04-06
Now I've got two problems.

First the transfer is stalling, that is it stops transferring without any errors
Second it errors out like the last post.

---

### Post by HermanAB on 2021-04-06
Different simptoms of the same problem - lost packets, causing rsync to get confused.

---

