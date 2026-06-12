---
title: "Error on sudo apt-get update"
date: 2007-07-03
forum: General Help
---

### Post by miLl3niUm on 2007-07-03
I get this when i type sudo apt-get update (at the last lines):

```
Get:4 http://www.virtualbox.org feisty Release.gpg [189B]                      
Ign http://www.virtualbox.org feisty/non-free Translation-en_US                
Hit http://www.virtualbox.org feisty Release                                   
Err http://www.virtualbox.org feisty Release                                   
  
Get:5 http://www.virtualbox.org feisty Release [556B]                          
Ign http://www.virtualbox.org feisty Release                                   
Ign http://www.virtualbox.org feisty/non-free Packages                         
Hit http://www.virtualbox.org feisty/non-free Packages                         
Fetched 748B in 12s (61B/s)                                                    
Reading package lists... Done
W: GPG error: http://www.virtualbox.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 390EC3FF927CCC73
W: You may want to run apt-get update to correct these problems

```

---

### Post by ashwin_cse on 2007-07-03
if virutalbox site is trusted by you, then you have to import the gpg key of the site to your pc.

---

### Post by miLl3niUm on 2007-07-03
Emmm.... how?

---

### Post by notwen on 2007-07-03
[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads") says 

```
apt-key add innotek.asc
```


Hope this helps. =]

---

### Post by xunil76 on 2007-12-23
sorry for bringing this old thread back up, but i just had the same problem and had to modify the below to get it to work......

> **notwen said:**
> [http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads") says 

```
apt-key add innotek.asc
```


Hope this helps. =]
more specifically, in Ubuntu you'd have to download the innotek.asc file, then browse to the directory where you saved it and run the command:

```
sudo apt-key add innotek.asc
```

hope that helps anyone else that comes across this problem

---

