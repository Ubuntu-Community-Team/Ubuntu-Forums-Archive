---
title: "Playing some stream with Firefox"
date: 2006-08-20
forum: General Help
---

### Post by jpmonette on 2006-08-20
Hi

I'm not able to watch some stream video files on the Internet with Firefox. When I look in about:plugins, i already have VLC, Quicktime, Real, Windows Media Player and mplayer. When I try to look at a video:

[http://altair.videolan.org/~dionoea/vlc-plugin-demo/](http://altair.videolan.org/~dionoea/vlc-plugin-demo/)

I get a black square with the text (no picture) in it. I don't know where this come from, I searched "(no picture)" on the ubuntu forums and find nothing, same for Google.

Thanks

---

### Post by H.E. Pennypacker on 2006-08-20
Get the MPlayer plug-in.  It works well, including on that website.

---

### Post by jpmonette on 2006-08-20
I already have it, I think it's VLC by default, that's why MPlayer isnt working.. But I don't know how to uninstall it.

---

### Post by H.E. Pennypacker on 2006-08-23
How to uninstall what?  The trick is in having the Mplayer plug-in handle your Firefox media.

Have any other plug-ins uninstalled to make sure they don't take over.  If you have the MPlayer plug-in currently installed and working, you'll definitely know, because before  a video/audio file plays, you'll see the name MPlayer.

Start up Synaptic, and remove anything you see like Totem Firefox plug-in.  If there's one for VLC, remove it.  Make sure Mplayer plug-in is installed, and that should be it.

---

### Post by jpmonette on 2006-08-25
Thanks a lot, it's working! :)

---

### Post by yossman on 2006-08-27
thanks to pennypacker, that was exactly the problem here too -- VLC was handling the firefox quicktime playing facility, which resulted in the 'black screen with '(no picture)'' showing.  uninstalling all VLC-related packages via synaptic fixed the problem, once we had w32codecs and mplayer + mozilla-mplayer installed. ;-)

thanks for the help!


yossman

---

### Post by tedrogers on 2006-11-25
I have done all of this and all I get is the MPlayer plugin gray screen with no picture...I've got sound though.

It shows me that the feed is loading / buffered etc and I get the link info on the screen.

I'm trying to stream a .WMV of Spanish TV from [www.madridman.com/multimedia.html](www.madridman.com/multimedia.html)

Prior to this I had the black screen with sound only (no video).

Any ideas?

---

### Post by tedrogers on 2006-11-26
I have since found that other wmv files play fine....it just seems to be this website which is problematic.

[http://www.madridman.com/multimedia.html](http://www.madridman.com/multimedia.html)

Can someone else try and play the top stream in the TV section called TeleMadrid SAT - its about half way down the page.

If it doesn't work for you either then it's a common problem.

Thanks.

---

