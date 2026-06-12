---
title: "Erlang on edgy"
date: 2007-02-02
forum: General Help
---

### Post by Uakari on 2007-02-02
I am using edgy in a vmware -server, I have a minimal install.  I installed the following packages:

gcc, libssl-dev, m4, openssl-devel, java-gcj-compat, java-gcj-compat-dev

This is the second day I have attempted to install erlang, yesterday I attempted to compile the source otp_src_R10B but after running into issues (listed on many different forums),  even after deleting the source and re-configuring it, after all packages mentioned above were installed; it still would not work.

I would now like to use apt-get and install erlang, but there doesn't appear to be an erlang package, even after trying backports:

root@server:/etc/apt# apt-cache search erlang
root@server:/etc/apt# 

I have done some fierce googling, but couldn't find anything.  Is there a tutorial that specifically addresses edgy and erlang?

---

