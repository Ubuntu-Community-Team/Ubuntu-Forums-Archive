---
title: "Moving Configuration Directories and Files to a Sub-directory of Home Directory"
date: 2014-11-08
forum: General Help
---

### Post by budhajeewa on 2014-11-08
Is it possible to move all configuration directories and files (Dot-directories and dot-files.) inside a sub-directory of my home directory?


I always have hidden files and directories shown, so I hate seeing all those dot-directories and dot-files right inside my home directory.


If it is possible to create a sub-directory called "config" inside my home directory and move all my config files and directories inside that, it'll be ideal!


So, is this possible? Is there any way to accomplish this?

---

### Post by deadflowr on 2014-11-08
You probably could, but you would also need to make all you programs know where the new locations will be for the configurations.
It would more likely suit you to simply enable hide folders/files. (ctrl +h)

If for some reason the hide option is not working I would guess that is a bigger issue...

---

### Post by CantankRus on 2014-11-08
I doubt it as the applications that use these files and directories look in that specific location.
If you don't like looking at dot files and directories why do you want to always show hidden?
What else is there to look at when showing hidden files besides backup(~) files.

---

### Post by budhajeewa on 2014-11-08
> **deadflowr said:**
> You probably could, but you would also need to make all you programs know where the new locations will be for the configurations.
It would more likely suit you to simply enable hide folders/files. (ctrl +h)

If for some reason the hide option is not working I would guess that is a bigger issue...

Ah nope, hide option is working well. I personally don't like hidden files being... well.. hidden. :)

It would be nice if OS didn't pollute the entire home dir though, they cold be using a sub-dir in home dir.

---

### Post by budhajeewa on 2014-11-08
I guess this is personal preference then, anyway, they could move all config dirs and files into a sub-dir.

---

### Post by QIII on 2014-11-08
Hello!

It's not just Ubuntu.  Seems to be a terrible thing just about all of them do.  Both of my Fedora machines do the same.

openSUSE, too.

:)

Edit... Ooops.  Heck.  So does raspbian on my Pi!

;)

---

### Post by sudodus on 2014-11-08
So many linux programs are made to store user settings in the home directory. I think it is not worth the effort to move them, because there are probably many places, where is must be changed.

Instead I suggest that you choose another place where you enter your directory tree of personal files, either the desktop or a separate ***data*** partition. You can easily keep those directories free from hidden files (except maybe one hidden directory for the trashcan in the data partition).

---

### Post by budhajeewa on 2014-11-08
> **QIII said:**
> Hello!

It's not just Ubuntu.  Seems to be a terrible thing just about all of them do.  Both of my Fedora machines do the same.

openSUSE, too.

:)

Edit... Ooops.  Heck.  So does raspbian on my Pi!

;)

Yeah, looks like it is a bad trait of UNIX-like OSes. Wonder how MacOS does this.

Another wonder, why don't they agree upon moving configs into a sub-dir of home-dir?!

---

### Post by budhajeewa on 2014-11-08
> **sudodus said:**
> So many linux programs are made to store user settings in the home directory. I think it is not worth the effort to move them, because there are probably many places, where is must be changed.

Instead I suggest that you choose another place where you enter your directory tree of personal files, either the desktop or a separate ***data*** partition. You can easily keep those directories free from hidden files (except maybe one hidden directory for the trashcan in the data partition).

Well, that sounds like a good work-around.

But "home" dir is home dir; I think it's the places I am supposed to store my docs, pics and what-nots. I don't mind my OS creating a sub-dir called "config" inside it and moving all of the config files and dirs inside that. But polluting my "home" dir with configs? That's not nice.

---

### Post by QIII on 2014-11-08
Beats the heck out of a monstrosity like the Windows registry.

---

### Post by budhajeewa on 2014-11-08
> **QIII said:**
> Beats the heck out of a monstrosity like the Windows registry.

At least they don't have to open the Registry Editor daily.

---

### Post by Impavidus on 2014-11-08
Where to put those config files is not a choice of the OS, it's a choice of the application storing the config file. And many applications nowadays do exactly as you wish, by storing those files in the directory .config. But not all. If you want to move those config files from their default location to .config, you'll have to tell the applications where to find the config file via a command line option or an environment variable. How to do this is different for each application. For some applications, you can't. To make it work automatically you'll have to edit things like launchers, .desktop files, .bashrc or .profile or create aliases.

---

### Post by budhajeewa on 2014-11-08
> **Impavidus said:**
> Where to put those config files is not a choice of the OS, it's a choice of the application storing the config file. And many applications nowadays do exactly as you wish, by storing those files in the directory .config. But not all. If you want to move those config files from their default location to .config, you'll have to tell the applications where to find the config file via a command line option or an environment variable. How to do this is different for each application. For some applications, you can't. To make it work automatically you'll have to edit things like launchers, .desktop files, .bashrc or .profile or create aliases.

That's too much work IMO, I think I'll have to wait a decade or so until everyone of them decide to move their config into .config.

---

### Post by vasa1 on 2014-11-08
> **budhajeewa said:**
> That's too much work IMO, I think I'll have to wait a decade or so until everyone of them decide to move their config into .config.
Yep.

---

### Post by HermanAB on 2014-11-08
I gave up years ago: "Render onto Ceasar that which is Ceasar's." and usually put my own data in a directory called /data.  That is also the only thing I ever back up.

---

### Post by budhajeewa on 2014-11-08
> **HermanAB said:**
> I gave up years ago: "Render onto Ceasar that which is Ceasar's." and usually put my own data in a directory called /data.  That is also the only thing I ever back up.

I think I will do that too. :(

---

