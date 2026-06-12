---
title: "Dictionary hotkey/keyboard shortcut?"
date: 2006-10-11
forum: General Help
---

### Post by ropers on 2006-10-11
Hi, 

I used to be the maintainer of a reasonably popular [Dictionary distribution]("http://www.ropersonline.com/dict/") for Mac OS X (this was before Apple included a local, offline Dictionary in Mac OS X Tiger).

Now I'm not using Mac OS X anymore (because of [DRM]("http://www.the-fifth-hope.org/mp3/drm.mp3")) and I'm finding the same situation in Ubuntu: The Dictionary client that is there by default only talks to online dictionary servers. 
*Translation: *
It requires an Internet connection (which isn't always a given); *and* it can be slow, unless the user's Internet connection is never maxed out (which isn't always a given); *and* it needs tcp/udp ports 2628 open (which isn't always a given).
Clearly having to contact remote dictionary servers just to look up a simple word is *teh sux0r*.

So I've looked into the matter. This is from an email I wrote yesterday or so:
> > If you get really bored, I'm sure a dict based Linux popup dictionary
> would be *very* popular,

See:
[http://ubuntuforums.org/showthread.php?p=1541000](http://ubuntuforums.org/showthread.php?p=1541000)

Ubuntu already has a DICT Dictionary client, it's missing a locally
running server (which I could set up). It's ironic. This is the same
situation I found with OS X, where I reckon that it was my precedent
that eventually resulted in Apple including Dictionary in their OS.
Maybe the same will happen with Ubuntu now, though for the moment I
have other stuff on my mind and can't be arsed.

Scrap that.
I've just found that by using the Synaptic Package Manager or apt-get
I could very simply install dictd with the same local databases I
included with DICTatoro (The only dict database missing in the default
Ubuntu repositories is the CIA world factbooks, and frankly I'd rather
prefer a more credible source such as Wikipedia.):

```
sudo apt-get install dictd dict-wn dict-gcide dict-vera dict-jargon
dict-foldoc dict-freedict-eng-lat dict-freedict-lat-eng dict-elements
dict-devil  dict-hitchcock dict-easton dict-moby-thesaurus
```

All that's left then is to tell Ubuntu's Dictionary in preferences to
use port localhost:2628. Job done. Though I think it's worth trying to
get the maintainers to include, say at least dictd, dict-gcide and
dict-wn by default and have the Dictionary client use local databases
by default. It's faster and not dependent on an Internet connection
that way.

The only thing I haven't working right now in Ubuntu is a Dictionary hotkey.

As you can see, I've got this working, but I'd like to ask:

- How can we petition/convince the maintainers to include dictd and at least dict-wn in Efty Eft? (Obviously, Ubuntu's Dictionary should then also by default be configured to use localhost and port 2628.)

**- How can I configure a keyboard shortcut in Ubuntu, in such a way that I would highlight any word in X11/GNOME, press a hotkey and have Dictionary open up and query its locally hosted dictd server for the highlighted word(s)?** Obviously, this should also become an Ubuntu Efty Eft default.

Cheers, 
--ropers

PS: 
(1) If you're into multi-language dictionaries, search for dict in Synaptic. It'll turn up a bunch of dictionary databases, including a bundle of bilingual ones (from freedict.de).

(2) The order in which Ubuntu's Dictionary displays the results can be changed by editing /etc/dict/dictd.order, eg. by```
sudo vi /etc/dictd/dictd.order
``` (if you don't know vi, type :q! and use [whichever editor you prefer]("http://www.gnu.org/fun/jokes/ed.msg.html")) 
I prefer this order:
```
wn gcide vera jargon foldoc *dict-freedict-eng-lat dict-freedict-lat-eng* elements devil hitchcock easton
```

The ones in italics are probably incorrect. Does anyone remember how to get a dictd server to show the short names of all of its installed databases/dictionaries?

---

### Post by ryu kun on 2006-11-18
Nice ideas, deserve attention.

Btw, Stardict is a great alternative for offline dictionary needs. Try it. 

[http://stardict.sourceforge.net/](http://stardict.sourceforge.net/)

It works like Babylon for MS Windows. Double click on a word and get the definition in a pop-up window, very useful indeed. GPL licenced and only uses free dictionaries. Very cool indeed. :)

Some of the dictionaries it can use:

> dictd_www.dict.org_devils 	RPM 	tarball 	GPL, 176K, 986 words
dictd_www.dict.org_elements 	RPM 	tarball 	GPL, 18K, 127 words
dictd_www.dict.org_gazetteer 	RPM 	tarball 	GPL, 2.2M, 52991 words
dictd_www.dict.org_gcide 	RPM 	tarball 	GPL, 35M, 174222 words
dictd_www.dict.org_hitchcock 	RPM 	tarball 	GPL, 57K, 2611 words
WordNet 	RPM 	tarball 	GPL, 10.7M, 149535 words
dictd_www.dict.org_world95 	RPM 	tarball 	GPL, 979K, 273 words
Free On-Line Dictionary of Computing 	RPM 	tarball 	GPL, 2.3M, 13452 words

Longman Dictionary of Contemporary English 	RPM 	tarball 	Free to use, 6.4M, 43052 words
Oxford Advanced Learner's Dictionary 	RPM 	tarball 	Free to use, 4.7M, 34153 words
Collins Cobuild English Dictionary	RPM 	tarball 	Free to use, 5.1M, 34097 words
Merrian Webster 10th dictionary 	RPM 	tarball 	Free to use, 2.5M, 20517 words
The Britannica Concise Encyclopedia 	RPM 	tarball 	Free to use, 7M, 24402 words
English Thesaurus

---

