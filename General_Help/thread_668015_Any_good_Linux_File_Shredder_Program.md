---
title: "Any good Linux File Shredder Program??"
date: 2008-01-14
forum: General Help
---

### Post by kevdog on 2008-01-14
OK -- Im looking for a file shredder program.  

It seems that the **shred **utility is not meant for ext-3 journaling systems
and the **wipe** utility puts a disclaimer on the man pages:

> The author, the maintainers or the contributors of this package can NOT be held responsible in any way if wipe destroys something you didn't want it to destroy. Let's make this very clear. I want you to assume that this is a nasty program that will wipe out parts of your files that you didn't want it to wipe. So whatever happens after you launch wipe is your entire responsiblity. In particular, no one guarantees that wipe will conform to the specifications given in this manual page

Any other good utility that is available?

Thanks

---

### Post by Mithrilhall on 2008-01-14
[http://sourceforge.net/search/?words=hard+drive&type_of_search=soft&pmode=0&words=wipe&Search=Search](http://sourceforge.net/search/?words=hard+drive&type_of_search=soft&pmode=0&words=wipe&Search=Search)

---

### Post by kevdog on 2008-01-15
Thanks for the sourceforge link, but wipe was the only utility listed.  Im looking for another solution after reading the wipe README file. (See original post)

---

### Post by barduck on 2008-01-15
Looks like the standard paranoid disclaimer of the sort you will find with any tool which has even the most remote possibility of doing anything you did not, or think you did not, intend. 

With all the legal crap flying around in the last years, I'd put this disclaimer with a "Hello World" script.

Why would it discourage you from using the software ? ;)

---

### Post by dagnabit dang doohickey on 2008-01-15
shred does work for ext3 file systems, if you're using the default data=ordered mode. Its when using the data=journal mode that shred becomes ineffective.

From the shred man page:
> In the case of ext3 file systems, the above disclaimer applies (and shred is thus of limited effectiveness) only in data=journal mode, which journals file data in addition to just metadata. In both the data=ordered (default) and data=writeback modes, shred works as usual.

---

### Post by HermanAB on 2008-01-15
Here you go:
[http://www.hammersource.com/Sledge_Hammers.html?gclid=CJ-f_unN-JACFQG3YAod5Cvyyw](http://www.hammersource.com/Sledge_Hammers.html?gclid=CJ-f_unN-JACFQG3YAod5Cvyyw)

This is the only delete utility that is guaranteed to work.  

Any software based erase algorithm is less than optimal.  The spooks can recover data more than 20 layers deep off a hard disk platter.

Cheers,

Herman

---

### Post by kevdog on 2008-01-15
> **HermanAB said:**
> Here you go:
[http://www.hammersource.com/Sledge_Hammers.html?gclid=CJ-f_unN-JACFQG3YAod5Cvyyw](http://www.hammersource.com/Sledge_Hammers.html?gclid=CJ-f_unN-JACFQG3YAod5Cvyyw)

This is the only delete utility that is guaranteed to work.  

Herman

Hmm took me a while -- I was confused at first -- but now I got it! :)  Id rather resort not to destroying my computer if possible.

Ok, maybe not the most rock-solid solution but Ive found this utility being mentioned a few times:
[http://packages.debian.org/sid/secure-delete](http://packages.debian.org/sid/secure-delete)

Anyone know where I can get the source?

---

### Post by dagnabit dang doohickey on 2008-01-15
You can download the source from the link you posted. But, an even easier way to install it is from the Ubuntu repos using aptitude or apt-get. ;)

---

### Post by kevdog on 2008-01-15
Im looking for a cvs or svn repository -- I like bleeding edge!

---

