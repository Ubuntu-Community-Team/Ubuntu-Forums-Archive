---
title: "Connect to ASP site"
date: 2008-01-24
forum: General Help
---

### Post by JFonner on 2008-01-24
How do I connect to an ASP website from Ubuntu?   My new job has a training version of their software on an ASP site.  I cannot connect as I normally would when in Windows using Microsoft Internet Explorer.  In IE you need to add the website into the Trusted Sites under the Tools options menu.  

I would hate to need to install Windows again just to connect to work.  


Any help would be appreciated.

---

### Post by beercz on 2008-01-24
> **JFonner said:**
> How do I connect to an ASP website from Ubuntu?   My new job has a training version of their software on an ASP site.  I cannot connect as I normally would when in Windows using Microsoft Internet Explorer.  In IE you need to add the website into the Trusted Sites under the Tools options menu.  

I would hate to need to install Windows again just to connect to work.  


Any help would be appreciated.
If I understand you correctly, from what you are asking, I think you need to use is firefox (or some other web browser), as an alternative to IE and firefox should be installed when you installed Ubuntu.  It is the webserver that delivers webpages to your web browser (firefox in ubuntu and IE in windows).  ASP is a script (or set of scripts) used by the web server to generate the HTML code needed for your browser, depending on what is needed at the time.

Firefox, and other browsers, installed in Ubuntu can generally read web pages scripted using ASP just fine, assuming that the pages are written to W3C standards (and not Microsoft's) - but that's another story.

Try firefox.

Good luck.

---

### Post by fyo on 2008-01-24
Your query makes no sense. ASP has nothing to do with anything in this context.

There are several possibilities as to the cause of your problem. My money is on activeX, but you'll have to provide something that even resembles a description of your problem. 

You obviously know how to use a web browser, since you can post here, and one would assume that you are using the default browser in Ubuntu, Firefox. So what happens when you visit the URL ("ASP site") in question?

---

### Post by JFonner on 2008-01-24
I am using Firefox.  When I type in the address, I come to a Microsoft Window Terminal Connection Window.  There is a "Connect" on the website, but when I hit the button Firebox does nothing.

---

### Post by JFonner on 2008-01-24
Well, I got it to work, but I resorted to installing Wine and using IEs 4 Linux (Internet Explorer for Linux).  It runs a little slow, but will do for what I need.  Plus I learned a few things along the way so what else can you ask for.

---

