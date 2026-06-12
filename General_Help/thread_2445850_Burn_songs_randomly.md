---
title: "Burn songs randomly"
date: 2020-06-20
forum: General Help
---

### Post by raleigh3 on 2020-06-20
I recorded 165 songs to my CD as mp3s.

But it recorded them in alphabetical order.

So it plays all the songs of one artist and then goes to the next etc.

I started renaming the files by song name first followed by the artist.

ex. disco_inferno_The_tramps.mp3

But that will take a long time.

Can those songs be recorded randomly on the cd?

Or maybe make the file dates modified all different?

Thanks.

---

### Post by Holger_Gehrke on 2020-06-20
I assume you're playing this disk on some kind of mp3-capable CD-player, if you're playing them on the PC then you should look at the playlist functionality of whatever player program you're using, they all allow reordering and some of them will shuffle a playlist randomly if you tell them to.

Most of the mp3 CD-players I've ever used in the past had the ability to play in random order, you might want to take a look in the manual of your device.

For renaming the files to a pattern along the lines of 'Songtitle - Album - Artist' many mp3-tag editors offer the ability to rename the files to match the tags and give a pattern for naming the files. Both easytag and kid3 can do it.

Reordering the files before burning is probably possible, but I've never seen options for that in any GUI burning application. You'd probably have to do it from the command line using genisoimage (see the man-page for all the many, many details) and then burn that image. Doing that might not help at all if the player itself sorts the files either by (path and) file names or according to their tags (I've had several portable mp3-CD-players over the years and I've seen both).

Giving the files names with a random number prepended might be helpful, something like 'for i in *mp3; do mv "$i" ${RANDOM}"$i";done' might help; but that also ends up giving you a fixed order (random, but fixed once the disk is burned).

Holger

---

### Post by raleigh3 on 2020-06-20
> **Holger_Gehrke said:**
> I assume you're playing this disk on some kind of mp3-capable CD-player, if you're playing them on the PC then you should look at the playlist functionality of whatever player program you're using, they all allow reordering and some of them will shuffle a playlist randomly if you tell them to.

Most of the mp3 CD-players I've ever used in the past had the ability to play in random order, you might want to take a look in the manual of your device.

For renaming the files to a pattern along the lines of 'Songtitle - Album - Artist' many mp3-tag editors offer the ability to rename the files to match the tags and give a pattern for naming the files. Both easytag and kid3 can do it.

Reordering the files before burning is probably possible, but I've never seen options for that in any GUI burning application. You'd probably have to do it from the command line using genisoimage (see the man-page for all the many, many details) and then burn that image. Doing that might not help at all if the player itself sorts the files either by (path and) file names or according to their tags (I've had several portable mp3-CD-players over the years and I've seen both).

Giving the files names with a random number prepended might be helpful, something like 'for i in *mp3; do mv "$i" ${RANDOM}"$i";done' might help; but that also ends up giving you a fixed order (random, but fixed once the disk is burned).

Holger

Thanks for your ideas.

I am playing the disc in my car.

My car is a 2009 Mazda Cx-7 and it has few options other than play and advance one song forward or backward.

I ended up renaming the files so that when sorted alphabetically, the same artist does not appear consecutively. 

I use CD-RW discs, so I can experiment without having to throw away some discs. :-)

---

