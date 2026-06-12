---
title: "Collaboration Tools ?"
date: 2014-08-10
forum: General Help
---

### Post by asearle on 2014-08-10
Hi Everyone,

I know that this is a bit off-topic (not directly Ubuntu-related) but I am looking for an on-line collatoration portal or tool (like Google-office but definitely NOT Google-office) where we (a small group of researchers using both Linux and Windows systems) can share information and documents.

This could either be a generic tool (on-line editing) or something like Sharepoint (but not Microsoft) or, even better, something based on Open/Libre-Office.

Many thanks for any tips that you can give me.

Yours,
Alan Searle
Cologne Germany

---

### Post by Frogs Hair on 2014-08-10
There is 2GB storage limitation on the free version of Team Drive . 

[http://www.teamdrive.com/addons.html](http://www.teamdrive.com/addons.html)

---

### Post by tgalati4 on 2014-08-10
You could set up *owncloud* on a server that you own and set up a web address so that several folks can interact with it.  You could set up a simple Ubuntu server with LibreOffice and run ssh clients with X-forwarding.  Windows users would need to install X-Windows clients.  Performance is not great, but may be acceptable.

You would need to define collaboration in detail, because there are a lot of aspects that need addressing.  Some tools work better than others.

Other tools to consider:

Evernote pro account (gives you shared access)
GoogleDocs (which can be painful to use)
Email documents back and forth
git/bazaar/svn version tracker
trac/redmine--trouble-ticket system
[http://getontracks.org](http://getontracks.org)
BaseCamp and other cloud-based collaboration services
Any service from:  [https://bitnami.com/stacks](https://bitnami.com/stacks)  It's helpful because you can read about the service and see screenshots.

Your actual collaboration effort will probably result in using 2 or 3 tools because no one tool will satisfy all of your needs--unless you write it.  Then you will name it YACT--Yet Another Collaboration Tool or NACT--Not Another Collaboration Tool.

OneNote is a nice notetaker, but I don't think it does Web-based collaboration.

Search for "collaboration" in this website.  [http://www.43folders.com/](http://www.43folders.com/)
There's a few podcasts concerning collaboration in writing books (I can't find them at the moment).  [http://www.degconsulting.net/resources](http://www.degconsulting.net/resources)
Several podcasts that deal with personal productivity, but are related to collaboration:  [http://www.gtdvsg.com/podcasts/2013/12/one-productivity-system-or-two.html](http://www.gtdvsg.com/podcasts/2013/12/one-productivity-system-or-two.html)

That will keep you busy for a few weeks.

---

### Post by asearle on 2014-08-14
Many thanks for these suggestions and the detail of the explanation.

I will give Team-Drive a go as that may be enough for what we have in mind.  But it is good to have other options in reserve.

I'll give feedback once I we have something running.

Once again: Many thanks.

Yours,
Alan Searle
Cologne, Germany

---

### Post by asearle on 2014-08-31
Hi Everyone,

The recommendation to use TeamDrive and Open/Libre- Office for our collaboration tasks sounds perfect so now I am investigating the install.

The install file has the following format ...

Install-TeamDrive-3.2.1.809_TMDR.run

... but my Ubuntu (14.04) doesn't seem to know what to do with this file.

I clicked on posible files and PyPar2 was suggested.  This apparently ran through an install process and created a string of .par2 files (python I think) but I am still not sure what to do with these.

Any tips on how to handle/install with a .run file?

Many thanks,
Alan Searle
Cologne

---

### Post by Habitual on 2014-08-31
open a terminal and run
```
sudo sh /path/to/Install-TeamDrive-3.2.1.809_TMDR.run
```

---

### Post by Brian_Wenzky on 2014-10-03
Hi you may evaluate LogicalDOC - [http://www.logicaldoc.com](http://www.logicaldoc.com)
It is integrated with LibreOffice through a very solid support to the CMIS protocol.
This allows you to automate the versioning and coordinate your team.

Apart of this, LogicalDOC also offers workflows and email alerts.

---

