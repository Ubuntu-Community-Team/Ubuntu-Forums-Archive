---
title: "Download Web Site..."
date: 2005-09-29
forum: General Help
---

### Post by Sirin on 2005-09-29
Hi i want an application so as to download a web site for offline browsing.. I have tried wget, but this downloads the php files without altering them and this makes the offline browsing impossible because all the time konqueror gives a prompt of how to open the file.
Do u have something in mind to suggest me?

---

### Post by aysiu on 2005-09-29
How about just doing "save page as" and then "web page complete"? This is in Firefox, not Konqueror, by the way.

---

### Post by Sirin on 2005-09-29
[QUOTE=aysiu]How about just doing "save page as" and then "web page complete"?[/QUOTE]
Well, first of all, the site consists of over 6,000 pages, and I can't do the "click, save as, save" routine over and over 6,000 times... that would take almost 5 days straight, night and day... :smile:

---

### Post by plumcreek on 2005-09-29
What you're looking for is httrack and webhttrack. 
webhttrack is the easier one to use
You can install it from synaptic or through apt-get
Open a terminal and type:
```
sudo apt-get install webhttrack
```
After it is installed, launch it from the command line with:
```
webhttrack
```

It will launch your web browser and prompt you for the site you want to download. Once you've told it what to do it will get busy for a while and when it is done everything will be downloaded and ready for offline browsing.

It works really well. Just yesterday I downloaded a site with over a thousand pages in less than 20 minutes.

---

### Post by linusgl on 2005-09-29
wget --html-extension will save pages with ".html" attached to the end.

---

