---
title: "Download a RSS feed with (Wget? Python? Ruby?)"
date: 2016-11-01
forum: General Help
---

### Post by sam_uk on 2016-11-01
So every day I'd like cron to run and to end up with a set of files in a folder.

News-date.html - (which is a[ list of the titles in a RSS feed and links ]("http://www.rssdog.com/index.htm?url=http%3A%2F%2Fnibleyleaves.co.uk%2Ftnhack%2Ffeed%2F&mode=html&showonly=&maxitems=0&showdescs=0&desctrim=0&descmax=0&tabwidth=100%25&linktarget=_blank&bordercol=%23d4d0c8&headbgcol=%23999999&headtxtcol=%23ffffff&titlebgcol=%23f1eded&titletxtcol=%23000000&itembgcol=%23ffffff&itemtxtcol=%23000000&ctl=0")to local RSSitem1.html, RSSitem2.html etc etc)
RSSitem1-Title-date.html
RSSitem2-Title-date.html
RSSitem3.Title-date.html

[This is the RSS feed]("http://nibleyleaves.co.uk/tnhack/feed/") in question

I don't really mind how it happens! I'd like the pages to be as small as possible, but with the Title in a H1 tag (So not just plain text)

I've been playing around with wget & pages from [RSS dog which turns pages into html]("http://www.rssdog.com/index.htm?url=http%3A%2F%2Fnibleyleaves.co.uk%2Ftnhack%2Ffeed%2F&mode=html&showonly=&maxitems=0&showdescs=0&desctrim=0&descmax=0&tabwidth=100%25&linktarget=_blank&bordercol=%23d4d0c8&headbgcol=%23999999&headtxtcol=%23ffffff&titlebgcol=%23f1eded&titletxtcol=%23000000&itembgcol=%23ffffff&itemtxtcol=%23000000")

I also found this[ Ruby script]("https://gist.github.com/bascht/a80669400e856357590d")  but that creates a bunch of folders and calls all the files index.html

---

### Post by sam_uk on 2016-11-01
Surely there must be a way to do this? This is my dirty bash script [http://pastebin.ca/3734506](http://pastebin.ca/3734506)

But i'd really like smaller files and an index rather than the larger files the above gives me.

It's for broadcasting files from space [https://outernet.is/tech](https://outernet.is/tech)

---

### Post by ian-weisser on 2016-11-02
I don't understand the question. Of course it's possible using pretty much any language.

You must simply choose one to learn, and begin. That's up to you.
I usually recommend Python3 to beginners. It's rather easy to learn, and very flexible.

While it would be a fun 20 minutes or so to write the script for you, I won't be around when you need to maintain or update or change it. So it's probably better if you take the time and learn to do it.

---

### Post by sam_uk on 2016-11-08
Well I worked together a kind of hack using 

[http://rss.bloople.net/?url=http%3A%2F%2Fwww.voanews.com%2Fapi%2Fz-%24otevtiq&showtitle=false&type=js&id=1478647926070785](http://rss.bloople.net/?url=http%3A%2F%2Fwww.voanews.com%2Fapi%2Fz-%24otevtiq&showtitle=false&type=js&id=1478647926070785) So the files are now being broadcast.

It turns out it would be better to have each article as a discete .htm file. So that's my new challenge.

Sed & Grep to split the html into parts somehow.

---

