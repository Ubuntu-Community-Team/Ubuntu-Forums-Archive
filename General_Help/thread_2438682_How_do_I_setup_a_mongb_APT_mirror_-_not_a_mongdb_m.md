---
title: "How do I setup a mongb APT mirror - not a mongdb mirror."
date: 2020-03-16
forum: General Help
---

### Post by myjess on 2020-03-16
Hi,

I need to setup an apt mirror for mongodb on a DMZ server.

I have read lots of posts that discuss keys, but they are all installing mongodb on the server itself, not actually creating a mongdb mirror that other servers can connect to, to do an apt update/apt upgrade.

The repo server as I call it has apt mirror for ubuntu 18.04.
I have also installed the keys for mongodb 18.04 on this repo server and can see two keys for mongodb when I execute apt-key list.

Whenever I try to apt update on another remote server pointed to this repo server, when it comes to mongodb, apt say InRelease is not signed.

Thanks for any help given.

---

