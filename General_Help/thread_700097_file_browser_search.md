---
title: "file browser search?"
date: 2008-02-18
forum: General Help
---

### Post by ninjadynasty on 2008-02-18
Why doesn't the file browser search function search for anything? 

 It just says search results 0 items found.  Even when I search for a file that I know is there.  copying and pasting the name.

---

### Post by honeydew on 2008-02-18
I am not sure why your search is not working.  However I can suggest installing beagle.  Its a very powerful desktop indexing tool.  Finds stuff in a flash, and integrates with ubuntu pretty well.  Here is a howto I dug up...

[http://ubuntuforums.org/showthread.php?t=78810&highlight=beagled](http://ubuntuforums.org/showthread.php?t=78810&highlight=beagled)

---

### Post by ninjadynasty on 2008-02-18
Thank you, thank you!

---

### Post by feelmjawlk on 2008-03-12
Hi!

I have a headless Ubuntu server with a lot of documents (pdf's and doc's etc.). And I've been trying to find a program to index them. I recently installed beagle but since the server is headless and I was unable to connect to the web interface (which is under heavy development) beagle isn't right for me.

The search interface mustn't be fancy, but I really need a webinterface. Lucene, which is the backend for beagle seems to be good, I just need a user-friendly frontend to it.

In my desperation I have even considered using "pdftotext" and "sort" but I wouldn't know how to proceed... 


Any suggestions?

---

### Post by jimcooncat on 2008-03-12
If you're just looking for a file that matches a filename, use "locate".

This relies on an index normally updated once a day by cron.

You can use "sudo updatedb" to force an update, for instance after you've installed new software.

This is kind of a half-solution to your problem, but I find it indispensable, especially for locating documents and examples about new software I've installed.

---

### Post by feelmjawlk on 2008-03-12
Thank you jimcooncat,

Yes, that would be a start. Eventually I'd like to have a searchable fulltext index though, accessible through a web interface.

EDIT: searching even futher I have found 3 interesting alternatives. And I wonder: has somebody got any experience of using any of these?

CLucene - [http://clucene.wiki.sourceforge.net/](http://clucene.wiki.sourceforge.net/) 
Xapian - [http://www.xapian.org/](http://www.xapian.org/)
Estraier - [http://estraier.sourceforge.net/](http://estraier.sourceforge.net/)

Edit 2: Xappy [http://xappy.org](http://xappy.org) - Don't I wish it was a bit further on it's way... :(

---

### Post by dbera on 2008-03-12
> **feelmjawlk said:**
> Hi!

I have a headless Ubuntu server with a lot of documents (pdf's and doc's etc.). And I've been trying to find a program to index them. I recently installed beagle but since the server is headless and I was unable to connect to the web interface (which is under heavy development) beagle isn't right for me.
Any suggestions?

Why werent you able to connect to the "web interface" ? Did you try asking their mailing list ?

Also, beagle allows usual networked search (using their standard beagle-search interface). It also allows machines running beagled to publish their service using avahi so that other beagle machines in the network can automatically find them and search their indexes.

---

### Post by feelmjawlk on 2008-03-13
Well entering:
beagle-config Networking WebInterface true

as per copy and paste from [http://beagle-project.org/Beagle_Webinterface](http://beagle-project.org/Beagle_Webinterface)

I got an error message stating that Networking was an unknown property and manually editing the xml config and restarting beagle didn't help either.

No, I havn't asked in their mailing list, never used a mailing list, I guess I could register though.

EDIT:
Ok, reinstalled beagle heres my terminal output:

xxx@server~$ beagle-config Networking WebInterface true
Debug: Loading Beagle.Util.Conf+IndexingConfig from indexing.xml
ERROR: Invalid section name 'Networking'

---

### Post by dbera on 2008-03-13
Ahh... the webinterface is only available for 0.3.0 or later. From the error message, it looks like you are using an older version (Gutsy has 0.2.18 which does not have the webinterface).

---

### Post by honeydew on 2008-03-14
> **feelmjawlk said:**
> Hi!

I have a headless Ubuntu server with a lot of documents (pdf's and doc's etc.). And I've been trying to find a program to index them. I recently installed beagle but since the server is headless and I was unable to connect to the web interface (which is under heavy development) beagle isn't right for me.

The search interface mustn't be fancy, but I really need a webinterface. Lucene, which is the backend for beagle seems to be good, I just need a user-friendly frontend to it.

In my desperation I have even considered using "pdftotext" and "sort" but I wouldn't know how to proceed... 


Any suggestions?


hoi.. I am in the exact same boat.. Im really looking for something that can handle thousands of my documents.. I would like it to run headless so I can share a bit of knowledge with friends.. programs I have found for this..

[http://www.phpdig.net/](http://www.phpdig.net/)
[http://hyperestraier.sourceforge.net/](http://hyperestraier.sourceforge.net/)
[http://www.yacy.net/](http://www.yacy.net/)
[http://htdig.sourceforge.net/](http://htdig.sourceforge.net/)
[http://red-piranha.sourceforge.net/](http://red-piranha.sourceforge.net/)

I would love to work on different ways to get a working system up and going.. my thing is all of this software is either missing features I want, or seems to be no longer developed.  Beagle definitely  seems like the best option to me, just because of the quality of there search results.. Im going to try getting the web interface going with that..

---

### Post by dbera on 2008-03-14
This page contains two ways to get network searches; check them out
[http://beagle-project.org/Getting_Started](http://beagle-project.org/Getting_Started)

---

### Post by honeydew on 2008-03-18
aye.. but you have to have the new beagle in your sources.. I dont think older versions have this.  However I can confirm that it is available in hardy, and it is running well ;).

---

