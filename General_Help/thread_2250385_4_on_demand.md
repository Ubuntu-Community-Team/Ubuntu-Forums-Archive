---
title: "4 on demand"
date: 2014-10-28
forum: General Help
---

### Post by UncleMonty on 2014-10-28
Have any ubuntu users had any trouble streaming videos on 4od? [http://www.channel4.com/programmes/4od](http://www.channel4.com/programmes/4od) I can't get anything to load and am trying to ascertain where the problem lies.

---

### Post by JazzPotato on 2014-10-28
I vaguely remember having problems with this myself, but I have not used that service in a long time.
Can you watch youtube videos/bbc iplayer? The problem may be because flash is not installed.

---

### Post by ajgreeny on 2014-10-28
I have managed to get it running on 12.04 but not yet tried on 14.04.

There is a long thread at [http://linuxformat.com/forums/viewtopic.php?f=5&t=16746&p=115468&hilit=4od#p115468](http://linuxformat.com/forums/viewtopic.php?f=5&t=16746&p=115468&hilit=4od#p115468) which you may find helpful; it looks as if you may need hal installed to get it working, which will need a ppa by the looks of it.

Good luck.

---

### Post by robbie 348 on 2014-10-28
This worked for me on 14.04. sudo add-apt-repository ppa:mjblenner/ppa-hal    sudo apt-get update    sudo apt-get install hal

---

### Post by UncleMonty on 2014-10-28
Hal fixed it. Thanks.

---

### Post by don62 on 2014-12-08
> **robbie 348 said:**
> This worked for me on 14.04. sudo add-apt-repository ppa:mjblenner/ppa-hal    sudo apt-get update    sudo apt-get install hal
Thanks a lot robbie, worked for me too, after fiddling with other good intentioned solutions which didn't.
I also had to figure out that each "sudo" had to be entered separately - I know, I'm an Ubuntu numpty.:lolflag:

---

