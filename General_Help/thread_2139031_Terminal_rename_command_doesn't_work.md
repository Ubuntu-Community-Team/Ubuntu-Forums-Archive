---
title: "Terminal rename command doesn't work"
date: 2013-04-25
forum: General Help
---

### Post by tehmessiah75 on 2013-04-25
Hi,
I just installed Ubuntu 12.04-LTS on my laptop (Previously I've used Xubuntu).
I've been using Xubuntu for over 5 years.

Anyway, I have a problem with iTunes screwing up my mp3 library, which is now on my Xubuntu server.
I am trying to rename multiple files that have stupid naming, ie.. -_-_01-songtitle-album-ft-someidiot.mp3

So I use
```
rename -v 's/ft.*\.mp3/\.mp3/' *
```
and get an output of
```
Unknown option: shake.mp3Unknown option: z
Unknown option: z
Unknown option: _
Unknown option: t
Unknown option: o
Unknown option: p
Unknown option: gimme_all_your_lovin.mp3
Unknown option: z
Unknown option: z
Unknown option: _
Unknown option: t
Unknown option: o
Unknown option: p
Unknown option: sharp_dressed_man.mp3
```

The rename Command doesn't seem to be working properly.
I can do things like
```
rename -v 's/ft/FT/' *
```
I have installed renameutils to no effect.
I don't understand why this works in Xubuntu but not Ubuntu.
Please Help

---

### Post by steeldriver on 2013-04-25
That may be because you have filenames that begin with hyphens, which the shell is interpreting as options to the 'rename' command - try explicitly delimiting the end of the option list with '--' i.e.

```
rename -v **[COLOR=#ff0000]--[/COLOR]** 's/*pattern*/*replacement*/' *
```

I'm not sure your regex does what you think it does though - I suggest you run it with the -n switch first to make sure the replacements are what you expect

```
rename -[COLOR=#ff0000]**n**[/COLOR]v **[COLOR=#ff0000]--[/COLOR]** 's/*pattern*/*replacement*/' *
```

---

### Post by tehmessiah75 on 2013-04-25
Thank you steeldriver,
I'll give it a go and report back, asap.

---

### Post by scbingham on 2013-04-25
I too have similar problems with music file names.

Have a look at Sound Converter, it's available from the Software Centre.
Not only can it do file type conversion, it can rename bulk files too.

---

### Post by tehmessiah75 on 2013-04-26
I'm currently waiting for MusicBrainz Picard to finish retrieving id3 tags for all mu music (20K+ songs)
It's been running for over 5 hours now and it's still going. (It hasn't frozen BTW just taking its time!)
Once Picard has finished I can then rename the files according to their id3 tags (either with Picard or with pyRenamer, I dont know whats better yet).
Once I have done that, maybe Rhythmbox, with the File Organiser plugin, will actually reorganise my library into folders for me.

iTunes messed it up so many times, reorganising it, that I mave more than 6 copies of the majority of my music.
Damn them apples....!
So now I'm trying to easily/quickly fix it all.

---

### Post by scbingham on 2013-04-26
Sound Converter can also save & create into sub folders eg Artist/Album

Maybe in future keep your library organised somewhere sensible ie on your Ubuntu pc & just dump the lot onto your iPod with Rhythmbox.
And yes, Damn those apples! :twisted: Good luck!

---

### Post by tehmessiah75 on 2013-04-26
> **steeldriver said:**
> That may be because you have filenames that begin with hyphens, which the shell is interpreting as options to the 'rename' command - try explicitly delimiting the end of the option list with '--' i.e.

```
rename -v **[COLOR=#ff0000]--[/COLOR]** 's/*pattern*/*replacement*/' *
```

I'm not sure your regex does what you think it does though - I suggest you run it with the -n switch first to make sure the replacements are what you expect

```
rename -[COLOR=#ff0000]**n**[/COLOR]v **[COLOR=#ff0000]--[/COLOR]** 's/*pattern*/*replacement*/' *
```

Didn't work mate.
I tried 
```
sudo rename -nv -- 's/-(\D{1})/$1/' *
and
sudo rename -nv -- 's/\-(\D{1})/$1/' *
```

---

### Post by steeldriver on 2013-04-26
well it's hard to debug unless you provide some actual filenames to work with - but fyi this is the issue I was referring to:

```

$ > "-zztop.mp3"                        # <--- creates an empty file called -zztop.mp3
$ 
$ rename -nv 's/^-//' *.mp3
Unknown option: z
Unknown option: z
Unknown option: t
Unknown option: o
Unknown option: p
Unknown option: .
Unknown option: m
Unknown option: p
Unknown option: 3
Usage: rename [-v] [-n] [-f] perlexpr [filenames]
$ 
$ 
$ rename -nv [COLOR=#0000ff]**--**[/COLOR] 's/^-//' *.mp3
-zztop.mp3 renamed as zztop.mp3
$ 

```

---

