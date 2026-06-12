---
title: "Cataloging software (list included, critic needed)"
date: 2008-03-17
forum: General Help
---

### Post by kung fu buntu on 2008-03-17
[COLOR="Red"]**Preface**[/COLOR]
Since I've switched from windows to Linux that I've been trying to find a good cataloging software to replace whereisit.
While I searched, I kept finding more and more software... The problem now is that I know of dozens of applications but am unable to compare them.

The purpose of this thread is to get feedback from its users and compare each tool, so that we can all pick the best tool for our needs.
The results of this "Comparison of cataloging software" could then be transformed in a table and hosted at wikinfo.org (wikipedia will just delete it due to the lack of 3rd party references; believe me it has happened before with my [[COLOR="Blue"]Comparison of desktop search software[/COLOR]]("http://www.wikinfo.org/index.php/Comparison_of_desktop_search_software")). This is because the forum doesn't support the use of tables and it would be usefull to more people as well.

I was hopping for comments like, "I use application appA because it supports features X, Y, Z and application appB didn't support it, although appB did had feature W, which appA doesn't has"

One other thing is that at first I wanted something like whereisit (to index my documents, archives, pics and videos), but them I noticed that there was more to it... like the management of collections (e.g. movies, games, music).
BTW, I inform that both Beagle and Tracker may support removable media indexing in the future (check the above article at wikinfo).

Well, even if this thread doesn't come out to be what I expected (i.e. no feedback), it will at the very least this thread will contain a list of cataloging software... and maybe even reach a sticky somewhere :p




[COLOR="Red"]**General indexing/cataloging (i.e. oriented at cd/dvd scanning):**[/COLOR]
[gnomecatalog]("http://gnomecatalog.sourceforge.net/")
[cdnavigator]("http://www.hdf.cz/cdnavigator/en/")
[cdcat]("http://cdcat.sourceforge.net/")
[gwhere]("http://www.gwhere.org/home.php3")
[cdfly]("http://cdfly.sourceforge.net/page/Main_Page")
[cdcollect]("http://cdcollect.sourceforge.net/")
[katalog]("http://salvaste.altervista.org/")
[gtktalog]("http://www.nongnu.org/gtktalog/")
[bumblebee]("http://bumblebee.homelinux.org/")

[COLOR="Red"]**General collection management:**[/COLOR]
[Tellico]("http://periapsis.org/tellico/index.php") (comic books, videos, music, coins, stamps, trading cards, video games, wines, board games, and file listings)
[GCstar]("http://www.gcstar.org/index.en.php") (books, movies, music, video games, wine)
[Data Crow]("http://www.datacrow.net/") (video games, music, books, movies, images)
[Stuffkeeper]("http://www.stuffkeeper.org/index.php/Main_Page") (a new kid on the block which seems to support anything!) - [http://ubuntuforums.org/showthread.php?t=743986](http://ubuntuforums.org/showthread.php?t=743986)

[COLOR="Red"]**Book collection management:**[/COLOR]
[Alexandria]("http://alexandria.rubyforge.org/")

[COLOR="Red"]**Comic books collection management:**[/COLOR]
[BirDy]("http://birdy.sourceforge.net/")
[qomics]("http://dev.inzenet.org/~panard/qomics")
[GNOME Comics Organizer]("http://krakoa.dk/linux-software.html#GCO")

[COLOR="Red"]**Anime collection management:**[/COLOR]
[AnimeLamp]("http://linux.softpedia.com/get/Information-Management/Animelamp-7178.shtml")

[COLOR="Red"]**Movie collection management:**[/COLOR]
[Griffith]("http://www.griffith.cc/")
[CeeMedia]("http://ceemedia.sosdg.org/")
[MeD's Movie Manager]("http://xmm.sourceforge.net/")
[Moviefly]("http://savannah.nongnu.org/projects/lmc/")
[vMovieDB]("http://vmoviedb.sourceforge.net/")



Some questions I would like to know:
(about indexing software)
- Does it index archive files (zip, tar, bz2, rar, 7zp, etc) recursively?
- Does it generate thumbnails for images? Can the thumbnail size be configured?
- Does it generates a series of images for video files? Can the resolution and frequency be configured?
- Does it saves data when indexing document files? (e.g. first 1024 chars in a text file; first 3 pages in a pdf file; etc)
(about collections)
- Does it go to episode level for TV series or anime?
- Does it go to chapter level detail on manga? (in manga, a series is made of volumes and a volume is made of chapters)
- Does it get movie screenshots from imdb?
- Does it get video games screenshots from any site?
(general)
- Can it handle thousands of entries?

---

### Post by Jose Catre-Vandis on 2008-03-17
Gwhere for indexing
GCStar for collections

---

### Post by kung fu buntu on 2008-03-18
Your arguments sure are convincing :)

I have been testing the movie applications, but haven't found a perfect solution yet (so far I have tested tellico, griffith and gcstar).

IMO the movie catalog application (ideally) should support this:
01 - use of **utf-8** for saving data
02 - allow **unique number (per movie)**. Ideally the program should do this automatically in a transparent way!
03 - allow **volume number** (to know where it is stored)
04 - allow setting if a movie is: **director's cut, unrated, extended, widescreen, limited, etc**. It should be possible to add this info when the movie is being added!
05 - use of pictures (**front, back, cd, screenshots**); should allow setting hi-res covers from cdcovers.cc. It's impressive how imdb pics come out messed up sometimes (try Blade Runner). It should allow updating the pictures/covers from other sites.
06 - good searching (e.g. search the movie "O")
07 - buttons/icons for websites (ideally it should be configurable and use the website's icon): **imdb,wikipedia, RT**
08 - allow **adding user-configurable fields** (note: this is not a tag) about the movie (e.g. quality, format, shop, who's gift, etc)
09 - supports **episodes** for TV series
10 - database should be text based thus allowing **VCS**


11 - **scan media (DVD/CD/external HDD)**, save **metadata** (*) and allow the user to **select a file and** copy/move/**link it to a new catalog type** (for example in a movie catalog it could then be updated for getting a cover, description, genres, actors, etc).

(*) file name/size/attributes/resolution/bitrate, checksum, image thumbnails (even in tar/rar/7zp files) for images, screenshots for videos.

Example: you have a DVD with a couple of movies (among other things like jpegs, pdfs and mp3s inside rar files). You scan it (where each file is indexed recursively) and have it identified by a unique number and recognized by its volume number. Then you can link an .avi file as a new entry in the movies catalog. That item in the movie catalog can always be traced to that DVD. You can then update information for that movie through, for example an imdb plugin.

Scanning and metadata extraction could potentially be done with something like Beagle or Tracker... but AFAIK it isn't supported yet... so it's not direct.

---

### Post by kung fu buntu on 2008-03-19
No feedback on this?

If anyone else knows of any other interesting piece of software feel free to post it.

rant: I remember seeing some screens of another program where it allowed the addition of several images (covers + screenshots) to each movie.... but it's really annoying me that I can't remember its name *grrrr*


edit: that program was DataCrow :p

---

### Post by Tian on 2008-03-23
Hello,

> **kung fu buntu said:**
> 
IMO the movie catalog application (ideally) should support this:

I could answer for GCstar and try to fill your check list ;)
> 01 - use of **utf-8** for saving data
OK
> 02 - allow **unique number (per movie)**. Ideally the program should do this automatically in a transparent way!
OK
> 03 - allow **volume number** (to know where it is stored)
There is a field for the place it is stored. It could be a number of any short text.
> 04 - allow setting if a movie is: **director's cut, unrated, extended, widescreen, limited, etc**. It should be possible to add this info when the movie is being added!
It's not directly available. But tags should fill this need.
> 05 - use of pictures (**front, back, cd, screenshots**); should allow setting hi-res covers from cdcovers.cc. It's impressive how imdb pics come out messed up sometimes (try Blade Runner). It should allow updating the pictures/covers from other sites.
There is just one for the moment (for movies are there are some screenshots also for video games). But you may update it from any supported site (no plugin for cdcovers.cc yet) as the user could select the field to fetch from a website.
> 06 - good searching (e.g. search the movie "O")
OK. With Advanced search, you can select the kind of comparison. It could be "contains" or "equals"
> 07 - buttons/icons for websites (ideally it should be configurable and use the website's icon): **imdb,wikipedia, RT**
There is already a button to the website the information was fetched from. But there is no icon. There was one in the early versions of GCfilms. But it has been removed for licencing issues.
> 08 - allow **adding user-configurable fields** (note: this is not a tag) about the movie (e.g. quality, format, shop, who's gift, etc)
09 - supports **episodes** for TV series
Both of these features will be available in 1.4.0 and are mostly there in the CVS version. For 08, it will also let users add images to fullfill the need from 05.
> 10 - database should be text based thus allowing **VCS**
OK. It's an XML file.

---

### Post by kung fu buntu on 2008-05-10
First of all Tian, thank you very much for all your work in GCStar! :D
And second, thank you for your reply on this thread and sorry for my late one.


> [QUOTE]04 - allow setting if a movie is: director's cut, unrated, extended, widescreen, limited, etc. It should be possible to add this info when the movie is being added! 
It's not directly available. But tags should fill this need.[/QUOTE]
It's nice to know that this information can be added, but OTHO, IMHO it makes sense that these aspects be 1st class citizens in a movie catalog, instead of just being tags.

> [QUOTE]07 - buttons/icons for websites (ideally it should be configurable and use the website's icon): imdb,wikipedia, RTThere is already a button to the website the information was fetched from. But there is no icon. There was one in the early versions of GCfilms. But it has been removed for licencing issues.[/QUOTE]
Yes... one big button...
My ideia is that it would be a lot more interesting to have a series of buttons (or even better, text hiperlinks -- that would solve any license issues) in that pannel instead.
You can have a pannel named <References> with links to <imdb>, <rotten tomatos>, <wikipedia>, and other user provided sites... That is a lot of info in just a couple of clicks at user convenince.

> [QUOTE]08 - allow adding user-configurable fields (note: this is not a tag) about the movie (e.g. quality, format, shop, who's gift, etc)
09 - supports episodes for TV series 

Both of these features will be available in 1.4.0 and are mostly there in the CVS version. For 08, it will also let users add images to fullfill the need from 05.[/QUOTE]
Cool! :D

I have now checkout the CVS version and will play a bit with it.


I'm still undecided between GCStar and Datacrow... IMHO these are the best cataloging tools by far... however none of them is fine-tuned to my particular tastes :p
And I'm still pondering which tool to use to my needs since adding my collections to either application will consume me many many many hours :(
I dare each developer to try the other one's tool! I think it would be a good experience. :)

I have added item 11 to my list of features.
This is a difficult feature, but IMO and extremely powerfull and usefull one as well.
Could you please comment on it as well?




EDIT:
@everybody, FWIW, so far I'm inclined to go with Datacrow.
Although I'm still to try Stuffkeeper which seems to be very flexible (note that Datacrow is also very flexible as well, e.g. adding custom fields).

---

### Post by qball on 2008-05-13
> **kung fu buntu said:**
> 
@everybody, FWIW, so far I'm inclined to go with Datacrow.
Although I'm still to try Stuffkeeper which seems to be very flexible (note that Datacrow is also very flexible as well, e.g. adding custom fields).

You wanted me to comment, so:

Stuffkeeper is still in development. It focus not only flexible, but also easy to use (KISS somewhat), so it won't have 10000 little options to tweak it to your little need. It will however (atleast it plans too) just work™.

---

### Post by pt123 on 2008-05-25
Thanks for creating this list. 

Overall I haven't had much success with cataloguing software in Linux. 

To Catalog Disks i.e. the actual file contents I used Broken Cross Disk Manager (the last free version) in Windows for sometime. Thankfully  it works without a problem on wine. Recently Broken Cross have provided a converter which outputs the data into XML. 

But currently I can't find a good linux program that can import it. 

The problem with the Linux apps is that there is very little development (most have died) I wouldn't be bothered to index my old CDs as they app. might not work in future linux distributions. 

The one which has seen development is Gnome Catalog but it crashes so frequently in Hardy.

I am surprised there isnt a decent one for KDE.

---

### Post by kung fu buntu on 2008-05-25
I believe DataCrow also scans cds/dvds...
It's a one developer project but it's active... I think the biggest problem is that it's not well known.

Anyway you can try to convince the author for a powerfull cataloging system over [here]("https://sourceforge.net/forum/forum.php?thread_id=2052204&forum_id=650036")

---

### Post by pt123 on 2008-05-26
Thanks I was not keen on it because it's using JAva. The GUI looked a little cumbersome too. 
But if it's the only choice, it may have to do.

---

