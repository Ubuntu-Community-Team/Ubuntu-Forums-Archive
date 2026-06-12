---
title: "Xbox 360 media"
date: 2008-05-08
forum: General Help
---

### Post by Doby on 2008-05-08
I have ubuntu 7.10 running on an external hard drive, with xp pro running in a virtual box.  All my media is stored on another external hard drive.

I use windows media player on my orginal hard drive to stream all my media to my xbox 360, so I can watch my movies on my big screen, and listen to music on my real stereo system.

Is there anyway to use my ubuntu virtual xp setup to do the same as my xp machine?  This way I would lose xp as a main os altogether.

---

### Post by magickangaroo on 2008-05-10
hi

Can i suggest looking fuppes to directly stream media from the ubuntu machine to the xbox.  This will remove the need for the xp virtual machine. 

the fuppes site is here [http://fuppes.ulrich-voelkel.de/](http://fuppes.ulrich-voelkel.de/) with pretty good documentation for building from source, or via a pre packed (but out of date) deb.  

If fuppes isnt your thing you may want to look at ushare as well which is a bit easier.

I have attached my fuppes configs which are stored in ~/.fuppes/  as they can be a bit fiddly, so hopefully that will save you some time if you go that way.

finally if you did want to use a virtual xp machine can i suggest looking at virtualbox.  You can install the image and then when it comes to networking use bridged networking to put the virtual machine on the same network as you actual pc.  There is a lot of documentation on the virtualbox site so i wont cover that in detail unless you find you need help with that.


Hope that helps

/Mgk

---

