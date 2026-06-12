---
title: "Apt does not update"
date: 2021-06-05
forum: General Help
---

### Post by charm_quark on 2021-06-05
Good day, I keep having this error when running apt-get. I am currently using 20.04LTS


```
Err:1 http://archive.ubuntu.com/ubuntu focal InRelease
  Connection failed [IP: 91.189.88.152 80]
Err:2 http://archive.ubuntu.com/ubuntu focal-updates InRelease
  Connection failed [IP: 91.189.88.152 80]
Err:3 http://archive.ubuntu.com/ubuntu focal-backports InRelease
  Connection failed [IP: 91.189.88.152 80]
Err:4 http://archive.ubuntu.com/ubuntu focal-security InRelease
  Connection failed [IP: 91.189.88.152 80]
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/focal/InRelease  Connection failed [IP: 91.189.88.152 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease  Connection failed [IP: 91.189.88.152 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/focal-backports/InRelease  Connection failed [IP: 91.189.88.152 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/focal-security/InRelease  Connection failed [IP: 91.189.88.152 80]
W: Some index files failed to download. They have been ignored, or old ones used instead.


```
I did a wireshark capture, and recieved an internal server error. [IMG]https://imgur.com/yxj1MCH[/IMG] ([https://imgur.com/yxj1MCH](https://imgur.com/yxj1MCH)) 
Note, my net is stable. Any suggestions.[IMG]https://imgur.com/yxj1MCH[/IMG]

---

### Post by QIII on 2021-06-06
Those resources appear to be up now.  They may have been down momentarily.

Try again.

---

### Post by charm_quark on 2021-06-06
I still seem to be having the error. I initially thought it was the network ( I changed it), then I thought it was the pc ( formatted it).

Except this time on wireshark the pcap does not say much [https://imgur.com/7K1DQ8E](https://imgur.com/7K1DQ8E)

I have further proceeded to change the mirror addresses

> a@a$ sudo apt-get update
Err:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease
  Connection failed [IP: 91.189.91.39 80]
Err:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease
  Connection failed [IP: 91.189.91.38 80]
Err:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease
  Connection failed [IP: 91.189.91.39 80]
0% [Waiting for headers]^C
a@a:~$ sudo apt-get update
0% [Waiting for headers]^C
a@a:~$ sudo apt-get update
Err:1 [http://archive.ubuntu.mirror.ba/ubuntu](http://archive.ubuntu.mirror.ba/ubuntu) focal InRelease
  Connection failed [IP: 85.209.96.20 80]
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.mirror.ba/ubuntu/dists/focal/InRelease](http://archive.ubuntu.mirror.ba/ubuntu/dists/focal/InRelease)  Connection failed [IP: 85.209.96.20 80]
W: Some index files failed to download. They have been ignored, or old ones used instead.
hms@hms:~$ sudo vi /etc/apt/sources.list
hms@hms:~$ sudo apt-get update
Err:1 [http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za) focal InRelease
  500  Internal Server Error [IP: 155.232.191.230 80]
Reading package lists... Done
W: Failed to fetch [http://ubuntu.mirror.ac.za/dists/focal/InRelease](http://ubuntu.mirror.ac.za/dists/focal/InRelease)  500  Internal Server Error [IP: 155.232.191.230 80]
W: Some index files failed to download. They have been ignored, or old ones used instead.
a@a:~$


---

### Post by deadflowr on 2021-06-06
Are you using any kind of proxy?

---

### Post by ActionParsnip on 2021-06-06
Does the system have internet access in a browser OK?

---

### Post by charm_quark on 2021-06-07
I am not using any Proxy, and the system has access to internet ( Snap works perfectly) 

On that note. I tried to do an apt-update ( note : it was configured to .za) 

> a@a:~$ sudo apt-get update
Hit:1 [https://ubuntu.mirror.ac.za](https://ubuntu.mirror.ac.za) focal InRelease
Reading package lists... Done


I had not changed anything. I then went to enable the rest of the repo's

> a@a:~$ sudo apt-get update
0% [Waiting for headers] [Waiting for headers] [Waiting for headers]
0% [Waiting for headers] [Waiting for headers] [Waiting for headers]
Get:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease [12.1 kB]
Get:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal/partner amd64 Packages [856 B]
Get:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal/partner Translation-en [384 B]
Hit:4 [https://ubuntu.mirror.ac.za](https://ubuntu.mirror.ac.za) focal InRelease
Err:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease
  Connection failed [IP: 91.189.91.38 80]
Err:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease
  Connection failed [IP: 91.189.91.39 80]
Err:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-security InRelease
  Connection failed [IP: 91.189.91.38 80]
Fetched 13.3 kB in 3min 1s (73 B/s)
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/focal-updates/InRel](http://us.archive.ubuntu.com/ubuntu/dists/focal-updates/InRel)                                         ease  Connection failed [IP: 91.189.91.38 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/focal/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/focal/InRelease)  Co                                         nnection failed [IP: 91.189.91.39 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/focal-security/InRe](http://us.archive.ubuntu.com/ubuntu/dists/focal-security/InRe)                                         lease  Connection failed [IP: 91.189.91.38 80]
W: Some index files failed to download. They have been ignored, or old ones used                                          instead.


So i realized that "us" is failing, but "za" is ok. So I modified source.list to use only .za

```
a@a:~$ sudo apt-get updateHit:3 http://archive.canonical.com/ubuntu focal InRelease
Hit:1 https://ubuntu.mirror.ac.za focal InRelease
Get:2 https://ubuntu.mirror.ac.za focal-updates InRelease [114 kB]
Get:4 https://ubuntu.mirror.ac.za focal/universe amd64 Packages [8,628 kB]
Get:5 https://ubuntu.mirror.ac.za focal/universe Translation-en [5,124 kB]
Get:6 https://ubuntu.mirror.ac.za focal/universe amd64 c-n-f Metadata [265 kB]
Get:7 https://ubuntu.mirror.ac.za focal-updates/main amd64 Packages [1,026 kB]
Get:8 https://ubuntu.mirror.ac.za focal-updates/main Translation-en [229 kB]
Get:9 https://ubuntu.mirror.ac.za focal-updates/main amd64 c-n-f Metadata [13.5kB]
Get:10 https://ubuntu.mirror.ac.za focal-updates/restricted amd64 Packages [266 kB]
Get:11 https://ubuntu.mirror.ac.za focal-updates/restricted Translation-en [38.9 kB]
Get:12 https://ubuntu.mirror.ac.za focal-updates/restricted amd64 c-n-f Metadata [456 B]
Get:13 https://ubuntu.mirror.ac.za focal-updates/universe amd64 Packages [779 kB]
Get:14 https://ubuntu.mirror.ac.za focal-updates/universe Translation-en [168 kB]
Get:15 https://ubuntu.mirror.ac.za focal-updates/universe amd64 c-n-f Metadata [17.6 kB]
Fetched 16.7 MB in 56s (296 kB/s)
Reading package lists... Done
```

And this worked.

But may anyone please tell me why it was failing ?

PS: I had also changed it to the default 'archive.ubuntu.com' and still had Connection failed [IP: 91.189.91.38 80] errors

---

