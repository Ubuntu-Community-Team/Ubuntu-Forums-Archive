---
title: "FTP Speed issues"
date: 2024-07-10
forum: General Help
---

### Post by theyikes on 2024-07-10
Hello! I have a question that I'm hoping someone can help me out with.

in short, i have an ftp server setup on my Kubuntu [FONT=monospace][COLOR=#000000]24.04[/COLOR]
. 

I can upload stuff and download it but the transfer speed is brutal slow.

I can't seem to find any working fix for Kubuntu.

Is this beyond fixing?

Thanks

The Yikes[/FONT]

---

### Post by currentshaft on 2024-07-10
What is "brutal slow"? What are you using to measure speed? How is the networking configured (wired, wireless, etc)? And why are you using FTP versus a more modern protocol?

---

### Post by dragonfly41 on 2024-07-10
Since you are in Kubuntu have you tried Krusader .. [https://docs.kde.org/stable5/en/krusader/krusader/remote-connections.html](https://docs.kde.org/stable5/en/krusader/krusader/remote-connections.html)
or FileZilla?

---

### Post by deadflowr on 2024-07-10
Which ftp-server?
There are a bunch.

---

### Post by theyikes on 2024-07-11
Vsftpd.

---

### Post by TheFu on 2024-07-11
If you want to see what the connections between two systems on your LAN could possibly achieve, as the theoretical max, use **iperf3** to test.  You'll never get transfers faster than that.  For GigE, the typical iperf3 tests will show 920-940 Mbps.  That's the possible network performance without any specific  protocol overhead.  Every file transfer protocol has overhead and is dependent on the speed of the storage for reading the information to be transferred and writing that information on the other side.  Disk bufferes (i.e. RAM) can hide this upto the limit of free RAM in the system, but for anything so large that you notice a performance problem, it is likely that after 5-10GB, RAM will be full and the transfers will slow to whatever the storage writing the data can handle.  This is all pretty clear.

If you want raw performance and don't care about security, use **netcat** to transfer files.

If you care about security and uploats, use sftp - sftp-server is built-into the openssh-server package which is well understood for how to secure it.

If you just want to download files quickly, use a tiny read-only webserver that is run for a few minutes from the directory with the files to be shared.  
```
$ python3 -m http.server 8000
```

You can tune your storage for specific performance based on the sort of files being transferred.  One of the easiest things to improve performance is to ensure the disk isn't full.  Next, ensure power management isn't enabled for the disks and lastly, avoid USB interfaces.  The USB storage protocol doesn't fully support the SCSI/SATA/eSATA protocol API and this can degrade performance.  Of course, of the source and target storage systems are both NVMe, you probably have the fastest storage possible already, unless you bought the off-brand or 2nd tier SSD devices without any onboard cache.  Stick with Samsung or SanDisk "Pro" models and that's the sweet spot for cost, total capacity, and performance.

If you want help, we'll need to know what "brutally slow" means.  We need bps (bits per second), since that's the standard for network transfers and disk write speeds.  Don't confuse bits and bytes.

While I'm here, I have to say this.  Plain FTP should have died off in 2002. We've had better options, more secure options, that work with our firewalls more cleanly over 20 yrs.  I really wish plain FTP would be removed from the Linux Tests.  I haven't setup a plain FTP server since the 1990s, because where I worked didn't allow it to be used.  Since the late 1990s, I've worked at 5 companies, so it isn't a single company with overly strict policies. It is industry standard NOT to use plain FTP.

---

