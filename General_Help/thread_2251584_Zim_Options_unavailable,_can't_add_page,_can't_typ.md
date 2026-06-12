---
title: "Zim: Options unavailable, can't add page, can't type"
date: 2014-11-05
forum: General Help
---

### Post by Bucky Ball on 2014-11-05
Hi all,

I can't survive without Zim! The Zim notebook I use for all my *buntu bits no longer gives me the option to add a new page or sub-page. Also, everything under the Insert and Format heading is greyed out and unavailable, as are most things under Edit and a few things under the other headings. No clues.

Oddest thing is, open other notebooks and they work fine so I guess the upside is I know it's confined to that notebook. Downside is I need to be able to add pages to that notebook and change things AND be able to edit the right hand text boxes.

I have attached a screenshot of the greyed out menu (first pic) and one of how it's supposed to look from another notebook. 

Could the notebook be full? Is there a size limitation? If so, can I tweak a file to change? Scratching my head, but will keep digging. Haven't found any clues online ... yet. :-k

Tnx in advance ... ;)

---

### Post by Bucky Ball on 2014-11-05
* Update: Just looked in my notebooks directory and noticed two of the five notebooks were missing, notably the one that is broken and another one I haven't tried. Go to Zim and click 'Open Notebook' and at the selection window, notice those two are indeed in another folder than the others. 

When I open the *buntu Bits notebook directly by clicking the notebook.zim file in that folder it opens and I have all options. When I open it through the Zim GUI, no options. 

And further to that, I opened the other notebook that is in the other directory with it from the selection GUI and that works fine, all options present. Thought I'd figured it out, but not at this point ...

---

### Post by Irihapeti on 2014-11-05
You could try the following. I use it when occasionally when things go weird.

Quit zim and run from the commandline 
```

	zim --index notebooks/notes/notebook.zim -V


```

Change the path and notebook name as needed.

This will flush and rebuild the index table.

Not sure if it will help in your case, but I don't see it doing any harm.
(But I could be wrong...)

---

### Post by tgalati4 on 2014-11-05
Check the SMART status of your hard drive:

```
sudo smartctl -a /dev/sda
```

The last time I had problems with *zim* was when my hard disk was starting to fail.  

Open the file in *gedit* or *pluma* and see if there is any binary gibberish in the file.

I agree, I can't live without *zim*.

---

### Post by Bucky Ball on 2014-11-05
```
zim --index notebooks/notes/notebook.zim -V
```

No diff.

```
sudo smartctl -a /dev/sda
```

All clear. Passed.

Very peculiar. Have made no changes prior to the errant behaviour. Was working absolutely fine one day, not the next. Can't remember a Zim update that may have broken it recently. I'm using 14.04 LTS incidentally. ;)

---

### Post by tgalati4 on 2014-11-05
```
gedit ~/Notebooks/notes/Home.txt
```

Go through each file in your directory hierarchy and make sure that each file is text-only and is intact. All it would take is one file of gibberish to mess up the indexing and render Zim inoperative.

Backups are a good idea at this time.

---

### Post by Bucky Ball on 2014-12-07
Hi all. I just discovered the fix for this. Along the top of Zim there are a bunch of icons. One is like a paper and pen and is 'Toggle notebook editable'. I must have accidentally clicked on that and not noticed. Didn't even know this option was available! Clicked on that icon and back to normal. 

Anyhow, that simple, and solved. Thanks for the input. ;)

---

