---
title: "Problems With Music Players"
date: 2008-06-19
forum: General Help
---

### Post by AnarchyAT on 2008-06-19
[FONT="Times New Roman"]Well I am sure you have heard this question a million times, what is a good alternative to iTunes for Linux.  Well I've tried them all: Amarok, RythmBox, Banshee, even SongBird.  But none of them really meet the expectations I had from iTunes.  Amarok and Songbird couldn't handle the size of my library, about 26,000 songs.  It would either be really slow or just sit for hours.  RythmBox was decent but transfered songs to my iPod at a snails pace.  And Banshee, well I just didn't like the way it displayed my library, couldn't search through artists and albums, only through the entire library of songs.  Amarok would be friggin sweetness if it wasn't so slow with my library.  Any other suggestions?[/FONT]

---

### Post by windoze87 on 2008-06-19
I don't use an iPod but i belive Listen Media Player has will work with them

---

### Post by Happy_Man on 2008-06-19
Did you try the newest version of Banshee (Banshee 1.0) from [http://getdeb.net?](http://getdeb.net?) That is much improved over Banshee 0.13.2 (the default version), and may be what you're looking for.

---

### Post by Hamm on 2008-06-20
> **Happy_Man said:**
> Did you try the newest version of Banshee (Banshee 1.0) from [http://getdeb.net?](http://getdeb.net?) That is much improved over Banshee 0.13.2 (the default version), and may be what you're looking for.

I am trying Banshee in Hardy. I can't get it to see a share that I have on a FreeBSD box. RythmBox uses it and my Windows machines running itunes uses it also. What do I have to do in Banshee to get that working? Any ideas?

---

### Post by kpkeerthi on 2008-06-20
See [https://launchpad.net/~banshee-team/+archive](https://launchpad.net/~banshee-team/+archive) for instructions

---

### Post by Nepherte on 2008-06-20
What type of database did you use for Amarok? SQLite or MySQL? Using MySQL would give you a boost already. The new Banshee or Exaile might be your thing as well.

---

### Post by Tharmas on 2008-06-20
> **AnarchyAT said:**
> [FONT="Times New Roman"]Amarok and Songbird couldn't handle the size of my library, about 26,000 songs.[/FONT]

Songbird 0.6 supposedly addresses that specific [issue]("http://blog.songbirdnest.com/2008/05/09/performance-improvements-in-songbird-06/"). Did you install that version?
And there is [gmusicbrowser]("http://packages.ubuntu.com/hardy/gmusicbrowser") available in the Ubuntu repositories, specifically designed for large music databases.

---

### Post by Christmas on 2008-06-20
Amarok handles very well my collection of around 4000 OGG Vorbis files. But, why don't you try it with MySQL database instead of the default SQLite?

A good and easy to use guide on how to set up Amarok with MySQL database can be found on the official Amarok Wiki, [here](http://amarok.kde.org/wiki/MySQL_HowTo).

Basically, you will need to install MySQL, set up a database and a user, and then go to Amarok configuration, and fill in the data in the *Collection* tab.

---

### Post by AnarchyAT on 2008-06-20
Thank you all for the quick and numerous responses, I'll try some of these and get back to you soon.

---

### Post by AnarchyAT on 2008-06-22
So far I have found Banshee 1.0 to meet my needs and hasn't frozen yet.  I appreciate the responses and will probably experiment with Amarok some more as well.  Thanks!

---

### Post by dmsuperman on 2008-06-22
Tried exaile yet?

I use exaile for my library, then just gtk-pod for my iPod (I organized my music very well in it's folders so I don't really need a whole music library app for my iPod).

---

