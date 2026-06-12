---
title: "Java Webstart"
date: 2005-05-31
forum: General Help
---

### Post by veelivar on 2005-05-31
Hello,

I've installed the latest version of java sucessfully and I belive set up firefox to use it, suns test page displays it's applet and reports the correct version of java.  

Any idea how I get firefox to deal with webstartable programs?  (.jnlp)

Cheers,
Dan.

---

### Post by veelivar on 2005-06-02
Anyone?

I know I have to associate jnlp files with javaws but I don't know where to browse to, to find it.

I downloded java from sun and followed the howcome to install it.  i made the bin into a deb and did "sudo dpkg -i sun-j2sdk1.5_1.5.0+update02_i386.deb" or whatever the actual deb was called. 

Cheers,
Dan.

---

### Post by TiMBuS on 2005-08-29
[QUOTE=veelivar]Anyone?

I know I have to associate jnlp files with javaws but I don't know where to browse to, to find it.

I downloded java from sun and followed the howcome to install it.  i made the bin into a deb and did "sudo dpkg -i sun-j2sdk1.5_1.5.0+update02_i386.deb" or whatever the actual deb was called. 

Cheers,
Dan.[/QUOTE]
 hi dan, sorry to hear no-one replied.

So you can run everything but .jnlp's? good. go [here](http://java.sun.com/products/javawebstart/download.jsp) to download the runtime platform. Also, your java enronment will need to be specified in the install. It's /usr/lib/j2re1.5-sun

hope that will help you and others in the future

---

### Post by foov2 on 2006-02-04
I finally got j2se installed on my new ubuntu 5.10 with the latest sun java version.  that was more difficult that everything else that i did.  thanks for all the suggestions on the forum.

i have a downloaded .jnlp program that i want to associate with /usr/bin/javaws and i can do that each time i run it but was wondering how to associate it permanently.

any help, most appreciated.

---

