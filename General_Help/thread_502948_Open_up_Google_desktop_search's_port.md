---
title: "Open up Google desktop search's port"
date: 2007-07-17
forum: General Help
---

### Post by Mujaheiden on 2007-07-17
Hi,

I just installed google-desktop-search, and immediately found a document I was looking for for ages :) It is really better then beagle :(

I also mounted a fileserver connected to my pc, so now I want to make the GDS available to my colleagues as well.

The search interface comes up at [http://127.0.0.1:34853/?hl=en_US&s=7WAuZv4Q11KDXtuyfQp2QlIaKps](http://127.0.0.1:34853/?hl=en_US&s=7WAuZv4Q11KDXtuyfQp2QlIaKps)

However, if I use my real IP addres - for arguments sake - 137.120.1.1, the desktop search is not reachable, so  [http://137.120.1.1:34853/?hl=en_US&s=7WAuZv4Q11KDXtuyfQp2QlIaKps](http://137.120.1.1:34853/?hl=en_US&s=7WAuZv4Q11KDXtuyfQp2QlIaKps)

Is it an apache port which is blocked, or is it GDS which blocks this?

I intend only to index the fileserver, and we are not on a public network, so I have no privacy concerns.

:edit:
All right, I know now this needs a [Proxy]("http://www.projectcomputing.com/resources/desktopProxy/") on my pc which translates a remote call into a local one. But how to implement?

---

