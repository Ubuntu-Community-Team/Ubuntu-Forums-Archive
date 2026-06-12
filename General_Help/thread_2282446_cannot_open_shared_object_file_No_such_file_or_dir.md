---
title: "cannot open shared object file: No such file or directory (ERRORS)"
date: 2015-06-14
forum: General Help
---

### Post by prabin3 on 2015-06-14
I'm getting these two errors, i'm using ubuntu 12.04 32 bit

libmysqlclient_r.so.15: cannot open shared object file: No such file or directory
libcrypto.so.0.9.8: cannot open shared object file: No such file or directory

I'm in really need of help to get this sorted, 

Thank you

---

### Post by Steve_Horan on 2015-06-14
Seems you may have uninstalled those shared libs.

> sudo apt-get update
sudo apt-get install libssl0.9.8 libmysqlclient-dev libcrypto++9

Should get you straight.

---

### Post by prabin3 on 2015-06-14
> **Steve_Horan said:**
> Seems you may have uninstalled those shared libs.



Should get you straight.

Thank you, second error fixed but this one is still left

[COLOR=#000000]libmysqlclient_r.so.15: cannot open shared object file: No such file or directory

[/COLOR]this is one hurdle to over come :/

---

### Post by Steve_Horan on 2015-06-14
Ahh lets go ahead and install these then: 

> apt-get install libmysql++-dev libmysql++3

Those should contain this shared library.

---

### Post by prabin3 on 2015-06-14
> **Steve_Horan said:**
> Ahh lets go ahead and install these then: 



Those should contain this shared library.

It still doesnt work, ive tried both the commands in my vps but keep getting this same error

---

### Post by Steve_Horan on 2015-06-14
Hmm... On your VPS, any chance you are attempting to run Ruby on Rails?

The only other package you could try to install would be libmysqlclient18.

---

### Post by prabin3 on 2015-06-14
> **Steve_Horan said:**
> Hmm... On your VPS, any chance you are attempting to run Ruby on Rails?

The only other package you could try to install would be libmysqlclient18.

im trying to run mysql plugin for a game server called SAMP, is there no other way i can make this up?

---

### Post by steeldriver on 2015-06-14
These sorts of errors sometimes occur when you try to run 32-bit software on a 64-bit platform without the necessary 32-bit library support: can you provide any more information about SAMP such as where you got it / how exactly you installed it?

---

### Post by Holger_Gehrke on 2015-06-14
If SAMP is GTA:San Andreas Multiplayer, then the mysql plugin you're trying to install was compiled for Ubuntu 10.04, which had an older version of libmysqlclient_r.so (Version 15). Current Ubuntu Versions have the newer version 18. Two things you can try: make a (symbolic) link named libmysqlclient_r.so.15 in the directory where libmysqlclient_r.so.18 resides (should be in /usr/lib/i386-linux-gnu/); if the two versions are sufficiently compatible, this should do it. Otherwise -- or if you don't have write access to that directory -- you can try to get the library from somewhere, put in in the directory where your plugin is and set LD_LIBRARY_PATH to include that directory.

**Edit:** or you could download a current version of the plugin from the [github address]("https://github.com/pBlueG/SA-MP-MySQL/releases") given on forum.sa-mp.com, that's compiled against Version 18 and even includes a statically linked version of the plugin ...

---

