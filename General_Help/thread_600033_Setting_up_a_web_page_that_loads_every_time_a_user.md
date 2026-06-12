---
title: "Setting up a web page that loads every time a user logs onto my home network???"
date: 2007-11-01
forum: General Help
---

### Post by eric5279 on 2007-11-01
I am not sure if this is the right place for this post, But I thought I would give it a shot.

Basically what I am trying to do is set up a web page that loads every time a user logs onto my home network.  Kind of like when you go into work and since you are on your intranet, your company or department web page always loads first.

I have a server and a domain, but how do I go about doing this?

---

### Post by perlluver on 2007-11-01
If it a site you made, your local host ip is 127.0.0.1, and then just route that to your index.

---

### Post by rfruth on 2007-11-01
Have the users start page = your domain (is this a trick question) ?

---

### Post by eric5279 on 2007-11-01
No.  This is not a trick question.  I do not mean just taking the URL of the web site and making it your default homepage.

I mean having the page load as the first page you see when you open up your browser, but then when you hit Home, you then go to your default home page that is set in your browser.

---

### Post by eric5279 on 2007-11-01
Some mentioned setting up a proxy server and using squid?  Any thoughts?

---

### Post by aot2002 on 2007-11-03
set your server as the default DNS in your router then anytime your users on the network try to access a webpage it has to go through your network.

if you configure a proxy like squid and DNS on your server you can get it to load a default webpage like starbucks does which then allows users when they pay to surf.

if you think its an easy task for a beginner think again. you'll need much studying in how dns and proxy works and alot of patience.

---

