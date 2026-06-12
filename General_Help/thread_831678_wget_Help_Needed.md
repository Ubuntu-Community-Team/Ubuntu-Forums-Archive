---
title: "wget Help Needed"
date: 2008-06-17
forum: General Help
---

### Post by PsyckoSama on 2008-06-17
I'm trying to use wget to back up subforums without backing up the entire main forum but I have no idea what commands to use.

[http://forum.blpublishing.com/default.asp?C=2](http://forum.blpublishing.com/default.asp?C=2)

These are the subforums I'm trying to back up.  

Please help. Thanks.

---

### Post by rraj.be on 2008-06-17
Try this

```
man wget in terminal
```

further this could help you

```
[[COLOR="Blue"]www.linux-tutorial.info/modules.php?name=News&file=article&sid=2284[/COLOR]]("www.linux-tutorial.info/modules.php?name=News&file=article&sid=2284")
```

---

### Post by iaculallad on 2008-06-17
> **PsyckoSama said:**
> I'm trying to use wget to back up subforums without backing up the entire main forum but I have no idea what commands to use.

[http://forum.blpublishing.com/default.asp?C=2](http://forum.blpublishing.com/default.asp?C=2)

These are the subforums I'm trying to back up.  

Please help. Thanks.

Open your terminal and create a directory to whatever name you want. Get inside that directory and issue the terminal command below to retrieve all pages including the site that it links to:

```
wget -H -r --level=1 -k -p http://forum.blpublishing.com/default.asp?C=2
```

---

### Post by PsyckoSama on 2008-06-17
> **iaculallad said:**
> Open your terminal and create a directory to whatever name you want. Get inside that directory and issue the terminal command below to retrieve all pages including the site that it links to:

```
wget -H -r --level=1 -k -p http://forum.blpublishing.com/default.asp?C=2
```

Didn't work. Its a pretty large forum and it only got the first page of it. :(

---

### Post by VMC on 2008-06-17
> **PsyckoSama said:**
> Didn't work. Its a pretty large forum and it only got the first page of it. :(

The -c ("continue") option sets Wget to resume a partial download if the transfer is interrupted. You might want to use that option if it's large download.

---

### Post by PsyckoSama on 2008-06-17
> **VMC said:**
> The -c ("continue") option sets Wget to resume a partial download if the transfer is interrupted. You might want to use that option if it's large download.

It wasn't interupted. It was complete... just it didn't download the entire sub forum.

Question, is there a way to make it not download or even access pages that are younger than a certain age? The forums I'm looking at have been closed for some time.

---

### Post by VMC on 2008-06-17
Using the -r as in : "wget -r http://linuxreviews.org/"

But many sites do not want you to download their entire site. To prevent this, they check how browsers identify. Many sites refuses you to connect or sends a blank page if they detect you are not using a web-browser. You might get a message like:

Sorry, but the download manager you are using to view this site is not supported. We do not support use of such download managers as flashget, go!zilla, or getright

Wget has a very handy -U option for sites like this. Use -U My-browser to tell the site you are using some commonly accepted browser: EXAMPLE: wget  -r -p -U Mozilla [http://www.stupidsite.com/restricedplace.html](http://www.stupidsite.com/restricedplace.html)

The above may explain why you can't download the entire site. Read the full story here:
[http://linuxreviews.org/quicktips/wget/](http://linuxreviews.org/quicktips/wget/)

---

### Post by PsyckoSama on 2008-06-17
> **VMC said:**
> 
But many sites do not want you to download their entire site. To prevent this, they check how browsers identify. Many sites refuses you to connect or sends a blank page if they detect you are not using a web-browser. You might get a message like:

I'm not trying to download the entire site, just the subforum. The problem is how to DL the sub forums without DLing the rest of the forums.

---

