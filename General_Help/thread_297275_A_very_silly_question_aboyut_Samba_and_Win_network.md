---
title: "A very silly question aboyut Samba and Win networks"
date: 2006-11-10
forum: General Help
---

### Post by podunk on 2006-11-10
I just finished intergrating my Linux machines into the network

I can read Windows shares - but they can't read me.

This is the way it's supposed to be - yes? because I have ext3 in Linux and Windows doesn't work with that.

---

### Post by Beernut on 2006-11-10
I think what you are looking for is to install Samba on your linux systems and create shares.  That will allow you to access files on the linux computers from windows.  If you setup a samba server it is running on ext3 the windows computers don't know about it or even care they are just accessing a network share.  This may help [HOWTO: Setup Samba peer-to-peer with Windows]("http://http://ubuntuforums.org/showthread.php?t=202605&highlight=samba")

---

