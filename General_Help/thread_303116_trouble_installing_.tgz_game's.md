---
title: "trouble installing .tgz game's"
date: 2006-11-19
forum: General Help
---

### Post by DougieFresh4U on 2006-11-19
I have downloaded 2 games from The Linux Tome. I can never get a tar file installed. The downloads are as follows- xmahjongg_3.5.tar.gz and the other- mahjong_lin.tgz -  Is there some way to install through terminal. At this point files are still in little download window. I would be glad if some one could help me out, I kind of need a little hand holding on this one. Thank you

---

### Post by David_T on 2006-11-19
If you're just starting out, I would recommend installing software through Synaptic if possible, just for the most trouble-free experience.  You may very well be able to find the games you want through apt/synaptic/aptitude.  See this tutorial:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If you just want to be able to unpack the .tgz or .tar.gz file, the terminal command for that would be

tar -xvzf xmahjongg_3.5.tar.gz

Then, you'd look for a file called README or INSTALL inside of the folder it creates.

---

### Post by DougieFresh4U on 2006-11-19
Thank you David_T! I got lucky on the xmahjong, when I went to the install file it directed me to a deb site and I ran it there and the package installer instqalled it but I do not know where it put it. I have searched menues and can not find it. could you possibly point me in a direction as to where do I find it now? The other game had a read me but did not say  how to install. thanks

---

### Post by taurus on 2006-11-19
Did you build it from ./configure && make && sudo make install?  If that's the case, then it's probably in /usr/local/bin so open a terminal and run it as

```
xmahjongg
```
Otherwise, most binaries are installed in /usr/bin...

---

### Post by igknighted on 2006-11-19
try typing xmahjong into the terminal, if that doesnt work try /usr/bin/xmahjong.  If neither of these work, off the top of my head I'm not sure where it would have been put.  Once you find the right command you can make a launcher button or use alacarte to create a menu entry.

---

### Post by DougieFresh4U on 2006-11-19
Thanks for all replies. I typed xmahjongg in the terminal and my screen went bonkers and computer restarted itself, scared me :eek:  So I went looking in Places and I found it in usr/ bin  or some thing like that. I tried to make a launcher but it didn't work out. I'll keep working at it. thank you. P.S. taurus-my little sister (mustangsally started laughing when she saw your reply. she's visiting me here(to cold in NYC)

---

### Post by taurus on 2006-11-19
Did you compile it from source yourself, ./configure && make && sudo make install?  There is something with it then if it crashes your machine when you try to run it!  Open a terminal and see what does it say with this command!

```
ldd /usr/bin/xmahjongg
```

p.s.  So, she's in the Mickey Mouse town now, eh!  It's freakin cold up here too especially the next few days...  Brrrrrrrrrrr!  ](*,)

---

### Post by DougieFresh4U on 2006-11-19
dougie@DougiesToyBox:~$ ldd /usr/bin/xmahjongg
ldd: /usr/bin/xmahjongg: No such file or directory
Not worry, I got it. /home/dougie/Mah_Mahjong and got the launcher. thanks. Yeah, I'm about to ship Her silly *** home in a day or two. They brought there horses here no less. expensive hobby she's got. Now to enjoy some peaceful mahjong

---

### Post by taurus on 2006-11-19
She has horses in NYC!!!  :shock:

---

