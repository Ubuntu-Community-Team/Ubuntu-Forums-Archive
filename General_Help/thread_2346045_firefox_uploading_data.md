---
title: "firefox uploading data"
date: 2016-12-10
forum: General Help
---

### Post by jgw on 2016-12-10
I noticed that my system was doing a lot of uploading - for no reason I could see.  I ran sudo netstat -tp and got:
```
greg@greg:~$ sudo netstat -tp
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp    14456      0 192.168.0.9:57804       185.33.21.112:11027     ESTABLISHED 3996/rhythmbox  
tcp        0      0 192.168.0.9:41916       sea15s07-in-f14.1:https ESTABLISHED 1973/firefox    
tcp        0      0 192.168.0.9:41846       sea15s07-in-f14.1:https ESTABLISHED 1973/firefox    
tcp        0     35 192.168.0.9:42856       pc-in-f108.1e100.:pop3s ESTABLISHED 1969/thunderbird
tcp        0 173082 192.168.0.9:53454       daisy.ubuntu.com:https  ESTABLISHED 740/whoopsie    
tcp        0      0 192.168.0.9:41524       104.16.108.18:https     TIME_WAIT   -               
tcp        0      0 192.168.0.9:46244       151.101.129.69:http     TIME_WAIT   -               
tcp        0      0 192.168.0.9:52898       pixel.quantserve.c:http TIME_WAIT   -               
tcp        0      0 192.168.0.9:38900       ec2-52-11-156-128:https TIME_WAIT   -               
tcp        0      0 192.168.0.9:58208       e2.ycpi.vip.bra.y:https ESTABLISHED 1973/firefox    
tcp        0      0 192.168.0.9:37762       207-109-73-137.dia:http ESTABLISHED 1973/firefox    
tcp        0      0 192.168.0.9:55588       sea15s07-in-f14.1e:http ESTABLISHED 1973/firefox    
tcp        0      0 192.168.0.9:46246       151.101.129.69:http     TIME_WAIT   -               
tcp        0      0 192.168.0.9:37702       50.56.53.186:http       TIME_WAIT   -               
tcp        0      0 192.168.0.9:37682       50.56.53.186:http       TIME_WAIT   -               
tcp        0      0 192.168.0.9:52440       pr.comet.vip.bf1.:https ESTABLISHED 1973/firefox    
tcp        0      0 192.168.0.9:37770       207-109-73-137.dia:http TIME_WAIT   -               
tcp        0      0 192.168.0.9:38672       sea15s07-in-f67.1:https ESTABLISHED 1973/firefox    
tcp        0      0 192.168.0.9:52980       pr.comet.vip.bf1.:https ESTABLISHED 1973/firefox    
tcp        0      0 192.168.0.9:57988       151.101.193.69:https    ESTABLISHED 1973/firefox    
tcp        0      0 192.168.0.9:41520       104.16.108.18:https     ESTABLISHED 1973/firefox    
tcp        0      0 192.168.0.9:39870       feijoa.canonical.:https TIME_WAIT   -               
tcp        0      0 192.168.0.9:41522       104.16.108.18:https     TIME_WAIT   -               
tcp        0     46 192.168.0.9:51970       edge-star-mini-sh:https ESTABLISHED 1973/firefox    
tcp        0      0 192.168.0.9:36602       ph-in-f106.1e100.:https ESTABLISHED 1973/firefox    
tcp        0      0 192.168.0.9:39868       feijoa.canonical.:https TIME_WAIT   -               
tcp        0      0 192.168.0.9:35458       192.0.73.2:https        ESTABLISHED 1973/firefox    
tcp        0      0 192.168.0.9:37684       50.56.53.186:http       TIME_WAIT   -               
tcp        0      0 192.168.0.9:36904       pixel.quantserve.c:http TIME_WAIT   -               
tcp        0      0 192.168.0.9:37704       50.56.53.186:http       TIME_WAIT   -               
tcp        0      0 192.168.0.9:35460       192.0.73.2:https        TIME_WAIT   -               
tcp        0      0 192.168.0.9:37764       207-109-73-137.dia:http TIME_WAIT   -               
tcp        0      0 192.168.0.9:37774       207-109-73-137.dia:http TIME_WAIT   -               
tcp        0      0 192.168.0.9:41518       104.16.108.18:https     ESTABLISHED 1973/firefox    
tcp        0      0 192.168.0.9:45796       [www.sfe.sv4.as5392:http](www.sfe.sv4.as5392:http) ESTABLISHED 1973/firefox    
tcp        0      0 192.168.0.9:59696       ec2-54-186-23-154:https ESTABLISHED 1973/firefox    
tcp        0      0 192.168.0.9:52894       pixel.quantserve.c:http TIME_WAIT   -               
tcp        0      0 192.168.0.9:59546       stackoverflow.com:https ESTABLISHED 1973/firefox    
tcp        0      0 192.168.0.9:57880       104.16.108.18:http      ESTABLISHED 1973/firefox    
tcp        0      0 192.168.0.9:46902       ne1onepush.vip.ne:https ESTABLISHED 1973/firefox    
tcp        0      0 192.168.0.9:59168       e2.ycpi.vip.bra.y:https ESTABLISHED 1973/firefox    
tcp        0      0 192.168.0.9:39872       feijoa.canonical.:https TIME_WAIT   -               
tcp        0      0 192.168.0.9:46238       151.101.129.69:http     ESTABLISHED 1973/firefox    
```

I have no idea why this is happening.  I shut down each tab, one after another, and it made no difference until I shut down my home page (which also shutdown firefox).  When I restarted firefox it didn't start the uploading again.  My homepage, the only remaining tab before exiting firefox, is "my yahoo" (yahoo).  The upload was running full out (my upload speed is something like .4Mb (slooooow))  Anyway, if it happens again I will try and figure out just what its sending out.  

Just wondering if anybody else has experienced this or know what might be going on.

thank you ....

---

### Post by Keith_Helms on 2016-12-11
Yahoo preloads and refreshes a lot of stuff in the background.  It's probably behind most of what you're seeing.  As soon as I browsed over to yahoo.com the list of connections shot up to about 25.

---

### Post by &amp;KyT$0P# on 2016-12-11
Let's take another look at that netstat output -
> ```
$ sudo netstat -tp
Active Internet connections (w/o servers)
Proto Recv-Q [COLOR="#FF0000"]**Send-Q**[/COLOR] Local Address           Foreign Address         State       PID/Program name
...
tcp        0 [COLOR="#FF0000"]**173082**[/COLOR]     ...:53454           daisy.ubuntu.com:https  ESTABLISHED 740/whoopsie    
...
tcp        0     [COLOR="#FF0000"]**46**[/COLOR]     ...:51970           edge-star-mini-sh:https ESTABLISHED 1973/firefox    

```
That's trimmed down to A) the entry showing the most uploading, and B) the **only** Firefox entry with any uploading.

Just FWIW.

---

### Post by jgw on 2016-12-11
Thank you for the replies ...........

I found out a couple of things.  The first is that if you check "www.sfe.sv4.as5392:http" I found it was a bad actor.  then I checked the firewall and see that I neglected to install it.  After I did install it the uploading seems to have stopped.  I wonder, is there a way to see what I would be downloading?

Thanks again!

---

### Post by &amp;KyT$0P# on 2016-12-11
> **jgw said:**
> I wonder, is there a way to see what I would be downloading?
Try Wireshark.  It's available in the package repositories.

---

