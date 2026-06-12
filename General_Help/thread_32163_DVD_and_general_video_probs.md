---
title: "DVD and general video probs"
date: 2005-05-06
forum: General Help
---

### Post by remin on 2005-05-06
Gday, im very new to linux as ive been a windows user all my life, so please be patient with me.
Anyway, im having problems playing back DVD's in Totem, the video and and sound are extremely sluggish causing the sound mostly to skip.
Any thoughts on how to fix this?

Also, I have quite a few DivX and Xvid movies lying around that cannot play atm, ive installed the gstreamer0.8-plugins and the w32codecs, obviously DivX and Xvid are not included in these, so is there any sources around that I could use.

Finally, I have onboard sound and a soundcard installed on my system, how do I make the soundcard the default output device?
Thanks in advance.

---

### Post by enquiry on 2005-05-06
[QUOTE=remin]
Anyway, im having problems playing back DVD's in Totem, the video and and sound are extremely sluggish causing the sound mostly to skip.
Any thoughts on how to fix this?[/QUOTE]
If you have an nVidia video card, follow this instruction for how to install the driver: [http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver) If you have an ATI card follow this instruction: [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

Make sure DMA is turned on. Do this by adding these lines at the bottom of /etc/hdparm.conf:

/dev/dvd {
dma = on
}

You may use the text editor gedit to edit the file by typing 
sudo gedit /etc/hdparm.conf
in the terminal.

I belive you will find a solution to your problems by searching the forum. I've found ubuntuguide.org very usefull. Also search in the wiki: [http://www.ubuntulinux.org/wiki/FrontPage/searchwiki](http://www.ubuntulinux.org/wiki/FrontPage/searchwiki)

---

