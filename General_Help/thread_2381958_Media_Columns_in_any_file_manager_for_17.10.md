---
title: "Media Columns in any file manager for 17.10"
date: 2018-01-07
forum: General Help
---

### Post by David4321 on 2018-01-07
I'm trying to find a file manager setup that includes media columns from metadata, like track length, artist, etc. for music files.

My preferred fm is Nemo, and there is a plugin, nemo-media-columns, but I was unable to install  this in 17.10. I keep getting unresolvable dependencies, notably python-pypdf. I've added several repositories recommended on forums, with no success installing nemo-media-columns or python-pypdf.

Any suggestions? Just resolving this for Nemo would be optimal, but I'd be open to alternative file explorers too. Any FM that has this feature, or available with plugin would be worth a look. My need is to have artist, track length, etc displayed as file details in columns, not just in a side panel per file. Thanks.


Update: apparently python-pypdf is retired in 17.10, updated package is python-pypdf2. I have this installed, however nemo-media-columns still requires python-pypdf and will not install. Does anyone know a work around? Can nemo-media-columns be manually edited to accept python-pypdf2 as dependency, and would this work? Or can python-pypdf somehow also be installed alongside without causing problems? No repositories seem to still have python-pypdf, or perhaps just will not allow install in 17.10.

---

### Post by David4321 on 2018-01-12
I redrafted this thread title and text to expand the topic and try to get some attention. I'm hoping adding this comment will bump it back to the top of the queue.

---

### Post by vasa1 on 2018-01-12
Even a plain "bump" every twelve hours is fine.

> **David4321 said:**
> I... I keep getting unresolvable dependencies, notably python-pypdf. I've added several repositories recommended on forums, ...
You could post actual specifics such as terminal output and the names of the "repositories".

---

### Post by cruzer001 on 2018-01-12
If you can live with Nautilus it also has the plugin.

Python-pypdf is in the repositories, wonder why it wont load.

Have you given the nemo ppa a spin?

[https://launchpad.net/~webupd8team/+archive/ubuntu/nemo3](https://launchpad.net/~webupd8team/+archive/ubuntu/nemo3)

---

### Post by Yellow Pasque on 2018-01-12
> **David4321 said:**
> Can nemo-media-columns be manually edited to accept python-pypdf2 as dependency, and would this work?

You could hack the media-columns .deb's control file to depend on python-pdf2. That would probably make it install. I don't know if it would run correctly, because it's still looking for pypdf. It would probably be better if upstream ported to use pypdf2. I don't how involved that would be. In the best case, you would only have to change this line:
[https://github.com/linuxmint/nemo-extensions/blob/5ad18ce0f729066a309ab107ef6b98dc6c8232c0/nemo-media-columns/nemo-media-columns.py#L39](https://github.com/linuxmint/nemo-extensions/blob/5ad18ce0f729066a309ab107ef6b98dc6c8232c0/nemo-media-columns/nemo-media-columns.py#L39)

---

### Post by mc4man on 2018-01-12
> **Temüjin said:**
> You could hack the media-columns .deb's control file to depend on python-pdf2. That would probably make it install. I don't know if it would run correctly, because it's still looking for pypdf. It would probably be better if upstream ported to use pypdf2. I don't how involved that would be. In the best case, you would only have to change this line:
[https://github.com/linuxmint/nemo-extensions/blob/5ad18ce0f729066a309ab107ef6b98dc6c8232c0/nemo-media-columns/nemo-media-columns.py#L39](https://github.com/linuxmint/nemo-extensions/blob/5ad18ce0f729066a309ab107ef6b98dc6c8232c0/nemo-media-columns/nemo-media-columns.py#L39)
I think that would be helpful, it may also need python-imaging package installed. managed to get it going in my 18.04 ubuntu with nemo install, screens
Tried quickly on a album folder of flac, everthing i enabled but bitrate showed.. (tried on other music files & the  bitrate showed, guess those flacs aren't tagged for that..
If I was to use the extension would probably try to limit it to specific folders, not overall in list view.

---

