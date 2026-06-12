---
title: "Problems with apt-get"
date: 2014-07-23
forum: General Help
---

### Post by mrkeef on 2014-07-23
So I was trying to upgrade my spotify client and I seem to have lost some critical files making it impossible to remove, upgrade or reinstall the client. 

To be clear, this is related to the package management not the actual client- I think.

At the moment I don't have a working copy of the client. But the computer thinks I do. In fact it thinks I have the latest available one.

If I try to remove what is there I get:

[INDENT]root@Amelia:/home/mrkeef# apt-get remove spotify-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  spotify-client
0 to upgrade, 0 to newly install, 1 to remove and 37 not to upgrade.
1 not fully installed or removed.
After this operation, 100 MB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 427370 files and directories currently installed.)
Removing spotify-client (1:0.9.4.183.g644e24e.428-1) ...
/var/lib/dpkg/info/spotify-client.prerm: 9: /var/lib/dpkg/info/spotify-client.prerm: ./unregister.sh: not found
dpkg: error processing package spotify-client (--remove):
 subprocess installed pre-removal script returned error exit status 127
/var/lib/dpkg/info/spotify-client.postinst: 5: /var/lib/dpkg/info/spotify-client.postinst: ./register.sh: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 spotify-client
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/INDENT]

Can you tell me how to fix this please?

---

### Post by steeldriver on 2014-07-23
Yes it sounds like some packages files were manually removed - you could try reinstalling it first

```

apt-get install --reinstall spotify-client

apt-get remove spotify-client

```

(as root - or with sudo). If that doesn't work there are other things you can try using the lower-level dpkg utility directly instead of apt-get.

---

### Post by mrkeef on 2014-07-23
Thanks for that, but it didn't work :( I pretty much got the same result

Setting up spotify-client (1:0.9.4.183.g644e24e.428-1) ...
/var/lib/dpkg/info/spotify-client.postinst: 5: /var/lib/dpkg/info/spotify-client.postinst: ./register.sh: not found
dpkg: error processing package spotify-client (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 spotify-client


I've tried dpkg also but no success.

---

### Post by mrkeef on 2014-07-23
In the end I took the sledgehammer approach- manually deleted all files and folders with "spotify" in the name then did apt-get update and apt-get install spotify-client and it's all happy :p

---

