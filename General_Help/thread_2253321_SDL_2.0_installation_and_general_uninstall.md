---
title: "SDL 2.0 installation and general uninstall"
date: 2014-11-18
forum: General Help
---

### Post by casper8000 on 2014-11-18
Hi, I'm super new to Ubuntu. I installed Ubuntu 14.04.1 LTS just this past weekend.  I'm trying to get SDL 2.0 up and running on it for Code-blocks.

I tried the method described in [https://www.youtube.com/watch?v=CiEwXjq4_yo](https://www.youtube.com/watch?v=CiEwXjq4_yo) George Hayes youtube video.  GPG (no clue what this is)/ updating libraries

That didn't seem to work.  So I tried this method. [http://askubuntu.com/questions/344512/what-is-the-general-procedure-to-install-development-libraries-in-ubuntu](http://askubuntu.com/questions/344512/what-is-the-general-procedure-to-install-development-libraries-in-ubuntu) (downloading source, compiling it using [SDL2-2.0.3.tar.gz]("https://www.libsdl.org/release/SDL2-2.0.3.tar.gz")[COLOR=#000000][FONT=DejaVuSansBook]  current vers off the website[/FONT][/COLOR])

That didn't seem to work either.  I've since tried purging SDL* on my machine to try and get everything off and start option 2 again.  I wanted to basically remove everything and start over again using option2.  Concerned that using option 1 put some things on that are somehow conflicting.  Is there a simple and straightforward way of doing that?

I tried [COLOR=#333333][FONT=Consolas]dpkg -s sdl2-2.0.3 [FONT=arial]in the ~/downloads/SDL2-2.0.3 directory and it stated it was not installed and no info is available.  [/FONT]

[/FONT][/COLOR]Any help is appreciated.  I'm very new and confused as to where all this is going on the PC, the ubuntu directories are generally a maze to me (being a long time windows user) and have no clue what's really going on other than searching and following instructions. 

Thanks,

---

### Post by casper8000 on 2014-11-18
third sites a charm.  This one worked.  [https://github.com/PluginIO/EX3/wiki/Setting-up-SDL2-in-Ubuntu-12.10](https://github.com/PluginIO/EX3/wiki/Setting-up-SDL2-in-Ubuntu-12.10)

my linker settings were a little hodgepodged, but I grabbed the one outta the first video and that worked!

---

