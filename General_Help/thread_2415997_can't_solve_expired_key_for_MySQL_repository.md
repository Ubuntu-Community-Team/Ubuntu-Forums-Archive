---
title: "can't solve expired key for MySQL repository"
date: 2019-04-03
forum: General Help
---

### Post by megunticook on 2019-04-03
I haven't run into this issue yet, but I seem to have a bad signature key for my MySQL repository on my Ubuntu 18.04.2 server. I've done a bunch of research and tried to fix it but am coming up short. Here's what happened when I try to run sudo apt update:

```
ubuntu@ip-177-77-77-772:~$ sudo apt updateHit:1 http://us-east-2.ec2.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://us-east-2.ec2.archive.ubuntu.com/ubuntu bionic-updates InRelease
Hit:3 http://us-east-2.ec2.archive.ubuntu.com/ubuntu bionic-backports InRelease
Hit:4 http://security.ubuntu.com/ubuntu bionic-security InRelease
Get:5 http://repo.mysql.com/apt/ubuntu bionic InRelease [16.9 kB]
Hit:6 http://ppa.launchpad.net/certbot/certbot/ubuntu bionic InRelease
Hit:7 http://ppa.launchpad.net/nginx/stable/ubuntu bionic InRelease
Hit:8 http://nginx.org/packages/ubuntu bionic InRelease
Err:5 http://repo.mysql.com/apt/ubuntu bionic InRelease
  The following signatures were invalid: EXPKEYSIG 8C718D3B5072E1F5 MySQL Releas                                                                                                                                      e Engineering <mysql-build@oss.oracle.com>
Fetched 16.9 kB in 1s (24.6 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up to date.
W: An error occurred during the signature verification. The repository is not up                                                                                                                                      dated and the previous index files will be used. GPG error: http://repo.mysql.co                                                                                                                                      m/apt/ubuntu bionic InRelease: The following signatures were invalid: EXPKEYSIG                                                                                                                                       8C718D3B5072E1F5 MySQL Release Engineering <mysql-build@oss.oracle.com>
W: Failed to fetch http://repo.mysql.com/apt/ubuntu/dists/bionic/InRelease  The                                                                                                                                       following signatures were invalid: EXPKEYSIG 8C718D3B5072E1F5 MySQL Release Engi                                                                                                                                      neering <mysql-build@oss.oracle.com>
W: Some index files failed to download. They have been ignored, or old ones used                                                                                                                                       instead.

```

Following advice I found online, I deleted the expired key, then tried adding the current key:

```
ubuntu@ip-177-77-77-777:~$ gpg --recv-keys 5072E1F5gpg: key 8C718D3B5072E1F5: 3 duplicate signatures removed
gpg: key 8C718D3B5072E1F5: 98 signatures not checked due to missing keys
gpg: key 8C718D3B5072E1F5: "MySQL Release Engineering <mysql-build@oss.oracle.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

But I'm still not able to update. How do I fix this? Thanks.

```
ubuntu@ip-177-77-77-777:~$ sudo apt updateHit:1 http://us-east-2.ec2.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://us-east-2.ec2.archive.ubuntu.com/ubuntu bionic-updates InRelease
Hit:3 http://us-east-2.ec2.archive.ubuntu.com/ubuntu bionic-backports InRelease
Hit:4 http://security.ubuntu.com/ubuntu bionic-security InRelease
Get:5 http://repo.mysql.com/apt/ubuntu bionic InRelease [16.9 kB]
Hit:6 http://ppa.launchpad.net/certbot/certbot/ubuntu bionic InRelease
Hit:7 http://nginx.org/packages/ubuntu bionic InRelease
Hit:8 http://ppa.launchpad.net/nginx/stable/ubuntu bionic InRelease
Err:5 http://repo.mysql.com/apt/ubuntu bionic InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8C718D3B5072E1F5
Fetched 16.9 kB in 1s (25.6 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up to date.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://repo.mysql.com/apt/ubuntu bionic InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8C718D3B5072E1F5
W: Failed to fetch http://repo.mysql.com/apt/ubuntu/dists/bionic/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8C718D3B5072E1F5
W: Some index files failed to download. They have been ignored, or old ones used instead.



```

---

### Post by huff2 on 2019-04-03
This is the issue:

"gpg: key **8C718D3B5072E1F5**: "MySQL Release Engineering <mysql-build@oss.oracle.com>" not changed"

"EXPKEYSIG [B]8C718D3B5072E1F5" 

[/B]The error message you received said that the bolded key above is expired. When you tried to get the new public key, the response said that the same key was not changed. The issue is that you still have not obtained a copy of the new public key.

[https://dev.mysql.com/doc/refman/8.0/en/checking-gpg-signature.html](https://dev.mysql.com/doc/refman/8.0/en/checking-gpg-signature.html) Follow this link to a copy of the new key. You will see that they have the option for you to copy and paste the key.

You will want to copy and paste it into a text file, which can be saved anywhere, really. Then you will want to add the key with:

sudo apt-key add /path/to/your/key.txt 

This will add that key to your apt key ring. 

Remove the expired key by sudo apt-key del[B] 8C718D3B5072E1F5
[/B]
Try to update again. Let me know if this helps.

---

### Post by megunticook on 2019-04-03
Bingo, thanks. 

I tried to add the key earlier by copying pasting text to a file but must've done something wrong. Appreciate it much.

---

### Post by huff2 on 2019-04-03
No problem! Can you mark this thread as solved if the problem is solved for you? Thanks!

---

