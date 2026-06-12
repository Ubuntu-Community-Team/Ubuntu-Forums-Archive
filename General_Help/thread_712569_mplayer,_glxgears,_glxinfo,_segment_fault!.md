---
title: "mplayer, glxgears, glxinfo, segment fault!"
date: 2008-03-01
forum: General Help
---

### Post by 00arthuryu on 2008-03-01
heya
i am an absolute n00b so please bare with me :D
when i tried to install the latest official nvidia drivers from nvidia, they kinda didn't work and i could not start X.
Then i tried installing all the ubuntu-nvidia-packages by doing
```

sudo apt-get install nvidia-glx-new

```
This gave me a working desktop but without any 3D acceleration, so i tried installing the official nvidia drivers, to which i decided that doing this would solve the problem
```
sudo apt-get remove nvidia*
```
which was..... probably the worse thing i could of done lol
and now i can't even get X to start i've tried all combinations of the official drivers and/or the ubuntu packages

glxgear, doesn't work
glxinfo, doesn't work
mplayer doesn't work (which really confused me)

edit: after fiddling about, it seems that if i install the drivers through envy, i am able to run X, but mplayer, glxinfo etc. still doesn't work, i also seem to be lacking 3D acceleration once again

any help would be recieved with open arms :D
have a good day! and thank you for taking a look :)
Arthy

---

