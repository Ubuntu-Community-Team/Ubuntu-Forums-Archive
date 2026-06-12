---
title: "Download complete sites?"
date: 2006-12-18
forum: General Help
---

### Post by PurplePenguin on 2006-12-18
I used to use a download manager during my windows days (either GoZilla or GetRight, I forget which) that would allow you to see a website's list of files.  That is, if there was a download here on Ubuntuforums.com, I could use this option to see which other files were available in the site's directory tree, and choose any of them to download.

Does anybody know of a program that will do this for linux?

Basically, my wife found a site with hundreds of cross-stitching patterns and they're all in individual rar files.  Downloading them individually really sucks. :D  So I was hoping to just put the website's address into a download manager, click "select all" and be able to download all files available on the website.  

Any ideas? :)  Thanks!

---

### Post by cilynx on 2006-12-18
Sorry to give the terminal-junky answer but:
```

wget --mirror http://www.whatever.com/

```
That'll pull down everything linked to on the same domain
```

wget --mirror --span-hosts http://www.whatever.com/

```
That'll pull down everything linked to on the original site, no matter what server it's on.  Beware that this usually gets out of hand.

---

### Post by Mithrilhall on 2006-12-18
Check out the section titled 'Linux'.

[http://www.flashgot.net/whats](http://www.flashgot.net/whats)


[https://addons.mozilla.org/firefox/220/](https://addons.mozilla.org/firefox/220/)

---

### Post by enopepsoo on 2006-12-18
You could install the flashgot extension in firefox and use aria as your download manager.  Just install aria from synaptic or apt-get it.  Aria supports levels of recursion, so if you only want one page and everything linked from it, or everything linked from those, and so on, that is possible.

wget also supports levels of recursion.

---

### Post by strabes on 2006-12-18
downthemall! firefox extension [https://addons.mozilla.org/firefox/201/](https://addons.mozilla.org/firefox/201/)

---

### Post by PurplePenguin on 2006-12-18
Wow, thanks for the quick replies!  Three replies in four minutes! :)

I actually have Aria running right now downloading one of the files.  That was the first thing that I tried, but I can't seem to figure out how to use it to download anything other than that single file (I'm using v1.0.0 - newest?). [COLOR="Red"]Never mind - just found it!  For other users, right click the file you're downloading, select "Selected Item Option", "HTTP/HTTPS" and there are some Recursive tabs to look through.[/COLOR]

Thanks for the other tips, though, too.  Although I don't use it very often, I am constantly in awe of the amazing power of the command line... so I can't wait to try out wget --mirror. :D  I might try that out right now, even if Aria does what I want it to. :)

Again, thanks a million for the great quick tips!

---

### Post by Eroo on 2007-03-28
I too would like something like this but I want it to download new updates from a repository and if files are removed from the repository then its deleted on the local copy too. Can wget do this?

---

### Post by cilynx on 2007-03-28
Maintaining an archive mirror is more of a job for rsync.  It has many options for how to manage the local copy, what to delete, etc..

---

### Post by quadCoreBrainWithNoMemory on 2008-07-17
I noticed a package called d4x that advertises recursive downloading as well.  Has anyone used it, or reviewed it?

---

