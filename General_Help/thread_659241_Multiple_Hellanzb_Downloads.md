---
title: "Multiple Hellanzb Downloads?"
date: 2008-01-05
forum: General Help
---

### Post by nfox on 2008-01-05
I'm using Hellanzb and have many files I want to get. The problem is that I can run it only once and cannot download more than one file at a time. Since my download speed is 6Mbps and I can only seem to get about 250Kb/sec per connection, multiple downloads would let me use all the bandwidth.
So...

How can I get Hellanzb to either download multiple (8,20,1000) files at a time?
How can I get Hellanzb to run multiple instances?


Any help is appreciated. I've searched 'the internets' and have found nothing yet.

---

### Post by markharding557 on 2008-01-05
do i understand you correctly? you want to download 8,201000 files at once?in muliple instances?omg!

---

### Post by nfox on 2008-01-06
Not quite. I meant 8 or 10 or whatever. 

I seem to max out between 200kb - 400kb -- favoring the mid 200's. With DownThemAll for Firefox, using 10 simultaneous connections, I can download at full speed. I want something like that for Hella. Problem is my Python skillz are zero. 

I know this is an app-related question but I have nary an idea.

I don't want multiple server connections -- I have one subscription. I need multiple concurrent downloads (pref. that I can specify)


For instance, hellanzb.conf has this line in it:
             connections = 8
I want something like this:
             concurrent downloads = sum bunch

---

### Post by HyperBaton on 2008-01-06
I can't say I understand very well. HellaNZB always tries to use all the connections it's allowed to make, and as far as I can tell it uses as much connections possible to download one single file at a time. You can see this if you run hellanzb as a terminal process (instead of daemon). It shows you how it utilizes it's connections. So if you just set the number of connections to the maximum allowed by your newsserver, you should be downloading at the maximum speed you are allowed to download at.

Please try to explain to me again if you want something completely different :)

---

### Post by nfox on 2008-01-06
My configuration says 8 connections at a time. That's spiffy but I would like 8*n where I can specify the value of n. 

I only run from the terminal and it goes like this:
```
 [1] some.file.r17
 [2] some.file.r17
 [3] some.file.r17
 [4] some.file.r17
 [5] 
 [6] 
 [7] 
 [8] 
Total 180.2 KB/s, 1Billion MB queued, ETA: too long
```

Which is fantastic for one file but I've a queue and I want it start getting used. I guess the crux of my situation is how to bypass this:

```

batman@titbox:~$ hellanzb

hellanzb v0.13 (config = /etc/hellanzb.conf)
Couldn't listen on 127.0.0.1:8760: (98, 'Address already in use').
Exiting: FatalError'>: Cannot bind to XML RPC port, is another hellanzb queue daemon already running?
batman@titbox:~$ []
```

How can I assign a range of ports to use for multiple files?

---

### Post by HyperBaton on 2008-01-07
Well, first of all, you seem to be only using 4 connections out of the 8 you want to use. This would mean that you are only allowed 4 connections by your newsserver. So whether you spend all 4 connections on one file, or you spend them on 4 files, you aren't going to get HellaNZB or any other download client to download any faster, cause that's where you're capped!

What kind of newsserver are you using, if I may ask? Is it provided by your ISP, or do you pay for it?

But to answer your question to use multiple instances of hellanzb, you can try these 2 options I suppose:

1) Copy your configfile and change the XML-RPC listen port. Then start hellanzb like this:
hellanzb --config=CONFIGFILELOCATION

2) Tell hellanzb directly what port to listen to:
hellanzb --rpc-port=RPCPORT

Let me know if any of these work.

---

