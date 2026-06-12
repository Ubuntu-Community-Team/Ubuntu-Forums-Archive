---
title: "Firefox 2.0.0.2 and Javascript not working together"
date: 2007-03-21
forum: General Help
---

### Post by ZeroXR on 2007-03-21
I'm coming across more and more sites that have Javascript are starting to slowly not function with my desktop machine running Edgy 6.10. Java runs fine, just Javascript won't load up and the loading progress just hangs at 99%.

I have tested the same sites with Konqueror on my desktop and they do load up. In addition, I have tried them on both my project laptop loaded with 6.10 and a friend's laptop with XP Home.

Is there a way to fix the functionality of Javascript on my desktop? It's not much to disable the Javascript just to allow the pages to finally load, but the functionality is nice as some pages just break without the Javascript.

---

### Post by ZeroXR on 2007-03-21
Tested sites:

[http://a.scarywater.net/](http://a.scarywater.net/) (All anime fan-subbing groups under their domain)
[http://www.mininova.com/](http://www.mininova.com/)

---

### Post by chewearn on 2007-03-21
I don't think it's because of Firefox javascript engine.

I opened those two sites you mentioned, the first one loads within 5 seconds (including the linked pages).  There was no javascript error shown in the Firefox error console.

The second site took slightly longer, but that's because its stuck at loading some advertisement (cashengines.com).  As is usually the case, these advertisement sites are slow to load, causing the originating site to get stuck.  In the error console, I didn't see any javasript error for this one as well, but there were some css warnings.

Anyway, you might want to look into Firefox plugin that blocks access to advertisement.  I use Adblock Plus.

---

### Post by ZeroXR on 2007-03-21
The thing about the ads is, when the Javascript is disabled, they load in seconds and same for the rest of the site.

The [http://a.scarywater.net/](http://a.scarywater.net/) link use to work for me (a week ago), but now I have to disable the Javascript just to get the bittorrent tracker to load all of the torrent data. Same case for Mininova.

I also get the same results in Opera, as odd as it sounds. I'm going to see if my error console shows me something... Thanks for your post as it reminded me that Firefox had it. I will post up what happens in a second or two.

---

### Post by ZeroXR on 2007-03-21
Now, I'm officially confused... After clearing out my error console to get a clear idea of what is happening and trying the sites again, they actually load up!

Although I did run into these errors, which oddly enough aren't CSS syntax errors:

[http://a.scarywater.net/kyuuketsuki/](http://a.scarywater.net/kyuuketsuki/) Test Site
- Warning: Error in parsing value for property 'cursor'.  Declaration dropped.
Source File: [http://a.scarywater.net/kyuuketsuki/](http://a.scarywater.net/kyuuketsuki/)
Line: 2
-Error: uncaught exception: Permission denied to call method Location.toString

Mininova Test Site
-Warning: Error in parsing value for property 'cursor'.  Declaration dropped.
Source File: [http://www.mininova.org/](http://www.mininova.org/)
Line: 2

The common denominator seems to be the declaration dropped involving a w3 string: 

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

---

### Post by chewearn on 2007-03-21
I frequently saw the cursor property error in many sites.  I don't think is it something to worry about.  The error (and css warnings) is due to the web pages using Internet Explorer non-standard syntax.  This is common is many sites, where the pages contains mix of IE syntax, but breaks some rules of the w3 standard.

Actually, this declaration:
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

tells the browser that the page does not follow the strict xhtml rules, but more relaxed transitional rules (i.e. transitioning from html to xhtml).

---

