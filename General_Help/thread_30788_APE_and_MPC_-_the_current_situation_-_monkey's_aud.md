---
title: "APE and MPC - the current situation - monkey's audio, musepack"
date: 2005-04-30
forum: General Help
---

### Post by seguso on 2005-04-30
Hello there,

I would like to make the point of the current situation about ape and mpc under hoary.

In order to listen to ape and mpc files with xmms, under hoary, I had to install the package xmms-dev, then compile and install the following packages:

* mac

* xmms-mac

* libmusepack

* xmms-musepack

, which I had to download from the following sites:

* [http://sourceforge.net/project/showfiles.php?group_id=123827](http://sourceforge.net/project/showfiles.php?group_id=123827)

* [http://svn.musepack.net/websvn/listing.php?repname=mdt&path=%2F&sc=0](http://svn.musepack.net/websvn/listing.php?repname=mdt&path=%2F&sc=0)


It was a simple matter of ./configure, make, and sudo make install. With an exception: while configuring "mac", I did

./configure --enable-backward=yes 

--

Why did I  choose xmms and not gstreamer? Actually, I can also listen to some APE files, with the gstreamer plugin "gstreamer0.8-monkeysaudio". But it does not work with newer ape files. And there is no gstreamer plugin for MPCs anyway.

---

I hope you find this useful. Now I have some questions:

1. The packages on the debian repository "rarewares" do not work. apt complains about a wrong version of libc. Do you confirm?

2. Do you know if  there is an equivalent repository for ubuntu? If not, is it in the works?

3. Do you know exactly why mac and xmms-mac cannot be included in ubuntu by default? It is my understanding that there are no patents on the APE format, so I don't see why such programs would be legally doubious.


Thanks  :smile:

---

### Post by Slo Mo Snail on 2005-05-28
There IS a gstreamer plugin for musepack since gst-plugins-0.8.6 around ;)

---

