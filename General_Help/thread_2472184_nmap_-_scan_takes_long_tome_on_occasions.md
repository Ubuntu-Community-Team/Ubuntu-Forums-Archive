---
title: "nmap - scan takes long tome on occasions"
date: 2022-02-20
forum: General Help
---

### Post by Geoff_Lane on 2022-02-20
Sometimes if I install a new network device I issue **nmap 192.168.1.1/24 **to find out what port numbers are associated with addresses to identify a device.

Normally this completes in under 30 seconds (or thereabouts) but on occasions it takes a long time.  Appreciate there are numerous flags one can add to affect what nmap does but the actions of the default seem erratic.

Yesterday this was the readout when I pressed return on a number of occasions;

```
Starting Nmap 7.80 ( https://nmap.org ) at 2022-02-19 20:38 GMT

Stats: 0:00:45 elapsed; 242 hosts completed (14 up), 14 undergoing Connect Scan
Connect Scan Timing: About 93.24% done; ETC: 20:39 (0:00:03 remaining)

Stats: 0:00:56 elapsed; 242 hosts completed (14 up), 14 undergoing Connect Scan
Connect Scan Timing: About 93.32% done; ETC: 20:39 (0:00:04 remaining)

Stats: 0:01:10 elapsed; 242 hosts completed (14 up), 14 undergoing Connect Scan
Connect Scan Timing: About 93.42% done; ETC: 20:39 (0:00:05 remaining)

Stats: 0:01:24 elapsed; 242 hosts completed (14 up), 14 undergoing Connect Scan
Connect Scan Timing: About 93.51% done; ETC: 20:39 (0:00:06 remaining)

Stats: 0:01:39 elapsed; 242 hosts completed (14 up), 14 undergoing Connect Scan
Connect Scan Timing: About 93.61% done; ETC: 20:40 (0:00:06 remaining)

Stats: 0:04:28 elapsed; 242 hosts completed (14 up), 14 undergoing Connect Scan
Connect Scan Timing: About 94.80% done; ETC: 20:43 (0:00:14 remaining)

Stats: 0:06:10 elapsed; 242 hosts completed (14 up), 14 undergoing Connect Scan
Connect Scan Timing: About 95.53% done; ETC: 20:44 (0:00:17 remaining)

Stats: 0:07:19 elapsed; 242 hosts completed (14 up), 14 undergoing Connect Scan
Connect Scan Timing: About 96.03% done; ETC: 20:46 (0:00:18 remaining)

Stats: 0:10:05 elapsed; 242 hosts completed (14 up), 14 undergoing Connect Scan
Connect Scan Timing: About 97.21% done; ETC: 20:48 (0:00:17 remaining)

```

You can see it took around 10 minutes, time remaining actually increased from three seconds up to 18 but bore no relevance to the actual time remaining, it seemed stuck on 242 hosts completed for ages.

Why would this suddenly take ages when normally it is quite quick?

Subsequently found this may be due to timeouts when a host is not responding and fact it scans around a 1000 ports per host.

Got over it by adding -p 22 option to see what are running ssh

Geoff

---

### Post by MAFoElffen on 2022-02-20
Could you please post the commands/options you used to try to recreate this problem?

---

### Post by SeijiSensei on 2022-02-21
For fast scans I recommend first identifying the target host in question with
```
nmap -sP network_address
```
for instance,
```
nmap -sP 192.168.1.0/24
```

That should let you identify the new device.  Then run
```
sudo nmap -sT ip.of.new.device
```
to run a TCP scan against that machine. 

You can add a "-v" to the options to get a more "verbose" reply.

You can run ping scans (-sP) as an ordinary user; for TCP scans you need to use sudo.

---

### Post by Geoff_Lane on 2022-02-22
> **MAFoElffen said:**
> Could you please post the commands/options you used to try to recreate this problem?

Hi, thanks for interest, I did state on first line the code I used, it was merely nmap [B]192.168.1.1/24

[/B]I was more querying why on occasions it often completed quickly but sometimes took a longish time.  Guessed it may have been due to timeouts.

[B]Geoff

[/B]

---

### Post by Geoff_Lane on 2022-02-22
> **SeijiSensei said:**
> For fast scans I recommend first identifying the target host in question with
```
nmap -sP network_address
```
for instance,
```
nmap -sP 192.168.1.0/24
```

That should let you identify the new device.  Then run
```
sudo nmap -sT ip.of.new.device
```
to run a TCP scan against that machine. 

You can add a "-v" to the options to get a more "verbose" reply.

You can run ping scans (-sP) as an ordinary user; for TCP scans you need to use sudo.

Thanks, that was useful.

Discovered another useful option, usually I am looking for a Raspberry Pi running ssh so give nmap the -p 22.80  option to look for ssh and web server.

Geoff

---

### Post by SeijiSensei on 2022-02-22
> **Geoff_Lane said:**
>  it was merely nmap 192.168.1.1/24

That's the wrong specification for a class-C subnet.  It should read 192.168.1.**0**/24.

---

