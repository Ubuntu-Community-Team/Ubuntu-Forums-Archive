---
title: "Video LAN Installation"
date: 2005-07-21
forum: General Help
---

### Post by eelozano on 2005-07-21
I am pretty new to linux and I do not understand which of these I would choose.

[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

Obviously none of the pre-compiled binaries will work, but they don't mention Ubuntu in the additional ones either.  Should I just download the source?

I am also wondering if someone could give me a hint on how to install it once I get the correct one.

make and make install are still kinda confusing to me.

---

### Post by Blues- on 2005-07-21
sudo apt-get install vlc

---

### Post by eelozano on 2005-07-21
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc


I'm using Hoary 5.04....vlc isn't included?

---

### Post by Holdem on 2005-07-21
You need to add the extra repositories.
Go here:
[http://www.frankandjacq.com/ubuntuguide/5.04/#extrarepositories](http://www.frankandjacq.com/ubuntuguide/5.04/#extrarepositories)
And then try the vlc install again. You can even use Synaptic (System-Administration-Synaptic)

---

### Post by eelozano on 2005-07-21
Thank you very much...that seemed to work.

---

