---
title: "FTP says upload completed, but error"
date: 2006-12-28
forum: General Help
---

### Post by Flavian on 2006-12-28
When I try to upload a file from my harddrive I face the following weird error.
gFTP as well as KFTP say that the transfer is completed, but in fact brakes up at 7%
There is not even a file fragment remaining on the server, it is as if I never uploaded anything.

Here is the Log from gFTP maybe someone knows what's going on there.
I had this error a bunch of times before but I dunno how it worked again :(

> 
Successfully changed local directory to /media/Fat32
Received URL file:///media/Fat32/equilibrium_feat_hatebreed-hollow_ground.wmv
Could not change local directory to /media/Fat32/equilibrium_feat_hatebreed-hollow_ground.wmv: Not a directory
Loading directory listing /videos from server (LC_TIME=en_GB.UTF-8)
PASV
227 Entering Passive Mode (213,202,225,41,83,119).
LIST -aL
150 Opening ASCII mode data connection for file list
226 Transfer complete.
PASV
227 Entering Passive Mode (213,202,225,41,216,186).
STOR /videos/equilibrium_feat_hatebreed-hollow_ground.wmv
150 Opening BINARY mode data connection for /videos/equilibrium_feat_hatebreed-hollow_ground.wmv
Error: Could not write to socket: Broken pipe
Disconnecting from site flavian.fl.ohost.de
Could not download /media/Fat32/equilibrium_feat_hatebreed-hollow_ground.wmv from local filesystem
Error: Remote site local filesystem disconnected. Will reconnect in 30 seconds
Looking up flavian.fl.ohost.de
Trying server6.ohost.de:21
Connected to flavian.fl.ohost.de:21
220 Welcome. FTP Server ready.
USER flavian
331 Password required for flavian.
PASS xxxx
230 User flavian logged in.
SYST
215 UNIX Type: L8
TYPE I
200 Type set to I
CWD /videos
250 CWD command successful
PASV
227 Entering Passive Mode (213,202,225,41,17,121).
REST 1679360
350 Restarting at 1679360. Send STORE or RETRIEVE to initiate transfer
STOR /videos/equilibrium_feat_hatebreed-hollow_ground.wmv
550 /videos/equilibrium_feat_hatebreed-hollow_ground.wmv: No such file or directory
Loading directory listing /videos from server (LC_TIME=en_GB.UTF-8)
PASV
227 Entering Passive Mode (213,202,225,41,203,181).
LIST -aL
150 Opening ASCII mode data connection for file list
226 Transfer complete.


---

### Post by taurus on 2006-12-28
Are you sure the file is resided on your server since it can't find it???

```

**550 /videos/equilibrium_feat_hatebreed-hollow_ground.wmv: _No such file or directory_**

```

---

### Post by Flavian on 2006-12-28
> **Flavian said:**
> 
There is not even a file fragment remaining on the server, it is as if I never uploaded anything.

Nope, the file isn't on the server! - I don't know what the deal is? I am really clueless...
Any ideas?? ](*,)

---

### Post by taurus on 2006-12-28
So you want to upload "equilibrium_feat_hatebreed-hollow_ground.wmv" from your machine to a server!  Try to see if you can do that from a terminal!

Applications -> Accessories -> Terminal
```
ftp <your server IP>
<your login name>
<your password>
bin
put equilibrium_feat_hatebreed-hollow_ground.wmv
bye
```

p.s. Make sure you have the write permission to that server!!!

---

### Post by Flavian on 2006-12-29
Thanks man!
I found the problem. I told my brother to try to upload it via Windows... and it broke at 7% as well. So I figured it must have been the server. Then I chose another FTP server I had, and it worked fine.
Weird... :/
But thanks for your help!
Flo

---

