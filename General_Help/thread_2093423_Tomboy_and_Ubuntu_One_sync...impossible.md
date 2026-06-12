---
title: "Tomboy and Ubuntu One sync...impossible?"
date: 2012-12-10
forum: General Help
---

### Post by Mr. Beekeeper on 2012-12-10
I'm at my wit's end.  I've done everything possible, even compiling the latest version from a tarball.  **Tomboy simply will not sync with Ubuntu One**, and there’s nothing in the "Details" section.  I've re-installed, cleared the settings, and added 15 or so "computers" to my Ubuntu One account (it adds a new one every time I configure it)  My iPhone syncs with it fine via webNotes app.  Why on earth is a native app being so difficult?  I've searched the web, but most of the posts are from 2010 or earlier.  

Please help...

...thanks!

---

### Post by qamelian on 2012-12-10
Have you tried this?
[https://one.ubuntu.com/help/faq/how-do-i-setup-tomboy-notes-to-sync-with-ubuntu-one/](https://one.ubuntu.com/help/faq/how-do-i-setup-tomboy-notes-to-sync-with-ubuntu-one/)

---

### Post by Mr. Beekeeper on 2012-12-10
Thanks. That was the first thing I tried. It synced once and never again.

---

### Post by Mr. Beekeeper on 2012-12-10
From more searching, I found this is probably a bug from 2010, so I doubt it will be fixed.  It's odd that they still seem to be developing for it.  With the bug being that old, I'd have figured development had stopped.

[https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/449648](https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/449648)


This is what happens when I try to sync, starting from terminal with:

```
$ tomboy --debug
```



```
[DEBUG 21:39:37.257] SyncThread using SyncServiceAddin: Tomboy Web
[DEBUG 21:39:37.313] Building web request for URL: https://one.ubuntu.com/notes/api/1.0/
[DEBUG 21:39:39.582] Building web request for URL: https://one.ubuntu.com/notes/api/1.0/user/
[DEBUG 21:39:40.339] 8
[DEBUG 21:39:40.342] Sync: GetNoteUpdatesSince rev -1
[DEBUG 21:39:40.349] Building web request for URL: https://one.ubuntu.com/notes/api/1.0/op/?include_notes=true
[ERROR 21:39:42.171] Synchronization failed with the following exception: 'strikethrough' is expected  Line 9, position 4.
  at Mono.Xml2.XmlTextReader.Expect (System.String expected) [0x00000] in <filename unknown>:0 
  at Mono.Xml2.XmlTextReader.ReadEndTag () [0x00000] in <filename unknown>:0 
  at Mono.Xml2.XmlTextReader.ReadContent () [0x00000] in <filename unknown>:0 
  at Mono.Xml2.XmlTextReader.Read () [0x00000] in <filename unknown>:0 
  at System.Xml.XmlTextReader.Read () [0x00000] in <filename unknown>:0 
  at Tomboy.Sync.NoteUpdate..ctor (System.String xmlContent, System.String title, System.String uuid, Int32 latestRevision) [0x00000] in <filename unknown>:0 
  at Tomboy.WebSync.WebSyncServer.GetNoteUpdatesSince (Int32 revision) [0x00000] in <filename unknown>:0 
  at Tomboy.Sync.SyncManager.SynchronizationThread () [0x00000] in <filename unknown>:0 

(Tomboy:7561): GLib-CRITICAL **: g_source_remove: assertion `tag > 0' failed

```




As frustrated as I am, I enjoy the fact that I'm using what Linux skills I have to try and get to the bottom of it.  You can get mad at bug, or just see them as an opportunity to learn!


:guitar:

---

### Post by Mr. Beekeeper on 2012-12-11
Ok.  It's working perfectly now.  Here's what I did.  You kinda have to file this one under "jiggle the handle" or "whack it a few times".  ;)

open a terminal and enter this:

note: if you're a newbie, the $ sign is where the command prompt ends; it's there for reference...don't actually enter it into the command prompt.

This navigates to where Tomboy keeps your notes:

```
$ cd ~/.local/share
```...and then this renames the note folder to another name so Tomboy won't see (or remove) it, but the files will remain safe:

```
$ mv tomboy tomboy.old
```...then COMPLETELY rid yourself of Tomboy:

```
$ sudo apt-get purge tomboy
```Now, reinstall Tomboy:

```
$ sudo apt-get install tomboy
```...and change your notes folder back:

```
$ mv tomboy.old tomboy
```Everything worked fine after that.


Note:  If anyone with more knowledge knows some tips to add, or corrections, please add them!  

Cheers!

---

### Post by Mr. Beekeeper on 2012-12-13
Nevermind.  The problem appears to be with mono:

```
[DEBUG 13:09:41.681] Building web request for URL: https://one.ubuntu.com/notes/api/1.0/op/?include_notes=true&since=265
[ERROR 13:09:42.125] Synchronization failed with the following exception: 'note-content' is expected  Line 9, position 53.
  at Mono.Xml2.XmlTextReader.Expect (System.String expected) [0x00000] in <filename unknown>:0 
  at Mono.Xml2.XmlTextReader.ReadEndTag () [0x00000] in <filename unknown>:0 
  at Mono.Xml2.XmlTextReader.ReadContent () [0x00000] in <filename unknown>:0 
  at Mono.Xml2.XmlTextReader.Read () [0x00000] in <filename unknown>:0 
  at System.Xml.XmlTextReader.Read () [0x00000] in <filename unknown>:0 
  at Tomboy.Sync.NoteUpdate..ctor (System.String xmlContent, System.String title, System.String uuid, Int32 latestRevision) [0x00000] in <filename unknown>:0 
  at Tomboy.WebSync.WebSyncServer.GetNoteUpdatesSince (Int32 revision) [0x00000] in <filename unknown>:0 
  at Tomboy.Sync.SyncManager.SynchronizationThread () [0x00000] in <filename unknown>:0 

(Tomboy:2733): GLib-CRITICAL **: g_source_remove: assertion `tag > 0' failed

```


I'm giving up.  I'm going to search for an alternative note application that can sync.  It's sad no one is actively pursuing bugs on this anymore.  It was a useful app.  It's too unpredictable.  I can't waste any more time fiddling with it only to have it break.  It's a waste of time.

---

### Post by Mr. Beekeeper on 2012-12-13
OK.  I think I figured out the problem...again.  It's with webNotes, not Tomboy, well maybe it's both. 

I'm using the webNotes app on an iPhone.  When you edit a note with this app, you're editing the raw xml (I think) data.  To duplicate this bug, follow these steps:

Make a note, using Tomboy with the text "foobar", where foobar is a link to another note.  Synchronize.

Now, open this note for editing with webNotes, do nothing to it but click 'save'... it changes the link to something that mono won't accept, causing it not to sync.  Here's an example:

(for clarity, this is being typed in webNotes, NOT Tomboy, and the note only contains the word "foobar", which is a link to another note.)


**Note in plain text before editing:**

foobar

**Note in editing mode:**

```
<link:internal>foobar[/a:link]
```

**When you hit "save" the note in plain text now looks like this:**

<link:internal>foobar

Synchronize notes using webNotes.  Now Tomboy won't sync.  It'll give you the error I posted above or something similar.  If you delete or edit the note so it no longer has that link, you can sync again.

Sorry if this wasn't super clear.  I'm going to write an email to the webNotes developer.  I just hope to save someone else a headache, because that's what Ubuntu and this forum are all about.  You people have good karma.  


):P

---

### Post by aardvark4 on 2012-12-19
Hi everyone. First, I'm really sorry for the inconvenience that this has caused anyone. I do think Mr. Beekeeper is right, though. From what it looks like, webNotes is properly converting the </link> tag into [a:/link], but it doesn't know about <link:internal>, which I suppose it would have converted to [a:link:internal] if I'd known about that one.

The reason for the conversions is an unfortunate limitation of the iPhone, and this is what's happening. The actual text of Tomboy notes is littered with its own specific tags, such as "<huge>text</huge>. The iPhone, unfortunately, doesn't support rich text editing and has only recently started to support rich text in labels.  That being the case, to SHOW the formatting in webNotes, I convert those tags into their equivalent HTML and show them in a web view. 

Without that step, in the preview of the note, you'd see the Tomboy-specific tags littered about instead of, say, large text.  When it's time to sync, I convert the stored [a:something]s back into Tomboy's own tags. The reason for the [a:something] at all, is really more just so that if you happened to have HTML tags in the note itself, it wouldn't also get cleared out or transformed. I hope that kind-of made sense, though I know it's a bit of a weird round-trip just to get formatting to show up. 

Long story short, for the short term, I will be adding the <link:internal> tag to the dictionary of things that webNotes knows about so that it gets transformed into something that Tomboy won't freak out about. I'll try and see if maybe there are any other tags I missed as well, to try and avoid this in the future. I'm sorry again for the inconvenience. That kind of update shouldn't be complicated, but it might take a few days because Apple will not be reviewing apps for a few days because of the holidays. I'll get it in the queue, though, and hopefully we can get this resolved before too long. In the long run, there is probably a better way to store the text on webNotes' end without doing all of those transformations (e.g. encode the whole thing instead of doing text replacements or something like that), and I'll look into it for the future.

Sorry again, and I'll try to get the update out as soon as I can.

Adam

---

### Post by aardvark4 on 2013-01-21
Hi everyone,

Sorry for the delay in getting the update out, but today there is an update to webNotes in the App Store that should address the links tags that were preventing the syncing. I think in most cases it should just correct itself the next time you sync with webNotes, but if not, if there are leftover orphan link tags in the notes (e.g. [/a:link] without an opening tag or something like that), you may want to clear them out manually. Sorry again for the inconvenience, and please let me know if there are further problems. 

Adam

---

