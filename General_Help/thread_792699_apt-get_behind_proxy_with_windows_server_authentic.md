---
title: "apt-get behind proxy with windows server authentication"
date: 2008-05-13
forum: General Help
---

### Post by Mr.nano on 2008-05-13
Hi all,

MY problem is that apt-get in not working behind proxy since i chnged my password to contain special characters.

Before the problem arose i used:

Edited my .bashrc file in my home directory to cantain the following line at the end:

export http_proxy=http://nano:oldpassword@proxy_ip_addr:8080
export ftp_proxy=ftp://nano:oldpassword@proxy_ip_addr:8080

it worked just great for me!!! But wen I changed my password to newp@$$ it stopped working! I realized that special characters have to be encoded in URLs so i did:

export http_proxy=http://nano:newp%40%24%24@proxy_ip_addr:8080
export ftp_proxy=ftp://nano:newp%40%24%24@proxy_ip_addr:8080

it is still failing to authenticate and is not working!

I,m authenticating to our domain's Windows 2003 server, if it does make any difference at all?

So any kind of help will be highly appreciated!!!

---

