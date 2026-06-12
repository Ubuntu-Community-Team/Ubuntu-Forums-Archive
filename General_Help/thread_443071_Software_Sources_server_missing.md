---
title: "Software Sources server missing?"
date: 2007-05-14
forum: General Help
---

### Post by zodmaner on 2007-05-14
Hi, I'm running Ubuntu 7.04 and recently downloaded and used EasyUbuntu to install some restricted codec. While I was installing the codec my software sources server (which is in Thailand) don't have all the necessary dependency, so I go into preferences and changes software sources server to Main server and the codec install just fine.

Now the problem is after that I can't find Thailand software sources server! (there isn't even a Thailand listed in the selection!) So can anyone help me out here? How do I find the server in my country. Thanks in advance. :)

---

### Post by Rippey on 2007-05-14
try source-o-matic
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
you'll probably find what you need there

---

### Post by hyperair on 2007-05-14
In your software sources, look for the Taiwan server (tw.archive.ubuntu.com) otherwise, you'll face the same case I did. I live in Malaysia, and and tried to use my.archive.ubuntu.com as my server. I then found out that it actually referred me back to the main server, and gave me slow speeds >.< Chances are there is no server for your country as well, or I'd use that server, since Thailand is so close to Malaysia.

When I told the software sources to pick the best server, it returned the Indonesian server, but that's less updated than the Taiwan server. Same goes for the Singaporean server.

---

### Post by zodmaner on 2007-05-15
Thanks for answer guys! I've followed the link to source-o-matic and it help me find my local server url. But just as hyperair say, it seems that it also seems to referred back to the main server. 

Anyway, when the Ubuntu was updating its source list, I notices that it fails to retrieve the following package:

Translation-en_US

Which is silly, because, well, do you need a translation for English? Anyway, this error occur in every server I tried to use. So what with this problem? And what is this package in the first place?

---

### Post by hyperair on 2007-05-15
My guess is that the Translation file is to give the descriptions in your locale's language and whatnot. en_US is a variant of English, and you may have en_GB as well, and others. It's built into APT to look for these files I reckon. Most servers only provide the descriptions of their packages in English, and hence you don't have the Translation file in those servers.

Of course, what I just said was merely speculation by me, but I don't think I'm far from the truth.

---

### Post by zodmaner on 2007-05-15
Hm... That is interesting. So anyone else had this problem/error?

---

