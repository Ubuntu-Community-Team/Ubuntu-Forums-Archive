---
title: "Display system info on desktop?"
date: 2007-05-28
forum: General Help
---

### Post by wie6Ein0 on 2007-05-28
While viewing linux user's screenshots on DeviantART, I found a screenshot with system details visible on the desktop...

Please, help me get a similar setup: [http://www.deviantart.com/deviation/55136051/](http://www.deviantart.com/deviation/55136051/)

---

### Post by notwen on 2007-05-28
If you're referring to the slim bar up top.  I believe that is conky running in it's own window.  Check out this [thread]("http://ubuntuforums.org/showthread.php?t=353362") to compile it, it's very easy to do. Post back here or within the thread linked above if you run into any issues.  =]

You may also want to check out this [thread]("http://ubuntuforums.org/showthread.php?t=281865") to view other ppl's individual conky configs.  Conky is fun, you can always copy what you want from other ppls configs, put them to use and even modify them to look the way you wish.  You can make conky be extremely small and simple or very complex and show multiple details/information on your desktop.

---

### Post by wie6Ein0 on 2007-05-28
> **notwen said:**
> If you're referring to the slim bar up top.  I believe that is conky running in it's own window.  Check out this [thread]("http://ubuntuforums.org/showthread.php?t=353362") to compile it, it's very easy to do. Post back here or within the thread linked above if you run into any issues.  =]

You may also want to check out this [thread]("http://ubuntuforums.org/showthread.php?t=281865") to view other ppl's individual conky configs.  Conky is fun, you can always copy what you want from other ppls configs, put them to use and even modify them to look the way you wish.  You can make conky be extremely small and simple or very complex and show multiple details/information on your desktop.

I ended up installing Conky using "sudo apt-get install conky" and run it by typing conky in either the terminal or the run dialog box.

Can you give me a hint on where the conkyrc file is so that I can edit it? I tried searching 'filesystem' but found no results.

---

### Post by LPomfrey on 2007-05-28
> **westoncampbell said:**
> I ended up installing Conky using "sudo apt-get install conky" and run it by typing conky in either the terminal or the run dialog box.

Can you give me a hint on where the conkyrc file is so that I can edit it? I tried searching 'filesystem' but found no results.
The file .conkyrc is in "/home/<username>/"

In Nautilus press Ctrl+H to view hidden files to see it.

There is a thread here: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865) where people have posted their .conkyrc files and screenshots of how it looks if you need any ideas and/or help setting it up.

---

### Post by notwen on 2007-05-28
When typing conky you're using the default conkyrc file provided w/ conky.  You'll need to create your own .conkyrc file in your /home/usernamehere folder.  In a terminal simply type "gedit.conkyrc" ; this will open up gedit(similar to notepad) and you can copy someone's config file from the 'post your .conkyrc' thread and save it.  Conky automatically tries to use your .conkyrc in your home/usernamehere folder before defaulting back to the one included w/ installation.  The thread w/ ppl posting their conky configs should have something similar to the screenshot you linked to.  Scream if you have any issues. =]  The compiling thread also has instructions on how to add conky to startup so you'll always see it upon botting up your machine, be sure to note if you're running a composite manager(beryl or compiz) you'll need to be sure to add adequate time for your composite manager to load before conky.  Good luck. =]

---

