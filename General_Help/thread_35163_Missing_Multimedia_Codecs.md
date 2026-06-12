---
title: "Missing Multimedia Codecs"
date: 2005-05-17
forum: General Help
---

### Post by kozmo on 2005-05-17
I did a fresh install of Hoarty two days ago and updated the repositories.

But when I do:
[B]sudo apt-get install w32codecs
sudo apt-get install liblame0[/B]

It returns "couldn't find package"

I did a Reload in Synaptic, then a search for these packages and they cannot be found.

I was trying the follow the instructions in the [Ubuntu Guide - Installing Multimedia Codecs](http://www.ubuntuguide.org/#codecs) 

Any idea where these packages are and why they are missing?

---

### Post by bored2k on 2005-05-17
[QUOTE=kozmo]I did a fresh install of Hoarty two days ago and updated the repositories.

But when I do:
[B]sudo apt-get install w32codecs
sudo apt-get install liblame0[/B]

It returns "couldn't find package"

I did a Reload in Synaptic, then a search for these packages and they cannot be found.

I was trying the follow the instructions in the [Ubuntu Guide - Installing Multimedia Codecs](http://www.ubuntuguide.org/#codecs) 

Any idea where these packages are and why they are missing?[/QUOTE]
 Did you add the correct repositories ?
If not do this: (this is not the regular method)
```

sudo echo deb ftp://ftp.nerim.net/debian-marillat testing main >> /etc/apt/sources.list && sudo apt-get update && sudo apt-get install w32codecs
```.

---

### Post by tread on 2005-05-18
I think you missed the part in the guide where it shows you how to add new repositories .. 
> 
Q: How to install Multimedia Codecs?
Read General Notes
Read How to add extra repositories?

wget -c [http://frankandjacq.com/ubuntuguide/gstreamer0.8-lame_0.8.8-0.1_i386.deb](http://frankandjacq.com/ubuntuguide/gstreamer0.8-lame_0.8.8-0.1_i386.deb)
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install w32codecs
sudo apt-get install liblame0
sudo dpkg -i gstreamer0.8-lame_0.8.8-0.1_i386.deb
gst-register-0.8


---

