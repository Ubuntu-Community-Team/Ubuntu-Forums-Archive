---
title: "aMule 2.0.0rc8?"
date: 2005-04-10
forum: General Help
---

### Post by chapterthree on 2005-04-10
Hey All,

Anybody know when aMule is going to be updated in universe?  It looks like aMule was updated to rc8 in December of 2004, and it appears there were some major changes, but it appears the universe still has rc7.

Thanks

---

### Post by kiddo on 2005-04-10
Sometime soon, according to the package maintainer (to who I sent an email), but it's already been 2 weeks since I'm waiting for it to appear. In fact, I think he'll be waiting for the amule 2.0 final release. That would be wiser.

I'm much more anxious at waiting for the ifolder workgroup capability ;)

---

### Post by jeremy on 2005-04-10
If you dl the aMule-2.0.0rc8+utils-debian_SID.tar.bz2 and extract it, then dpkg the amule_1.2.6+rc8-1_i386.deb that you will find in the extracted folder, that will work and install the 2.0.0rc8 (and it looks good too!).

---

### Post by bored2k on 2005-04-10
[http://www.amule.org/files/details.php?file=59](http://www.amule.org/files/details.php?file=59)

---

### Post by RastaMahata on 2005-04-10
I think I'll wait for final :P And hope it uses gtk2 (right?)

---

### Post by bored2k on 2005-04-10
[QUOTE=RastaMahata]I think I'll wait for final :P And hope it uses gtk2 (right?)[/QUOTE]
 The link I posted already uses GTK2, mighty pretty.

---

### Post by chapterthree on 2005-04-10
[QUOTE=jeremy]If you dl the aMule-2.0.0rc8+utils-debian_SID.tar.bz2 and extract it, then dpkg the amule_1.2.6+rc8-1_i386.deb that you will find in the extracted folder, that will work and install the 2.0.0rc8 (and it looks good too!).[/QUOTE]

Will using this method "upgrade" the version that is already installed, or will this create a new installation?  Also what would the dpkg command look like?  (Sorry, don't use dpkg much)

Thanks

---

### Post by bored2k on 2005-04-10
[QUOTE=chapterthree]Will using this method "upgrade" the version that is already installed, or will this create a new installation?  Also what would the dpkg command look like?  (Sorry, don't use dpkg much)

Thanks[/QUOTE]
 > sudo dpkg -i amule_name.deb 
Should install it. If an error occurs, hit apt-get -f install.

---

### Post by chapterthree on 2005-04-10
Sweet, that worked perfectly, ty!  :)

---

### Post by seguso on 2005-04-28
[QUOTE=bored2k]The link I posted already uses GTK2, mighty pretty.[/QUOTE]

Did noone notice that wxwidgets (and therefore amule) when linked with gtk2, has huge memory leaks?

The memory usage increases steadily each minute, until it reaches hundreds of megabytes after a few hours. My systems slows down to a crawl and I am forced to shut down amule. This is tragic because some files require you to stay in the queue for many hours.

OTOH, using gtk1, amule takes only few megabytes (20 or so, I don't remember), and the size does not increase with time. It is clearly a memory leak in wxwidgets + gtk2.

Comments?

---

### Post by Chayyiel on 2005-04-28
My aMule will stay ugly until the final release :)

---

### Post by fng on 2005-04-28
i suppose there won't be any new aMule package in the hoary repositories.  Unless someone backports it for hoary.  

The new amule will appear in the breezy repo.

---

### Post by DutchLau on 2005-04-28
Amazing little program this aMule. I was using GTK Gnutella before, but aMule rocks! I'm using rc7 right now, but I'll wait for the final stable version to appear before I download it.  :-P  Man oh man aMule is fast.

I recommend it *any day* over Limewire or GTK Gnutella

Cheers, Dutchlau

---

### Post by bored2k on 2005-04-28
[QUOTE=DutchLau]Amazing little program this aMule. I was using GTK Gnutella before, but aMule rocks! I'm using rc7 right now, but I'll wait for the final stable version to appear before I download it.  :-P  Man oh man aMule is fast.

I recommend it *any day* over Limewire or GTK Gnutella

Cheers, Dutchlau[/QUOTE]
 I still won't ditch Limewire Pro. I like it better for small files like mp3s 'cause I just hate aMule's waiting period's at times. For big files aMule has a lot more files though..

---

