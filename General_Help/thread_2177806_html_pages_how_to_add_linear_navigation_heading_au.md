---
title: "html pages how to add linear navigation heading automaticaly"
date: 2013-09-30
forum: General Help
---

### Post by gam01hr on 2013-09-30
Hello Sirs,
I use Kompozer to make simple static html pages. Then I would like to add a heading for navigation (links: next, back, home).
It's not easy do it manually. Especially if I want to insert new pages between the older pages and refresh the navigations links.:) 
Is there a tool for editing static pages automaticaly? Also checking integrity of all links in the whole set would be fine.

---

### Post by theDaveTheRave on 2013-09-30
gam01hr,

you should have a look a [jQuery]("http://jquery.com/") I realise it isn't 'static', but it may be able to give you what you are after

David

---

### Post by SeijiSensei on 2013-09-30
You could try using "[server-side includes]("http://httpd.apache.org/docs/current/howto/ssi.html")" or [frames]("http://www.w3.org/TR/html401/present/frames.html") to create pages where the header is automatically included at the top of each content page.

---

### Post by theDaveTheRave on 2013-10-03
> **SeijiSensei said:**
> You could try using "[server-side includes]("http://httpd.apache.org/docs/current/howto/ssi.html")" or [frames]("http://www.w3.org/TR/html401/present/frames.html") to create pages where the header is automatically included at the top of each content page.

side note here....

design things now suggest that iframes (inline frames) are not a good path to take, causes problems for site indexing etc.

However if I understand the OP he is creating 'static' pages, and doesn't want the 'overhead' of installing a full blown web server (I don't know how other 'light weight' web servers handle server side includes.

A quick solution may be to make use of [tiddlyWiki]("http://tiddlywiki.com/"), which will give you menu's on left and right (OK I admit you wanted it on the top.... but tiddlyWiki may give you a quick eash in browser solution.

Although thinking about it now jQuery may also require a server... the OP will have to test it out.

David

---

