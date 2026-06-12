---
title: "Dreamweaver alternative for coding, ftp etc"
date: 2014-03-11
forum: General Help
---

### Post by micwit2 on 2014-03-11
I currently use windows, but have mucked around in Linux (have just set up a raspberry pi as a web/backup server), and with windows 8 am getting more and more keen for a change over to Linux (at the moment I think Ubuntu is best bet). I am a website dev and use dreamweaver, but also do some video work etc and have the Adobe CS5 master collection.

I do not use the WYSIWYG part of dreamweaver. I code everything from scratch (html, css, ajax/jquery, javascript, php, mysql), but love the colour coding and error detection that dreamweaver uses (for example if you dont close a loop or use a ; in php, dreamweaver will flag that line red). The other feature that is awesome in dreamweaver is the site management.

I have a local server for development and testing (this will soon be on the raspberry pi). The www is set as a mapped network drive on the windows machine, and the local path is set through there in dreamweaver. The FTP server is just set up with the details for the live server account online. So as I save (which because its local is instant), I can press F5 in the browser window (duel monitors) to view my changes. If I like what is done and it is ready to go live (or it is server specific features that I have to test on the live site), I can just use ctrl+u to upload when in that file, or select the entire site from the file structure tree to upload the lot.

Is there any software that has a good project manager (quick and easy to use that includes FTP) as well as code highlighting/highlighting/error detection? When people have posts on the forum, seems to always point to a WYSIWYG that may not have the features I need. Keen to hear from some PHP devs here to see what they have used and like if possible.

Of course it would be nice to get the entire CS5 suite running in linux, but doubt that will happen :(

Thanks

---

### Post by CharlesA on 2014-03-11
Mmmm Bluefish. :)

---

### Post by Bucky Ball on 2014-03-12
Welcome. I use Kompozer which has wysiwyg and html. It's in the repos.

---

### Post by onlywayislinux on 2014-03-12
I use Sublime Text for coding, It is fantastic.

---

### Post by evanherk on 2014-04-23
Bluefish was fairly stable under ubuntu until now (crashed occasionally under Windows), but after my upgrade to ubuntu 14.4 it crashes within seconds as soon as I start it up.

---

### Post by slickymaster on 2014-04-23
Quanta Plus, Aptana, Bluefish, Amaya.

---

### Post by kostkon on 2014-04-23
Good news, [Google Web Designer]("https://www.google.com/webdesigner/") has just [become available on Ubuntu]("http://www.phoronix.com/scan.php?page=news_item&px=MTY3MTQ").

---

### Post by whistlerspa2 on 2014-04-24
I can't find kompozer in the repos and Google web Designer opens to a featureless black screen - no menus or anything else. (Ubuntu 14.04 64bit)

---

### Post by slickymaster on 2014-04-24
> **whistlerspa2 said:**
> I can't find kompozer in the repos and Google web Designer opens to a featureless black screen - no menus or anything else. (Ubuntu 14.04 64bit)

Kompozer was dropped from the repos, since it is no longer maintained in Debian. But, you can still install it (at least on the 12.10 and 13.04 releases). See [this]("https://help.ubuntu.com/community/InstallKompozer").

---

### Post by mastablasta on 2014-04-24
> **whistlerspa2 said:**
> ...Google web Designer opens to a featureless black screen - no menus or anything else. (Ubuntu 14.04 64bit)

could it be that google web designer needs 32bit libraries to run??! or perhaps it needs some other program installed such as java?

---

### Post by whistlerspa2 on 2014-04-25
Thanks for the suggestion but I don't think that's it.  I have 32bit libraries installed for other software and I have Java installed for IntelliJ and Eclipse.

---

### Post by sitro on 2014-04-25
I propose an alternative not only software but also coding.
I no  longer use software like dreamweaver for coding. Because the need of coding each page in the web site and the need to upload to the server each time you edit the site.  it's too boring.
So now I use Content Management System [http://en.wikipedia.org/wiki/Content_management_system](http://en.wikipedia.org/wiki/Content_management_system)
Of course at first step I have to build the display but some software like the heavy "eclipse" or even a color editor like the simple "gedit"  can do the job.
and there are on internet xhtml validator than can check the code better than anything. For example this one :
[http://validator.w3.org/](http://validator.w3.org/)

my penny ;)

---

### Post by micwit2 on 2014-05-04
I have tried a few things out. Google web designer looks ok, but doesn't have any FTP or site management tools in it (and I'm keen for open source, not sure it is). Looks like its really only for HTML5 and animated content, not really for coding. Bluefish looks ok, but again, can't manage multiple sites, and can't mirror a local site with an online one, its FTP seems annoying. Kompozer is no longer supported (why is this, is it a dead project?), but may give it a go. I'm surprised there isn't something out there that has taken the advantages of each package and rolled it into one!

---

### Post by bapoumba on 2014-05-04
I use Komodo on the Macs [http://komodoide.com/](http://komodoide.com/)
They have Komodo Edit for Linux, but not sure about ftp..
[http://komodoide.com/download/#edit](http://komodoide.com/download/#edit)

---

### Post by rewyllys on 2014-05-04
I used to be (>= 6 years ago) a frequent user of Dreamweaver in Windows.  

But nowadays I am quite happy using Bluefish for developing and maintaining Webpages, and Filezilla for uploading and downloading.  I keep these two programs open simultaneously, and find it quite convenient to work that way.

Furthermore, IMHO Bluefish makes it easy to produce cleaner HTML than Dreamweaver.

---

### Post by micwit2 on 2014-05-04
Hmm, seems Bluefish seems like the way to go. How do you go about swapping between projects (or are you only ever working on the one project at once)? I would be keen to see bluefish put in some kind of project manager, and as part of this, even integrate filezilla as part of the project management and a shortcut key to upload the file I am currently working on.

---

### Post by rewyllys on 2014-05-04
> **micwit2 said:**
> Hmm, seems Bluefish seems like the way to go. How do you go about swapping between projects (or are you only ever working on the one project at once)? I would be keen to see bluefish put in some kind of project manager, and as part of this, even integrate filezilla as part of the project management and a shortcut key to upload the file I am currently working on.
It's easy to set up two or more projects under Bluefish.

And it's also easy to set up two or more Websites in Filezilla.

---

### Post by micwit2 on 2014-05-04
OK, but it means in Bluefish you need to find and load the project file every time you swap between 2 projects! That ridiculous! If I want to find some code I used in a different project, I don't want to have to go find the project file, I want to just quickly swap between the 2!

As far as filezilla goes, this seems ridiculous if you want to upload just the files you are working on. You would have to go find them in the tree in filezilla, when you have them already open in Bluefish! Bluefish has support for FTP, just sucks that you cant have a local site AND a remote site.

From the point of view of someone doing website development in a commercial environment on a daily basis, Bluefish has a lot of advantages, but there are a few BIG things that shouldn't take much to implement that is holding it back. I may try have a chat to the Bluefish devs.

---

### Post by MrMichaelHill on 2014-05-04
> **CharlesA said:**
> Mmmm Bluefish. :)

+1

---

### Post by findingthebalance on 2014-05-05
Google web designer has been fixed, no longer opens to black screen.

---

### Post by kostkon on 2014-05-05
> **findingthebalance said:**
> Google web designer has been fixed, no longer opens to black screen.
Good news, again.

---

### Post by micwit2 on 2015-01-05
[COLOR=#000000]Problem solved! Brackets ([/COLOR][http://brackets.io/](http://brackets.io/)[COLOR=#000000]) is fully opensource, works well in ubuntu, OSX, Windows etc and is the best editor I have come across yet. The extension manager is awesome, and I use SFtpUpload which I think is better than dreamweavers (although I wish there was a simple option of pulling files down). It only recently reached version 1.0 (I have only used it for the past few weeks), but it already seems to be the best to use in my situation. I would recommend trying it. In Ubuntu, you can add the repository (If anyone wants the link, let me know), however, it comes down with adobe extract (preview) which I don't want, so I choose just to download it and install it from the website.[/COLOR]

---

