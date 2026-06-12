---
title: "Beagle not impressive"
date: 2007-05-02
forum: General Help
---

### Post by stchman on 2007-05-02
Hello all, I tried Beagle as there are many articles on the net extolling it's virtues.  Well I tried it and it was pretty much useless.

I installed it and then typed beagled for the indexing.  Every time I entered a search parameter in the Beagle search box it found zero.  I then tried .mp3 as I have some MP3s on my PC and it did not find them.

I will stick with the garden variety file search and use grep at the command line.  Does anyone know if grep searches recursively?

If I am doing something completely wrong then let me know.

---

### Post by SeTsU on 2007-05-02
As far as I'm aware, Beagle takes a bit of time indexing all your files and programs. I remember trying it right after dist-upgrading and it found nothing. A few hours later I tried again and voilá! It found most of my files.

Wait for a few hours and try again later. :)

EDIT: BTW, if you want to search recursively try using "find" and grepping the results. ;)

---

### Post by aidanr on 2007-05-02
you could also try [tracker]("http://www.gnome.org/projects/tracker/")

---

### Post by stchman on 2007-05-02
> **SeTsU said:**
> As far as I'm aware, Beagle takes a bit of time indexing all your files and programs. I remember trying it right after dist-upgrading and it found nothing. A few hours later I tried again and voilá! It found most of my files.

Wait for a few hours and try again later. :)

EDIT: BTW, if you want to search recursively try using "find" and grepping the results. ;)

Ok, so the indexer takes time.

Also when I was messing around with Beagle I belive that it only indexes and searches for stuff in the /home directory.  Is this correct?  I have another partition mounted, so will Beagle automatically index those or do I have to specify?

Thanks

---

### Post by 50words on 2007-05-02
Yeah, give it time. Beagle is pretty awesome, in my experience. You can set it to point to other folders, but it will only do your /home folder by default. I also like using Beagle through [Deskbar]("http://raphael.slinckx.net/deskbar/"), which adds a whole new dimension to it.

---

### Post by engla on 2007-05-05
Tracker is awesome as well. I set it up to only index the folders I care about, around 5000 files. It indexed those in under half an hour. And the live search with deskbar is better than spotlight (OS X) and much much faster than beagle.

And yeah, I installed tracker under edgy. it works well, even though nautilus integration is missing.

---

### Post by agurk on 2007-05-06
Could someone tell me what they use these things *for*? Ever since the first Google Desktop was released, I've tried and found these search utilities impressive, but without any real use, more like a solution looking for a problem.

I can see how they could become useful in, say, a corporate environment for indexing big file servers, but on my workstation or laptop? I have found they just tend to slow things down and drain my battery.

---

### Post by engla on 2007-05-06
To find back documents or programming files that you know you have but not where. I don't have too much documents but it still helps. Also, tracker does have a metadata storage backend.. so you can tag files so that you can browse files by tag, or have them appear together if you search for say "economy".

---

### Post by CocoAUS on 2007-05-06
Beagle only indexes your home folder by default, but you can change that in the preferences.  I have it indexing my entire / directory, and it did it fairly quickly.

---

### Post by agurk on 2007-05-06
Ah, right, if you're a programmer having a lot of source files lying around, I can imagine it being useful for quickly finding code snippets. Thanks for the usecase.
Do you think it would be possible to have the indexer running on a file server for remote users to connect to and query, rather than everyone indexing the file server themselves?

---

### Post by engla on 2007-05-06
> **agurk said:**
> Ah, right, if you're a programmer having a lot of source files lying around, I can imagine it being useful for quickly finding code snippets. Thanks for the usecase.
Do you think it would be possible to have the indexer running on a file server for remote users to connect to and query, rather than everyone indexing the file server themselves?

I can imagine that would work. Either they would have to login as the search user and run the search, or they could use the tracker-search command-line tool to search. I think that if the tracker-search application is setuid to the tracker user, everyone searches the same database.

---

### Post by Peverel on 2007-05-24
I am using beagle at the moment but I think I will give tracker a chance...

Am I getting this right, beagle starts indexing again everytime I reboot? 
Just curious, since I run a dual boot with Vista and have to reboot sometimes...

---

### Post by Peverel on 2007-05-24
One more question, when I want to try Tracker, do I have to disable or deinstall beagle somehow, if so, how?

Thanks

---

