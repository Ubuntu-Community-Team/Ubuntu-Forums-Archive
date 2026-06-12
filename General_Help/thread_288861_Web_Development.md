---
title: "Web Development"
date: 2006-10-30
forum: General Help
---

### Post by Leec on 2006-10-30
Hope this is the right place to post.  Need some guidance on where to place things for web development.  Never done any on this platform and don't know where things go or how to make it happen.  Planning on using postgresql as the database and have that with pgadmin3 as the frontend working.  Will use PHP as the primary language, so any help or suggestions greately appreciated.
lee

---

### Post by bistrototal on 2006-10-30
Do you mean where to install things? Package management system (apt-get/aptitude/synaptic) takes care of that. When it comes to the php code files which you write, you must specify in the apache (or other www server software) config file where it resides.

[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=sql&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=sql&titlesearch=Titles)

edit: added link

---

### Post by Leec on 2006-10-30
Thanks bistro for the reply.  I'm asking where do you place the main entry to the web...ie  index.html or whatever you desire to call the home page and how and where are things laid out.  I'm not familiar where these things go as I'm coming from Windoz and want to get my hands around some web development in Ubuntu.  I was looking for some help in where to most efficiently place page source, graphics, database items, etc....  if this makes any sense under Ubuntu....like I said, I'm a little lost as to where to start.  Thanks again
lee

---

### Post by Minus0 on 2006-10-30
The root is at /var/www/

---

### Post by Paul41 on 2006-10-30
> The root is at /var/www/
It is helpful to add yourself to the www-data group so you can access files here with your normal privileges.

---

### Post by Leec on 2006-10-30
Thanks for the replies Minus0 and Paul41.  Not for sure Paul41 what you mean by "add yourself to the www-data group"?  Is that a forum here...didn't see it on the main page,  but haven't throughly researched this either.....again, thanks
lee

---

### Post by Paul41 on 2006-10-30
The www-data is the default group for the /var/www folder. If you add yourself to the group you will not have to use sudo to open the files in this folder.

---

