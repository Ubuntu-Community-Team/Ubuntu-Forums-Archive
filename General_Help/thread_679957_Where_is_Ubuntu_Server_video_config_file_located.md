---
title: "Where is Ubuntu Server video config file located"
date: 2008-01-27
forum: General Help
---

### Post by er2183 on 2008-01-27
I am installing Ubuntu Server on an AMD PIC dectop. For an installation with X, such as Xubuntu, I need to edit xorg.conf to get the display working. In Ubuntu Server, there is no xorg.conf. 
I need to know where the video config file is located.

thank you.

---

### Post by taurus on 2008-01-27
Have you installed Xubuntu, yet?  It's in /etc/X11/xorg.conf.

```
cat /etc/X11/xorg.conf
```

---

### Post by er2183 on 2008-01-27
I know where it is for xubuntu. it's not there for ubuntu server.
I guess I can probably just install xubuntu and change the run level to 3 or something.

---

### Post by taurus on 2008-01-27
There is no /etc/X directory if you only installed the server version.  Therefore, you must first install xorg before you can configure /etc/X11/xorg.conf.  Installing Xubuntu will install X server for you automatically.

I am not sure I understand your second sentence.

---

### Post by nutts4life on 2008-02-12
HI there, 

I have the same problem I only want to install the command line xubuntu so i can build on top of it.

The full xubuntu package runs too slow.

Here's the problem:

 I want to install the command line xubuntu and then build xfce4 on top, so it's light weight.

But i can't boot up into the command line as it keeps failing when loading hardware drivers. 

Before i did the command line install i installed the full xubuntu install and exactly the same problem arised. 
BUT i could boot into the usb stick, mount the hda1 drive and modify the xorg.conf.

BUT with the command line install there is no xorg, but the same problem still occurs.

Basically this video problem still occurs with the command line interface. 

I'm not sure how all this works, but does the command line have some kind of video configuration?

See this wiki for more info on the installation process and the problem: [http://dectop.nfshost.com/wiki/index.php/%28X%29ubuntu_on_decTOP](http://dectop.nfshost.com/wiki/index.php/%28X%29ubuntu_on_decTOP)

Would be great if anybody could help!

nutts4life

---

