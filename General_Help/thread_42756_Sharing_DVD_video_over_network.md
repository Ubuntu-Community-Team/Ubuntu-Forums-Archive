---
title: "Sharing DVD video over network"
date: 2005-06-19
forum: General Help
---

### Post by randomjunk on 2005-06-19
I'm trying to setup my Linux box as a file server mainly to talk to a small computer that sits under my TV to play video files. This all works fine the the Linux box sharing samba folders really well.

But now I want to be able to share the DVD drive in the linux box, so that I can play DVDs on the Windows box under the TV. This works fine with unencrypted DVDs, but breaks with any encrypted ones.

Is there any way to share a video DVD and have it automatically decrypted by libdvdcss or whatever? Ideally in a way which is compatible with Windows Media Center.

Thanks.

(the TV computer can't have it's own DVD drive, there isn't space)

---

### Post by smoon on 2005-06-19
I think [VLC respectively VLS](http://www.videolan.org/) can do it. But I've no ideo if Windows box is able to play the streams back...
But why do you use Windows for the box under your TV at all? There are very good Linux alternatives to a Windowes based Media Center, like [MythTV](http://www.mythtv.org/), [Freevo](http://freevo.sourceforge.net/) or the [NMM Multimedia-Box](http://www.networkmultimedia.org/NMM/Status/MMBox/index.html).

---

### Post by randomjunk on 2005-06-19
because irritatingly, my housemate owns the box under the TV and insists on Windows... I own the Linux box... this isn't gonna change anytime soon so I'm looking for a decent solution -- we can use VLC to do the stream, and it works great, but you can't use the IR remote to activate it all. The DVD menus don't work either.

Media Center will play a DVD from a samba folder, but only if it is unencrypted, so I'm having to spend 20mins ripping the DVD first, which is irritating. I am trying to find a way of doing this on the fly.

Thanks

---

### Post by randomjunk on 2005-07-22
Not many people seem to need to do this, but anyway.
To answer my own question, it's possible if you do the following:

Install fuse, you can find ubuntu packages.

Compile the attached c file.
```
gcc -o dvdcssfs -D_FILE_OFFSET_BITS=64 dvdcssfs.c -ldvdread -lfuse -lpthread
```
Put the bianry in the path somewhere eg /usr/bin

Set up a samba share with the following options added:
```
preexec dvdcssfs <a mount point> --dvd <dvd device eg /dev/dvd>
postexec fusermount -u <a mount point>
```

Tell your DVD playing software to play the shared folder -- and voila!

---

### Post by flamerail on 2006-05-13
I cant get it to work.. sais invalid token at 'newline'..
Also how do I compile the c tile?
thanks!

---

