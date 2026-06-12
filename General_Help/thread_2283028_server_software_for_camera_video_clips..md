---
title: "server software for camera video clips."
date: 2015-06-18
forum: General Help
---

### Post by matt_symes on 2015-06-18
Hi all,

I'm looking for suggestions for a web based server software package to view motion triggered clips from a security camera in a web browser. It also needs to be able to relay the real time feeds from the cameras in a web browser. 

The server software needs needs to be able to authenticate any connected clients. These cameras are private.

The server needs to relay the feed from the cameras in real time to any connected and authorised clients.

It needs to be secure so I'll be using https for both uploading the clips and for viewing the clips and for viewing the camera feeds in real time.

The clips need to be viewable as soon as they are uploaded and this needs to be automated. 

All the clips uploaded must be available in a way so that it is easy to identify them using thumbnails of the clips and preferably time-lined.

Multiple cameras need to be viewable from a single web page.

If possible, multiple accounts each separately authenticated, each with multiple cameras, need to be catered for.

The camera feeds and clips streams need to be viewable on phones,  tablets and computers so, although i don't want to, I'll transcode if  required.

Obviously i could roll my own but I'm looking for a package that can already do this or as near enough.

Any suggestions ?

Any suggestions for rolling my own as well would also be welcome.

Thanks and kind regards.

---

### Post by HermanAB on 2015-06-18
Hmm, it is called... wait for it... drum roll... motion.

apt-get install motion

---

### Post by dragonfly41 on 2015-06-18
Perhaps throw red5-server into the mix?

Runs as servlet on tomcat.

Might cause a clash of ports with motion pkg and so conf will need tweaks?

Another thought for user management is to connect apache2 front end server to tomcat7 back end server?

---

### Post by matt_symes on 2015-06-18
Hi

> **HermanAB said:**
> Hmm, it is called... wait for it... drum roll... motion.

apt-get install motion

I have used motion on a LAN but not on the Internet and i did wonder if i could use it.

Will this actually do what i need if i install it on a remote server, over the Internet, remote from the cameras ? Will it handle all the use cases i need ?

I will investigate more after your suggestion though.

Kind regards

---

### Post by matt_symes on 2015-06-18
Hi

> **dragonfly41 said:**
> Perhaps throw red5-server into the mix?

Runs as servlet on tomcat.

Might cause a clash of ports with motion pkg and so conf will need tweaks?

Another thought for user management is to connect apache2 front end server to tomcat7 back end server?

Interesting. Thanks.

This would be part of rolling my own solution along with motion as suggested by HermanAB. I was also going to look into zoneMinder to see if that could be used.

I was hoping for a package that would do most of it for me but if there isn't one then that is not too much of a problem.

Kind regards

---

