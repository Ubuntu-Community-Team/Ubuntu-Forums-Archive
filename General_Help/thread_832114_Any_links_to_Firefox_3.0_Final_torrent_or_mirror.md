---
title: "Any links to Firefox 3.0 Final torrent or mirror?"
date: 2008-06-17
forum: General Help
---

### Post by mjpatey on 2008-06-17
Hi, group-

I've been trying to download Firefox 3.0 for Linux, but all links I've tried are getting hammered (as you might imagine 37 minutes after release!)

Has anyone here found a working torrent or other download link?

-Mark

---

### Post by rudihawk on 2008-06-17
Nope! :| Lets hope someone else has!

---

### Post by linuxd00 on 2008-06-17
Keep in mind that Firefox final is only RC3 renamed!

Release candidate 3 got accepted.
So if you already have RC3 there is absolutely no point in "getting" F3 Final. It would only rename your files.

Even the package hashes are the same.

---

### Post by rudihawk on 2008-06-17
Oh right! :P I have RC3...fantastic.

---

### Post by Nepherte on 2008-06-17
The official site worked for me.

---

### Post by retrovertigo on 2008-06-17
Here's a direct link to download the en-US version:

[http://mirror.internode.on.net/pub/mozilla//firefox/releases/3.0/linux-i686/en-US/firefox-3.0.tar.bz2](http://mirror.internode.on.net/pub/mozilla//firefox/releases/3.0/linux-i686/en-US/firefox-3.0.tar.bz2)


HOWEVER, I am having problems with it.  I can't bring up any webpages, they all show "Could not find server" errors.  I had backed up my ~/.mozilla directory so I just deleted it.

I unpacked the .bz2 archive to ~/firefox, and when running ~/firefox/firefox, it loads Firefox 3.0 just fine, the EULA comes up, and then nothing.  Can't browse any site.  Konqueror works just fine.  I even ran Firefox 3 from the command line and there were no errors.

Anyone else experiencing this?


EDIT: I think I might have downloaded from a bad/outdated mirror.  I finally got through to the official site and the file that I am downloading now is of a different size than the one I had originally downloaded.  I have updated the link above with the new URL.

---

### Post by mjpatey on 2008-06-17
...and it just worked for me, too.  Traffic has cleared up a bit!

[http://download.mozilla.org/?product=firefox-3.0&os=linux&#9001;=en-US]("http://download.mozilla.org/?product=firefox-3.0&os=linux&lang=en-US")

The above will start the download if you're using U.S. English as your language.

-Mark

---

### Post by retrovertigo on 2008-06-17
Well it's official, Firefox 3 does not work for me.  I'm having the same problem I described above, even with the copy I downloaded directly from the official site.

---

### Post by mjpatey on 2008-06-17
It's working for me!  Here's what I did:

1.  Backed up ~/.mozilla and deleted it.
2.  Unpacked the .bz2 file into a folder.
3.  Ran the shell script in the file called "Firefox" by double-clicking the file.
4.  The installer completed and I am now posting this using the new version of Firefox.

I'm using Ubuntu 8.04, 32 bit version.

-Mark

---

### Post by retrovertigo on 2008-06-17
Hmmm... I downloaded the same version.  I am running Kubuntu for AMD64 processors, but that shouldn't really matter.  Any idea of where Firefox would be logging errors, since it doesn't seem to want to output them to the console when I run it from the command line?

---

### Post by retrovertigo on 2008-06-17
Well, looks like Ubuntu has added FF3 to their Hardy repositories, I'm grabbing it from there right now.  Wish me luck!

Well, Ubuntu's copy of FF3 is working.  Freakin' bizarre.

---

### Post by mjpatey on 2008-06-17
I guess that's why Mozilla leaves the packaging up to the distros!  Ubuntu's version may be tweaked for greater Ubuntu compatibility.

-Mark

---

