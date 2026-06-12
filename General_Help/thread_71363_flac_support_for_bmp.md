---
title: "flac support for bmp?"
date: 2005-10-03
forum: General Help
---

### Post by bigjoe on 2005-10-03
how to add flac support for beep media player?

thnx,
bj  :confused:

---

### Post by GrammatonCleric on 2005-11-17
Download the following...

[http://linuxjunkie.net/stuff/bmp_input_plugins.tgz]("http://linuxjunkie.net/stuff/bmp_input_plugins.tgz")

Extract the contents.

```


tar zxvf bmp_input_plugins.tgz


``` 
Change in the the extracted "Input" Directory.

```


cd Input/


``` 
Now copy the contents to the  /usr/lib/bmp/Input directory.

```


sudo cp * /usr/lib/bmp/Input


``` 
Launch Beep Media Player and try playing a .flac file or files.

GC

---

### Post by corax on 2007-01-21
Hi GrammatonCleric ! 

I tried your suggestion now I can play all types of file BUT .flac :-)

I can play .flac through VLC player (it uses gstreamer ) but I like to play in BMP and not in BMPx :-)

I read many forums about it. Nearly everybody says "copy or link the two .flac plugins from XMMS to /usr/lib/bmp/Input ...".

It isn't working for me ... :-(

BMP says when I try to open a .flac file:

```
Unable to play files.

The following files could not be played. Please check that:
1. they are accessible.
2. you have enabled the media plugins required.
```

Can you or someone please help ? 

Thanks !!

---

### Post by corax on 2007-03-05
bmp :) maybe ? anyone ? :-(

---

### Post by corax on 2007-05-31
Some additional information to anyone still has this problem :)

Project BMP has been moved to BMPx ...

(For those who don't like BMPx (like me) :) )

A new project has been forked form the original BMP called audacious - it can be installed through synaptic (aptitude) - which is a winamp clone for linux.

---

