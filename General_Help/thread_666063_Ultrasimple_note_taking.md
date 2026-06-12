---
title: "Ultrasimple note taking?"
date: 2008-01-12
forum: General Help
---

### Post by sicofante on 2008-01-12
I'm looking for an ultrasimple note taking program. I'm used to [NotesHolder]("http://notes.aklabs.com/") in Windows and that's the sort of functionality I'm looking for. (I haven't tried running it under Wine, but I'd rather choose a native Gnome app before doing that.)

Tomboy would do it if it didn't force me to click on the icon to open a menu and then choose "New note" from the menu. It's a lot of mouse work when I'm on the phone and I just want to write down a phone number or anything that simple. If there was a one-click-to-new-note action I could use with Tomboy I would be happy.

Thanks for any help.

---

### Post by tgalati4 on 2008-01-13
You could program a hot-key to generate a new note, say a multimedia key or a function key or a hot-key combo.

I like zim:

>sudo apt-get install zim

---

### Post by sicofante on 2008-01-13
> **tgalati4 said:**
> You could program a hot-key to generate a new note, say a multimedia key or a function key or a hot-key combo.
You mean I can do that for Tomboy? How?

Regarding Zim, it's nice but far from ultrasimple.

---

### Post by ugm6hr on 2008-01-13
> **sicofante said:**
> If there was a one-click-to-new-note action I could use with Tomboy I would be happy.

Why not create a panel shortcut for a new note in Tomboy?

Right-click whichever panel you want it on - select Add to Panel.
Create a *custom application launcher* with the command:
```
tomboy --new-note
```

You can use the Name and Comments to make it clear that it will start a new note in Tomboy.  You can also change the icon (by clicking on it) to whatever you want.

PS: It will mean that you have a panel icon and a system tray icon for Tomboy at the same time when it is running.  Shouldn't be too confusing though.

Other option is to set a hotkey for new note in Tomboy.  Right-click Tomboy system tray icon and select Preferences.  Select HotKets tab.  You can set whatever hotkey you want in "Create new note" - just be wary not to set something that is already assigned to a different program / unction.

Hope that helps

---

### Post by r57 on 2008-01-13
Hi there! 

> 
I'm looking for an ultrasimple note taking program.


What about sticky notes applet. You could add it to any of your panels and it is fast and simple as U wish. 

Dunno if U could use key to qickly add note thought.

Simply click on panel with right mouse button and choose "Add to panel..." there U should find it.

Hope it helps.

---

### Post by sicofante on 2008-01-13
Thanks guys. The launcher idea has got me reading Tomboy's man page and I've seen I can create a key binding for creating new notes. [EDIT: Errr, sorry, you also suggested that.] I guess I'll try both the launcher in the panel and the key shortcut. Now I have to investigate how to create a truly empy new note, that is, without any title in it and without that "Describe your new note here." text in it.

I tried sticky notes before and it's OK, but one feature I do value is being able to search notes (after a week or two I can have lots of them), and I can't seem to find any such capability in stickies. Thanks for the tip though.

---

### Post by Eric Weir on 2008-02-02
> **tgalati4 said:**
> I like zim:

I take it you're a user. What version do you have? I've installed the one form the repositiories, but it's out of date, and I understand the most recent version has significant additional features. 

I'm considering Zim as a replacement for a Windows free-form database application -- InfoSelect -- that I've been using for about 15 years. It's the only Windows application for which I haven't found a ready Linux replacement.

I'd be interested in a report on your experience using Zim.

Thanks,

---

### Post by thetree on 2008-04-11
If you want something simple yet flexible, try out [BIXTEP](http://www.bixtep.com). It's text only and you can organize your notes with tags.

---

### Post by Eric Weir on 2008-04-12
> **thetree said:**
> If you want something simple yet flexible, try out [BIXTEP]("http://www.bixtep.com"). It's text only and you can organize your notes with tags.
Thanks. I've not come across this before. I'll check it out. 

I'm looking for a replacement on Linux for MaxThink, an ancient DOS app that I'd been using the last several years in a DOS window on Windows. I've got it running in DOSbox now, which is reasonably satisfactory. 

The MaxThink developer says he's working on a version for Mac and Linux that would be command drive, the way the DOS version of MaxThink is, but I'm ot counting on it anytime soon. 

[The Windows/GUI version is a completely different program as far as I'm concerned. I could just never get with it. Imagine that, spoiled for Windows by a DOS app! What that speaks to for me is the power of MaxThink in its original command-driven form.]

I'll let you know what I think of BIXTEP.

Regards,

---

### Post by sicofante on 2008-05-10
I've found this today:

Tobu ([http://tobu.lightbird.net](http://tobu.lightbird.net))

It isn't ready for mainstream yet (somewhat buggy and some missing features), but it's nice and simple and can be used both with Windows and Linux (which is good for switchers).

---

### Post by Eric Weir on 2008-05-11
> **sicofante said:**
> I've found this today:

Tobu ([http://tobu.lightbird.net](http://tobu.lightbird.net))

Thanks. I might find I can work with it, but the use of tagging takes it out of the "simple" domain for me. 

InfoSelect, that I'm still running on an XP laptop doesn't use tagging -- or anything else. You just enter your text into a note. It searches on text. I've got about 50 files, some with only a few notes, but altogether quite a few. It has all my contact info going back to 1990. 

I just hit f5 and start typing a character string, any character string, that I think's likely to be in the note I'm looking for. Usually a unique note will pop up in a second or so. At a minimum a few notes that I can quickly scan. 

Notes are also organized heirarchically, which is sometimes helpful in locating things when the first method doesn't work or I'm uncertain of the character string to use. 

Do you know if Tobu can import?

Regards,

---

### Post by Eric Weir on 2008-05-11
I should mention this, too: [http://www.tiddlywiki.com/](http://www.tiddlywiki.com/)

 The following is from the creator's introduction:

> Welcome to [TiddlyWiki]("http://javascript%3Cb%3E%3C/b%3E:;"), a [popular]("http://javascript%3Cb%3E%3C/b%3E:;") free [MicroContent]("http://javascript%3Cb%3E%3C/b%3E:;") [WikiWikiWeb]("http://javascript%3Cb%3E%3C/b%3E:;") created by [JeremyRuston]("http://javascript%3Cb%3E%3C/b%3E:;") and a busy [Community]("http://javascript%3Cb%3E%3C/b%3E:;") of independent developers. It's written in HTML, CSS and JavaScript to run on any modern browser without needing any [ServerSide]("http://javascript%3Cb%3E%3C/b%3E:;") logic. It allows anyone to create personal [SelfContained]("http://javascript%3Cb%3E%3C/b%3E:;") hypertext documents that can be posted to a WebServer, sent by email or kept on a USB thumb drive to make a [WikiOnAStick]("http://javascript%3Cb%3E%3C/b%3E:;"). Because it doesn't need to be installed and configured it makes a great [GuerillaWiki]("http://javascript%3Cb%3E%3C/b%3E:;"). This is revision 2.4.0 of [TiddlyWiki]("http://javascript%3Cb%3E%3C/b%3E:;") (see [recent changes]("http://trac.tiddlywiki.org/wiki/History")), and is published under an [OpenSourceLicense]("http://javascript%3Cb%3E%3C/b%3E:;").There is a fantastic community of highly creative and genuinely helpful developers and users that can be found at: [http://groups.google.com/group/TiddlyWiki](http://groups.google.com/group/TiddlyWiki) 

There are also abundant examples on the web of the ways people have used TiddlyWiki. With it's platform independence, great versatility, and seemingly endless customizability, it's very appealing. It does make heavy use of tagging, though.

Regards,

---

### Post by sicofante on 2008-05-12
> **Eric Weir said:**
> Thanks. I might find I can work with it, but the use of tagging takes it out of the "simple" domain for me.
You're right. As a matter of fact, after a few hours of use, I uninstalled it. I guess I should've waited before posting

> 
Do you know if Tobu can import?
I don't know sorry.

---

### Post by Eric Weir on 2008-05-12
> **sicofante said:**
> You're right. As a matter of fact, after a few hours of use, I uninstalled it. I guess I should've waited before posting.

This is one area where Linux seems to be poor compared to Windows and OSX. There are numerous freeform applications in both domains I have yet to see anything in Linux comparable to the things I've found useful for Windows. 

This and other things -- the fact that even with Ubuntu I have to be a lot more involved in system setup and maintenance than I want to be -- might cause me to go out and get myself a Mac.

Thanks for suggesting Tobu, even though it didn't work out.

Sincerely,

---

