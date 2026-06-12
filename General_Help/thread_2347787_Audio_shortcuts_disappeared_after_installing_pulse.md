---
title: "Audio shortcuts disappeared after installing pulseaudio+jack"
date: 2016-12-28
forum: General Help
---

### Post by lucedan on 2016-12-28
Hello all,

I was installing Ardou in Ubuntu 16.10r, and wanted to connect it to Supercollider.
So I run these on the command line:

sudo apt-get install pulseaudio-module-jack
load-module module-jack-sink

As I was there, I said "why don't I connect everything to Jack? (e.g. browser)"

So I followed the tutorial "How to route everything to Jack": [https://www.youtube.com/watch?v=UVhRDU6Kcds](https://www.youtube.com/watch?v=UVhRDU6Kcds)

and added: 
load-module module-jack-sink
load-module module-jack-source

to /etc/pulse/default.pa

It worked great. Only problem is that now my shortcuts (ctrl+F10, F11, F12) on my X200CA don't work anymore.
Can someone help me to restore those shortcuts to raise and lower volume?

---

