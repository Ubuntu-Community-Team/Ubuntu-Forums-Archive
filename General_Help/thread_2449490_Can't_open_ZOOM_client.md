---
title: "Can't open ZOOM client"
date: 2020-08-27
forum: General Help
---

### Post by plutobuntu on 2020-08-27
I installed the ZOOM client from the store, but when I try to launch the app nothing happens, it doesn't open.

I'm using Xubuntu 64 bits.

---

### Post by deadflowr on 2020-08-27
By Store do you mean the Software Store?
I think that version is the snap version.
perhaps see if true
```
snap list
```
then if true and is the snap version try
```
snap run zoom-client
```
and see what it posts.

Edit:
Or remove it.
and grab the deb version from here:
[https://zoom.us/download?os=linux]("https://zoom.us/download?os=linux")
(Use the 16.04+ version as that means it runs on everything from 16.04 and up to the latest version, 20.04)

How to install the deb: [https://support.zoom.us/hc/en-us/articles/204206269-Installing-or-updating-Zoom-on-Linux#h_adcc0b66-b2f4-468b-bc7a-12c182f354b7]("https://support.zoom.us/hc/en-us/articles/204206269-Installing-or-updating-Zoom-on-Linux#h_adcc0b66-b2f4-468b-bc7a-12c182f354b7")

---

### Post by plutobuntu on 2020-08-27
> **deadflowr said:**
> By Store do you mean the Software Store?
I think that version is the snap version.
perhaps see if true
```
snap list
```
then if true and is the snap version try
```
snap run zoom-client
```
and see what it posts.

Edit:
Or remove it.
and grab the deb version from here:
[https://zoom.us/download?os=linux](https://zoom.us/download?os=linux)
(Use the 16.04+ version as that means it runs on everything from 16.04 and up to the latest version, 20.04)

How to install the deb: [https://support.zoom.us/hc/en-us/articles/204206269-Installing-or-updating-Zoom-on-Linux#h_adcc0b66-b2f4-468b-bc7a-12c182f354b7](https://support.zoom.us/hc/en-us/articles/204206269-Installing-or-updating-Zoom-on-Linux#h_adcc0b66-b2f4-468b-bc7a-12c182f354b7)


The terminal says (after the second command you posted) "no such file or directory" a bunch of times. Then it says "xrdb: permission denied" and "xrdb: can't open display ':0.0'"
zoom client. I guess it doesn't mean something good.

...So I tried grabbing the deb and installed it and it worked. Thanks! :D

---

