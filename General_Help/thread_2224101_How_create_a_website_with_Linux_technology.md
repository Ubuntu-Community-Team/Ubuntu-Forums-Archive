---
title: "How create a website with Linux technology"
date: 2014-05-14
forum: General Help
---

### Post by BSG Fan on 2014-05-14
when I have no experience in webpages development.
1- Where I should start?

2- Can I use my own computer as my server? How can I do that?


Thanks in advance

:confused:

---

### Post by HiImTye on 2014-05-14
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Lars Noodén on 2014-05-14
For the web pages, look up HTML 4 for structure and CSS2 for layout.  

[http://www.w3.org/Style/Examples/011/firstcss](http://www.w3.org/Style/Examples/011/firstcss)

Then as you get comfortable you can move to XHTML 1 and CSS3.  One of the tools for pag editing would be Bluefish, but Geany or Kate would be fine too at the beginning.  You'll have to look around for tutorials that match your learning style and level.  As always the ultimate reference source for HTML and CSS is the W3C.  Anything else is either derivative or wrong.  Use it at the beginning like you would a dictionary or thesaurus.

[list]
[*] [http://www.w3.org/TR/html401/index/elements.html](http://www.w3.org/TR/html401/index/elements.html)
[*] [http://www.w3.org/TR/CSS1/](http://www.w3.org/TR/CSS1/)
[*] [http://www.w3.org/TR/CSS2/](http://www.w3.org/TR/CSS2/)
[/list]

The link provided above by HiImTye shows how to set up Apache2.  That's all you need for web pages on your own machine, you don't need PHP or MySQL at the beginning.  Which version of Ubuntu are you running?

---

### Post by BSG Fan on 2014-05-14
> **Lars Noodén said:**
> For the web pages, look up HTML 4 for structure and CSS2 for layout.  

Which version of Ubuntu are you running?

I am in the prehistory.  I am using Ubuntu 10.04

---

### Post by Lars Noodén on 2014-05-15
It would be a very good idea to move to 12.04 or 14.04 because [Desktop 10.04 was discontinued a year ago](https://wiki.ubuntu.com/Releases) and won't get any updates of any kind.  If the GUI is a problem on the new versions, which it is for many, then you can look to [install MATE](http://www.omgubuntu.co.uk/2014/01/mate-desktop-ubuntu-1404) or Xfce.  The latter is quite popular and comes as part of Xubuntu but can always be installed a la carte.

---

### Post by T.J. on 2014-05-15
Hi BSG Fan!  

Wow, you are asking a big question.  Let me see if I can help. =)

"1- Where I should start?"

You will need to install Apache, and perhaps other software from the repository, depending on what you want to use: such as MySQL, PostgreSQL, PHP, or Ruby.  You may have to do some hand configuring to get it up to spec.  Feel welcome to send me private message here on the board if you want to set up some "one on one" help.  It would probably take a lot of space on the message board to explain it thoroughly.

"2- Can I use my own computer as my server? How can I do that?"

Yes, you can!  I highly recommend it for local design and development, as you can edit and view your changes, exactly as they will be on a live server.  

Actually serving webpages to the rest of Internet however, is another story.  It gets considerably more complicated, as it involves your Internet service provider routing requests to your computer as well as registering your site's URL with the DNS system.  Simply, it will cost you some money because all of those things have to be setup and maintained.  There is also the consideration that if you serve your own sites from your home you have to pay the electric to have the computer on 24/7.

---

### Post by Mark Phelps on 2014-05-15
There is the additional problem that if you run a web server from your personal Internet account, your ISP may consider this a "commercial" operation -- and then charge you commercial rates, which are a LOT higher than personal rates.  It depends very much on the particular ISP you're using.

---

### Post by Lars Noodén on 2014-05-15
> **Mark Phelps said:**
> There is the additional problem that if you run a web server from your personal Internet account, your ISP may consider this a "commercial" operation -- and then charge you commercial rates, which are a LOT higher than personal rates.  It depends very much on the particular ISP you're using.

True.  But just installing Apache2 or nginx won't do that alone.  You have to go out of your way to adjust the router to make it publicly available before the terms of service come into the question.  For a home lab, things should be quite ok with the defaults.

---

### Post by Alley_Oop on 2014-05-15
You could bypass all the above and just start with a free website from wordpress.com or blogger.com. Wordpress is easiest plus it has the added bonus of not having to learn HTML or CSS or XAMP.

---

### Post by spynappels on 2014-05-15
Ummm, I think the OP actually wants to learn?

---

### Post by buzzingrobot on 2014-05-15
If you just want to put up a little site, then, yes, look at Wordpress.com, etc.

If you want to learn about creating web pages and sites, that's a different matter. Lots of good, and lots of not-so-good, material on the web, as well as some pretty good books about the subject.  It is a discipline equivalent in many respects to software development.

One distinction to keep in mind:  What a site looks like is separate from what the site does. One is design, and determined by things like the choices made when the HTML and CSS are written.  Interaction with a user involves things like form design, Javascript, PHP, dealing with databases behind the scenes, etc. 

Sites can be coded entirely using only a text editor. GUI tools can make it faster. Some GUI tools crank out their own HTML, etc., which may or may not permit the kind of control you want, or be very difficult to read and debug.

For learning and testing purposes, you do need something to serve up your pages on your local machine.  You do not need to set up and adminster Apache or another server on a remote VPS or some such thing.

Here's an intro from Lifehacker a few years ago: [http://lifehacker.com/5790955/how-to-make-a-web-site-the-complete-guide](http://lifehacker.com/5790955/how-to-make-a-web-site-the-complete-guide).  Many, many like it on the web.

---

### Post by BSG Fan on 2014-05-15
> **spynappels said:**
> Ummm, I think the OP actually wants to learn?


lol, yes, the original poster (OP) wants to learn. This is something I want to do for years.

It is just tons of information to digest the first time. I need time to read and understand all this.

I want to thank all the users that replied and posted their knowledge in trying to help me.
I will be back..

---

### Post by HiImTye on 2014-05-15
> **Lars Noodén said:**
> For the web pages, look up HTML 4 for structure and CSS2 for layout.  

[http://www.w3.org/Style/Examples/011/firstcss](http://www.w3.org/Style/Examples/011/firstcss)

Then as you get comfortable you can move to XHTML 1 and CSS3.  One of the tools for pag editing would be Bluefish, but Geany or Kate would be fine too at the beginning.  You'll have to look around for tutorials that match your learning style and level.  As always the ultimate reference source for HTML and CSS is the W3C.  Anything else is either derivative or wrong.  Use it at the beginning like you would a dictionary or thesaurus.

[LIST]
[*] [http://www.w3.org/TR/html401/index/elements.html](http://www.w3.org/TR/html401/index/elements.html) 
[*] [http://www.w3.org/TR/CSS1/](http://www.w3.org/TR/CSS1/) 
[*] [http://www.w3.org/TR/CSS2/](http://www.w3.org/TR/CSS2/) 
[/LIST]

The link provided above by HiImTye shows how to set up Apache2.  That's all you need for web pages on your own machine, you don't need PHP or MySQL at the beginning.  Which version of Ubuntu are you running?

I guess I misunderstood your question. Lars is completely correct. HTML & CSS is the easiest route to learn, and the other two technologies build on top of them. you can find many resources if you do a web search for "web site tutorial," "html tutorial," or "css tutorial"

---

