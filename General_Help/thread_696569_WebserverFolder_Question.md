---
title: "Webserver/Folder Question"
date: 2008-02-14
forum: General Help
---

### Post by betamax on 2008-02-14
Hello,

I'm currently setting up a basic web server which will eventually be used by my works service engineers to access tech manuals, drivers and software.

The structure of the site means there are many pages and folders.

I have PHP/Html page (index.php) which can be placed in folders to allow the page to link to a style sheet for layout etc.

Is there a way of either making this page default for each folder or copying into all the sub folders on one go.  As I am currently having to copy it into each folder separately.  I just get the feeling I'm going about this in a very clunky way and would assume with linux/apache there is an elegant and simple way around this.

I may be wrong ?

Thanks for any help.

Darren

---

### Post by hahahan on 2008-02-14
Maybe I understand you wrong but
 <LINK HREF="path/to/your.css" REL="stylesheet" TYPE="text/css"> in the header of each page will do the job.

Regards.

---

### Post by betamax on 2008-02-15
Thanks Hahahan,

I was making a REALLY daft mistake.......all running sweet now.

Cheers.

---

