---
title: "noob disaster"
date: 2005-04-23
forum: General Help
---

### Post by Noobenstein on 2005-04-23
Ok I'll see what I can do to retrace all my steps here. It wasn't prity.

It all started with me looking for games. I decided I wanted to try this one [http://themanaworld.org/](http://themanaworld.org/)  Upon trying compile it I found I needed to get all the dependencies. But rather than checking the documentation I just checked the error messages when I was compiling it. That did eventually work, but I think I created alot of duplicate files when doing ./configure, make, and make install multiple times for each application. When I tried to run it I got this 
$ tmw
tmw: error while loading shared libraries: libguichan_sdl.so.0: cannot open shared object file: No such file or directory

That file exists in /usr/local/lib along with libguichan_sdl.so, libguichan_sdl.so.0.0, and libguichan_sdl.so.0.0.0 and a bunch of other files with the same duplicates. So I decided to search the file system for anything containing libguichan and delete them, redownload the sources for everything and just start from scratch. Well I don't think I found and deleted everything because after doing everything again I still get 
$ tmw
tmw: error while loading shared libraries: libguichan_sdl.so.0: cannot open shared object file: No such file or directory
 :-? 
I checked /usr/local/lib and it  has the files with so.0.0.0 in it again, including the file it says it can't find.

So what should I do now? Please be gentle; extremly frustrated uber-noob  ](*,) 

On another note, does anyone know a really good site for learning linux? I can't seem to find a decent one on my own and I'm getting real sick of turning simple tasks into my own little noob adventures through labarinths of despair. Thanks guys.

---

### Post by k.ODOMA on 2005-04-23
I can't speak directly to the problem of libguichan (although I have had similar problems that were solved by creating a symbolic link for the version of the library that was installed with the version the program was looking for), but have you tried installing the Debian package for TMW? Seems like you'd probably have better luck.

---

### Post by az on 2005-04-23
If you have foo.so and you need to compile something with it, you need it's headers.

foo.so is part of the libfoo package.  You would need the libfoo-dev package.

Go to:

packages.ubuntu.com

---

### Post by tread on 2005-04-23
Create a symbolic link as the person two posts above me suggested.

Say you want a library called foo.0.0.1 but you have foo.0.0.3 in your directory (since you have a newer version, it should work, right? not quite.)


Create a symbolic link thus:

ln -sf foo.0.0.3 foo.0.0.1

And you should be good to go.

Also, multiple ./configure, make, make install will just keep installing the same file in the same place repeatedly, so you wont be creating duplicate copies afaik.

---

### Post by Noobenstein on 2005-04-23
The thing is the file that it says does not exist is sitting right there in /usr/local/lib
So what would I need to link to what?

---

