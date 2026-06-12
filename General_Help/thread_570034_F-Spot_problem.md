---
title: "F-Spot problem"
date: 2007-10-07
forum: General Help
---

### Post by kosy on 2007-10-07
I get an error while using F-Spot when editing or uploading certain images to Flickr or other gallery. There is some library bug seen here that seems to do make this error:
[http://bugzilla.gnome.org/show_bug.cgi?id=382382](http://bugzilla.gnome.org/show_bug.cgi?id=382382)

How can I install this update to try it out?

I did also download new version of F-Spot 0.4.0. but when installing I get this error when typing make: make: *** No targets specified and no makefile found.  Stop.

I am newbe so be patient:)

I am using Ubuntu 7.04

kosy

---

### Post by cameronw on 2007-10-10
Hi there,
> I did also download new version of F-Spot 0.4.0. but when installing I get this error when typing make: make: *** No targets specified and no makefile found. Stop.This is a error that beginners commonly get stuck on.
Simply put this into Terminal as you may not have the required packages installed to build from source code:
```
sudo apt-get install build-essential

```Alternatively you could update F-Spot through Synaptic if a newer version is available.

---

