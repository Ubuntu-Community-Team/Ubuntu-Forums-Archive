---
title: "Beagle not indexing document contents"
date: 2008-06-18
forum: General Help
---

### Post by 50words on 2008-06-18
I use Beagle rather than tracker, and for some reason, it is not indexing the contents of my OOo and PDF documents. It brings up some e-mails, but not all of them.

Any ideas why this would be?

---

### Post by dbera on 2008-06-18
> **50words said:**
> I use Beagle rather than tracker, and for some reason, it is not indexing the contents of my OOo and PDF documents. It brings up some e-mails, but not all of them.

Tell us which version you are using ? Sometimes there are too many search results and the file you are looking for gets buried in them. Add a ".pdf" or ".odf" to the query string to narrow the searches to only .pdf or .odf files.

If you know the path of one PDF/OOo document you feel beagle has not indexed try this command from a terminal

```
beagle-query --verbose uri:file://<full-path>
```
where <full-path> is something like /home/myname/Documents/file.pdf

Or you can ask the beagle people in their IRC. This link will open the IRC channel right away.
[http://embed.mibbit.com/?server=irc.gimp.net&channel=%23dashboard](http://embed.mibbit.com/?server=irc.gimp.net&channel=%23dashboard)

---

### Post by 50words on 2008-06-18
It isn't some PDF or ODF documents. It is EVERYTHING besides Evolution e-mail. I there a way to rebuild the index?

---

### Post by dbera on 2008-06-18
Oh thats bad. To rebuild the filsystem index, stop beagled ("$ beagle-shutdown"), remove the directory ~/.beagle/Indexes/File*Index and restart beagled ("$ beagled"). To rebuild everything, just delete ~/.beagle directory. I am assuming you are using Hardy.

---

### Post by 50words on 2008-06-30
Deleting ~/.beagle did not work. I still cannot find any of my files using Beagle. Any ideas?

---

### Post by 50words on 2008-06-30
Nevermind. Forgot to add the server directory in which my files are stored. Duh.

---

