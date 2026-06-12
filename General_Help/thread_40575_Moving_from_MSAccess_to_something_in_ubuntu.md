---
title: "Moving from MSAccess to something in ubuntu"
date: 2005-06-09
forum: General Help
---

### Post by matthew on 2005-06-09
I have an MS Access database that I would like to move to any program that will run in a moderately similar fashion in Ubuntu. The database is a mailing list that consists of about 400 names, addresses, etc as a space for personal info. I can currently search and sort it using any field and even use the US Post Office web site to confirm address data.

Is there anything in the repositories that would give me similar functionality that would also have a nice GUI to work from? How would I export the data form Access and import it to the new program?

I'm not afraid of learning a new program, but I would like it to be relatively simple to use once set up.

---

### Post by shakin on 2005-06-09
Have a look at one of the how-tos for installing an OpenOffice.org 2.0 beta. It includes a database app that's supposed to be a replacement for Access.

---

### Post by matthew on 2005-06-09
[QUOTE=shakin]Have a look at one of the how-tos for installing an OpenOffice.org 2.0 beta. It includes a database app that's supposed to be a replacement for Access.[/QUOTE]

Thanks, shakin,

I already downloaded the OOo version in the repository (1.9.79.2) to see if that would work as I had been reading about their new program (called Base). So far it hasn't been released as a stand-alone product that I can tell. You can access a pre-made database called "Bibliography" using Writer and looking in the Tools menu. There is an option to create a new database once Base is up and running, but I can't find any way to import data from ms's mdb file. Maybe that will be included in the 2.0 release. If it comes down to it, I can keep dual-booting into Windows for a little while longer until OOo Base is ready.

I was hoping someone might know of another app that already exists and can make the conversion.

---

### Post by mlmurray on 2005-06-09
You may want to check out [Knoda](http://www.knoda.org/) .  i think they just recently added the ability to access data in *.mdb files.

---

### Post by matthew on 2005-06-09
Knoda looks good. I prefer Gnome. Do you know if it will work in that environment or would I need to switch to KDE?

I have also looked at MDBTools which is available in the ubuntu repositories. Here's their page: [http://mdbtools.sourceforge.net/](http://mdbtools.sourceforge.net/)

As I have played with it I found it does a great job of allowing me to view all info in the mdb file, but it hasn't developed yet to the point of being able to add/modify so it sin't much use unless I just need to see something or want to try to use it as a converter. Still, it has promise, too.

---

### Post by matthew on 2005-06-10
I keep posting ideas to my own thread...

Anyway, I found a couple of things and I wanted to see if anyone has tried them out.

The first is actually a winxp program that is supposed to convert from the Access mdb format to MySql format, then I would transfer the file to my Ubuntu machine.

[http://www.mdbtomysql.de/index.htm](http://www.mdbtomysql.de/index.htm)

The second looks interesting and might be of interest for the ubuntu repositories, but I really don't know enough yet about linux to be able to comment intelligently on that or to help with the testing and stuff. If you think I should post the idea in the respositories forum, let me know. This one is supposed to work with the previously mentioned, already in the repositories, mdbtools but will go a step further. Instead of just letting you look at the data or try to export it to a ??? format, it will supposedly format it completely for MySql.

[http://www.enobis.com/sw/mdb2mysql/](http://www.enobis.com/sw/mdb2mysql/)

Okay, now that I have mentioned the options, I have another question: for someone who is just looking for a way to convert a simple mailing list of 400 names and addresses and doesn't need it to be accessible from the internet or even from another computer via any sort of server-client setup, are these options going to be overkill? Should I just be patient for a bit longer and wait for the full 2.0 OpenOffice.org release? The new Base program seems to be an Access clone and I am not really in a rush, other than being ready to delete my windows partition and make the jump to linux completely.

---

### Post by matthew on 2005-06-13
I just installed the latest beta of Ooo (1.9.104) using the instructions found [here](http://www.evolutioncolt.com/mainweb/?q=node/11). One note: the nonjava script link is incorrect. remove the "_nonjava" form the end of it and all will work well.

I am going to try to import everything into Base, which is a stand-alone product in this newest version of the suite and looks like it should work. I will either edit this post or post a followup after I have had a bit of time testing it out. If it all works I may write a howto.

---

### Post by matthew on 2005-06-13
Well, the method wasn't quite what I thought it would be, but I found something that worked out beautifully. So far Base cannot directly import mdb files. However, it can import spreadsheet files. So, what I did is from within MSAccess I exported the database to MSExcel. Then I was able to import the Excel spreadsheet into Base and save the database.

Pretty easy. If anyone thinks this warrants a complete howto, let me know and I'll write it up start to finish, otherwise I really think this should suffice.

---

### Post by Talorgan on 2008-03-18
Have there been any further developments in this area in the last 2+ years?

Given that I am happy with KDE it looks like Knoda might be the best bet.

---

