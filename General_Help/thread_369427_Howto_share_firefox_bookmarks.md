---
title: "Howto share firefox bookmarks"
date: 2007-02-24
forum: General Help
---

### Post by Zill on 2007-02-24
Dapper Firefox 1.5.0.9 - Ideas please for the best ways to:

a) Share bookmarks with another user on a PC connected via NFS.

b) Send a sub-set (folder) of bookmarks (addresses only) to another user via email.

Any help gratefully received.

---

### Post by Gerard Barberi on 2007-02-24
[Chipmarks]("https://addons.mozilla.org/firefox/666/") and [Firefox bookmark share]("https://addons.mozilla.org/firefox/617/") look like they have the functionality you're asking.  But, I've never used them before.  I use Google sync.

About the subset of folders with addresses only, I only saw a way to import/export the whole thing as a web page with links.

---

### Post by Zill on 2007-02-25
Thanks for the info Gerard. I will check out the two add-ons and see how well they work.

Google Sync sounds interesting but doesn't really have the functionality I was after.  I also have doubts about entrusting my personal data to a secretive closed-source mega-corporation :-k 

I agree that the current export facility isn't quite what I wanted as it exports everything.  I simply wanted a quick way to list a subset of web addresses in a single email so that the recipient could just take a look at the links without having to import anything.
If anyone else has managed to do this then please let me know.

Thanks again.

---

### Post by rsambuca on 2007-02-25
It's a bit of a pain, but the bookmarks file is just an html file in your firefox setting directory.  You can quickly open it up, delete the sites you don't want, then save and send it away.

---

### Post by Zill on 2007-02-25
Thanks rsambuca - Yes, that would work but it is a pain as you say.  The file "bookmarks.html" is tucked away inside a folder with a bizarre "variable" name in the hidden firefox directory, so is not easy to find quickly.  Even then, the file contains far more metadata on each link than I wanted - a simple web address would have been sufficient :-(

I thought this would have been a simple task but it is now looking like I will have to learn how to write my own firefox extension :-)

---

### Post by rsambuca on 2007-02-25
This looks like it is what you are looking for.  If you do try it, let us know if it works!

[[COLOR="Red"]Synchronize your bookmarks...[/COLOR]]("http://paininthetech.com/synchronize_your_bookmarks_between_different_computers")

---

### Post by Zill on 2007-02-25
> Synchronize your bookmarks...

Thanks but again it isn't quite what I was looking for.  This needs an internet server and uses ftp.  I want something simple to share some bookmarks between a few PCs on a LAN via NFS.

Alternatively, I need a quick way of getting web addresses from bookmarks into a text email.  At the moment I have to open each bookmark and then drag the address into the email - just thought their had to be a better way :-)

---

