---
title: "How do I input this???"
date: 2007-09-14
forum: General Help
---

### Post by iheartubuntu on 2007-09-14
I wanna watch soccer games via sopcast. Sopcast requires Mplayer to work, so now Im looking to install mplayer.

I came across this info here:
[COLOR="DarkRed"][B]
Extract the files into a temporary directory. Change to the directory into which you downloaded the files and enter the following commands:

./configure --enable-gui
make
su (if you're not already root)
make install [/B][/COLOR]

But dont know what to do with it! Where do I enter the commands? Any tips? Im completely new to Ubuntu so I think once I figure this out, I'll have no probs with other software in the future.

Thanks for any help!

---

### Post by mcduck on 2007-09-14
Just go to Applications/Add/Remove.., find MPlayer and install it. No need to download anything yourself. This is not Windows, we can install stuff like this with much less work :D

[How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

(Make sure that you have 'Show all available applications' in the upper right corner)

---

### Post by iheartubuntu on 2007-09-14
I can see Mplayer in the "add/remove" programs list, but when I go to install it, everything freezes and wont install. Im trying to install it some other way.

---

### Post by Maestro23 on 2007-09-14
> **shirteesdotnet said:**
> I wanna watch soccer games via sopcast. Sopcast requires Mplayer to work, so now Im looking to install mplayer.

I came across this info here:
[COLOR="DarkRed"][B]
Extract the files into a temporary directory. Change to the directory into which you downloaded the files and enter the following commands:

./configure --enable-gui
make
su (if you're not already root)
make install [/B][/COLOR]

But dont know what to do with it! Where do I enter the commands? Any tips? Im completely new to Ubuntu so I think once I figure this out, I'll have no probs with other software in the future.

Thanks for any help!

You are trying to compile a program from source, which can be a real pain for people new to linux.  I would highly suggest against it until you are more comfortable.

Can you not go into your (Menu Bar)>> System... Synaptic Pkg Mgr... Search for MPlayer... Mark for Install.

---

### Post by iheartubuntu on 2007-09-14
> **Maestro23 said:**
> You are trying to compile a program from source, which can be a real pain for people new to linux.  I would highly suggest against it until you are more comfortable.

Can you not go into your (Menu Bar)>> System... Synaptic Pkg Mgr... Search for MPlayer... Mark for Install.


mplayer is not listed. only "kmplayer" is.

---

### Post by Maestro23 on 2007-09-14
> **shirteesdotnet said:**
> mplayer is not listed. only "kmplayer" is.


Hmm.. Open a terminal and type:

> apt-cache search mplayer

---

