---
title: "how do I get started?"
date: 2007-08-23
forum: General Help
---

### Post by Valkyrie Wrath on 2007-08-23
I dont know how to use Wine. I dont know if its Wine or not but when I try to install Image converter Plus it opens Wine in the background and I get an error message that says 80000100 (I cant remember the whole thing?. Also, where can I find the basic commands for the terminal?

---

### Post by WiseElben on 2007-08-23
I don't know if that will work in Wine, but there are a lot of other options:

* GIMP
* nautilus-image-converter (it's in the repos, install using apt-get)
* ImageMagick - [http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)
* Google's Picasa - [http://picasa.google.com/](http://picasa.google.com/)

As for basic terminal commands, just search Google:

* [http://www.ss64.com/bash/](http://www.ss64.com/bash/)
* [http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal)

---

### Post by tszanon on 2007-08-23
> **Valkyrie Wrath said:**
> I dont know how to use Wine. I dont know if its Wine or not but when I try to install Image converter Plus it opens Wine in the background and I get an error message that says 80000100 (I cant remember the whole thing?. Also, where can I find the basic commands for the terminal?
Basic commands for the terminal: [http://www.linuxcommand.org](http://www.linuxcommand.org)
Never used it, but the index tells me it's very friendly. Just found it using google. :)

First, make sure that the application you want to use has been tested with Wine in [http://appdb.winehq.org/](http://appdb.winehq.org/). After installing wine, go to the terminal and type
```
winecfg
```
It will create the folder ~/.wine, that contains the "fake windows files". It's also where the programs you install will be contained.

Then, to use wine, go to the terminal, go the program folder (probably something like ~/.wine/drive_c/Program\ Files/program_folder) and type
```
wine <program.exe>
```

It should work.

---

