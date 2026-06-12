---
title: "Index.htm as default page on Website"
date: 2005-07-06
forum: General Help
---

### Post by WiFi Net Guy on 2005-07-06
Hi. Sorry if this is a simple question. However, I'm quite the "n00b". I've created a website via FrontPage. I've moved it over to the correct directory (/var/www) on my Kubuntu box. All goes well except that when I enter the domain name, it gives me a list of the contents (index.htm is in there) instead of displaying the correct site page (index.htm). 

What am I missing that will make the surfer see the index.htm file without having to navigate to it?

Thanks in advance...

---

### Post by Caboto on 2005-07-06
[QUOTE=WiFi Net Guy]Hi. Sorry if this is a simple question. However, I'm quite the "n00b". I've created a website via FrontPage. I've moved it over to the correct directory (/var/www) on my Kubuntu box. All goes well except that when I enter the domain name, it gives me a list of the contents (index.htm is in there) instead of displaying the correct site page (index.htm). 

What am I missing that will make the surfer see the index.htm file without having to navigate to it?

Thanks in advance...[/QUOTE]
 Naming the Index file index.htm is done by FrontPage. MicroSoft wants to have all endings with only 3 characters.
Normally you would choose index.html (which will be interpreted right by the Apache Webserver).

---

### Post by WiFi Net Guy on 2005-07-07
Thank you. Worked great!

---

