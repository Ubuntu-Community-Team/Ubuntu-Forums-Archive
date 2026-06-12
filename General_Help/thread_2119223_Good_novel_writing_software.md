---
title: "Good novel writing software?"
date: 2013-02-23
forum: General Help
---

### Post by DisappearingOak on 2013-02-23
I'm looking for a good novel writing software. I do not need advanced features such as scene tiddlers. Just a basic but good looking pad with auto-save. It should save and save a backup at every word change. That's all. But the app should be beautiful to facilitate a pleasant writing experience. I liked Basket Note Pads but it seems it lags a bit when writing in a long container. So something else. Thanks. 

Edit: I would like to use a client-side tiddlywiki sort of thing with inline editing and adding content (instead of editing the whole tiddler) but I do not have time to set up such a thing, but a tiddlywiki spinoff that serves would do, if there is any. Otherwise, native apps are ok, too.

---

### Post by schragge on 2013-02-23
There is [yWriter5](http://www.spacejock.com/yWriter5_Linux.html). It's freeware, but not open source.

---

### Post by graabein on 2013-02-23
Go for gold. Emacs and LaTeX.

---

### Post by sudodus on 2013-02-23
Have a look at this link

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=937963[/COLOR]]("http://ubuntuforums.org/showthread.php?t=937963")

---

### Post by DisappearingOak on 2013-02-24
> **sudodus said:**
> Have a look at this link

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=937963[/COLOR]]("http://ubuntuforums.org/showthread.php?t=937963")

Those seem to be too complex for me.
Okay, is there just a regular WordPad sort of application that's beautiful/skinnable and has autosave? I don't need much more than that.

---

### Post by robert shearer on 2013-02-24
Several here from simple to not so simple...

[http://writingisdreaming.com/the-best-software-for-writers-on-ubuntu-linux/](http://writingisdreaming.com/the-best-software-for-writers-on-ubuntu-linux/)

Maybe focuswriter ?

> Focuswriter is a fullscreen writing program designed to be
distraction free.  You can customize your environment by changing the
font, colors, and background image to add ambiance.  FocusWriter
features an on-the-fly updating wordcount, optional auto-save,
optional daily goals, and toolbars that hide away to allow you to
focus more clearly.  Additionally, when you open the program your
current work in progress will automatically load and position you at
the end of your document, so that you can immediately jump back in.

```
sudo apt-get install focuswriter
```

---

### Post by sudodus on 2013-02-24
> **DisappearingOak said:**
> Those seem to be too complex for me.
Okay, is there just a regular WordPad sort of application that's beautiful/skinnable and has autosave? I don't need much more than that.
What about Abiword and LibreOffice Writer? They 'belong' to linux, and if not included in the install iso file, they are easy to install from the Software Center or with the commands
```
sudo apt-get install libreoffice
```
```
sudo apt-get install abiword

```
Abiword is simpler than LibreOffice Writer.

---

### Post by K.Mandla on 2013-02-24
[Wordgrinder]("http://wordgrinder.sourceforge.net/"). Eliminate all distractions.

---

### Post by DisappearingOak on 2013-02-24
I'm trying out Abiword and so far it's working.. thanks

---

### Post by HermanAB on 2013-02-24
ed

Because it is the standard.

---

### Post by DisappearingOak on 2013-02-24
> **HermanAB said:**
> ed

Because it is the standard.

I was actually looking for something with tiddlywiki like backup where you can set infinite backups for every time you save, so nothing is ever lost whether you work on the master file or else.

I'm not sure how this abiword handles backups and autosaves though, so I'm worried about losing my work.

---

### Post by sudodus on 2013-02-24
> **DisappearingOak said:**
> I was actually looking for something with tiddlywiki like backup where you can set infinite backups for every time you save, so nothing is ever lost whether you work on the master file or else.

I'm not sure how this abiword handles backups and autosaves though, so I'm worried about losing my work.

[s]I looked at the menus and in the help text of Abiword and didn't find any information about it.[/s] ***HermanAB helped us find it in Abiword*** :KS

The other linux standard word processor, Libre Office Writer, has Autosave at

Tools -- Options -- Load/Save -- General
- Save autorecovery information every [ ] minutes
- Always create backup copy (I guess it means a file~ version).

---

### Post by HermanAB on 2013-02-25
Howdy,

Abiword can actually do Auto Save (Edit, Preferences menu), infinite History, Revisions and Annotations (Tools menu).

I regularly use Abiword, but I will not recommend it for a novel.  For a novel you should use Scrivener, which is a Windows program.

---

### Post by sudodus on 2013-02-25
> **HermanAB said:**
> Howdy,

Abiword can actually do Auto Save (Edit, Preferences menu), infinite History, Revisions and Annotations (Tools menu).

I regularly use Abiword, but I will not recommend it for a novel.  For a novel you should use Scrivener, which is a Windows program.

Bad searching by me. Thanks for sharing your knowledge about Abiword :-)

---

### Post by Bucky Ball on 2013-02-25
*Thread moved to **General Help**.*

---

### Post by fantab on 2013-02-25
Try[ **CELTX**]("https://www.celtx.com/index.html"), it is for both, writing Screenplay and Novels.

---

### Post by Docaltmed on 2013-02-25
Scrivener is by far the best of the bunch, both for fiction and non-fiction. It isn't a wikithingy at all.

Although it is still in beta, I've been using it for about two years. The first couple of versions were kinda creaky, but the app has been rock-solid for the better part of a year now.

If you go to the web site, it won't say a thing about Linux, as the Linux version is "unofficial." However, if you go to the forums:

[http://www.literatureandlatte.com/forum/](http://www.literatureandlatte.com/forum/)

You will find a subforum for the Linux crowd there. While new versions of the software are released as tarballs, somebody usually makes a .deb out of them fairly fast. The developers aren't really into unix, and thus they make some kind of wierd decisions for FOSS-worlders; like they release time-bombed versions that will die after a given date (at this point usually 9 months down the road). The devs claim this is so bug reports don't get confused between versions.

I far prefer the Launchpad/Sourceforge/Bugzilla release/reporting style, but what the hey. It works for them.

There is really good support for ubuntu users on the forum, and at this point the only real hiccup are 32-bit libraries that 64-bit users don't have on their installations, the .deb packagers always miss those, and then you have to scratch around and find them yourself. Or wait a couple of days.

It may seem like the Linux platform is a me-too kind of thing for these devs, but I have to say, the major bugs get fixed a lot faster than on a lot of gnome-standard programs (did someone say Evolution?).

I'm serious. I used to be a full-time professional writer and editor, and this is the best program I've used since 1982. Check it out.

---

