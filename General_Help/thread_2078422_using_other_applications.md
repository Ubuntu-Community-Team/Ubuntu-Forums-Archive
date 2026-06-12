---
title: "using other applications"
date: 2012-10-30
forum: General Help
---

### Post by anon_private on 2012-10-30
Because I have only 512 MB of memory at present, if I am reading a webpage and need to open a document from a link ubuntu (9.10 livecd) uses Free Office.

This places a strain on my system. I would like to try and open all documents using the viewer. I don't know where it is. Can anyone advise?

For future reference, how can I determine the location of a package?

Thanks

---

### Post by jerrrys on 2012-10-31
Ubuntu 9.10 reached end-of-life in April 2011.  Support for it will be little to none.  :(

With 512M of ram you may want to try something lighter like Xubuntu.

[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

---

### Post by Wim Sturkenboom on 2012-10-31
Open a pdf document (e.g. abc.pdf) with the viewer. Next open a terminal and run _ps -ef |grep abc.pdf_. It will give you the program, in my case 'evince'.

---

### Post by anon_private on 2012-10-31
> **Wim Sturkenboom said:**
> Open a pdf document (e.g. abc.pdf) with the viewer. Next open a terminal and run _ps -ef |grep abc.pdf_. It will give you the program, in my case 'evince'.


I get the option to open with another programme. I should be able to browse to the programmes, but I dont know where they are.

I need to open Word and pdf like documents.

---

### Post by Abhinav Kumar on 2012-10-31
To know the location of a package you could try```
locate packageName | more
```where packageName has to be replaced with the package you want to search.
Generally many executables are in /usr/bin folder
:)

---

### Post by anon_private on 2012-10-31
> **jerrrys said:**
> Ubuntu 9.10 reached end-of-life in April 2011.  Support for it will be little to none.  :(

With 512M of ram you may want to try something lighter like Xubuntu.

[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

What do you think of XUBUNTO vs. LUBUNTU.

LUBUNTU looks a bit basic

CD-R vs CD-RW as burning media. Any benefit to using CD-RW such as being able to save configurations etc?

---

