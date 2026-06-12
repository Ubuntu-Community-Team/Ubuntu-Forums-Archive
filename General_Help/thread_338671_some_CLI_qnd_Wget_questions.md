---
title: "some CLI qnd Wget questions"
date: 2007-01-14
forum: General Help
---

### Post by Darth_tater on 2007-01-14
ok... ive got two simple (i assume they are simple to a seasoned CLI specialist)

1) is there a way, to do a massive find/replace on a text file?
          i ask because i am doing some web dev work and i need to convert hundreds of links in a            html file.  like for example.. is there any way that i can simply say that for every time you find "target= <some variable content here>  <br />"  and simply change it/remove it?

2) using wget, is there a way that i can specify to get all of the paths listed in a file...
eg: tell wget to go to 

edit: see explanation in below post. thanks!

thanks for the help!
i am sorry if this isint specifically ubuntu related, but this is linux CLI related and i dont know where else to ask.

thanks!

---

### Post by aysiu on 2007-01-14
I have some general answers but nothing specific.

#1, there is a command called *sed* that can do find/replace within files. I don't know the syntax for it, though.

#2, you can specify with *wget* to go several (1, 2, 3, etc.) directory levels deep. I'm not sure if that's exactly what you're looking for.

---

### Post by ardchoille42 on 2007-01-14
If the file has the following text:

---begin file---
This is a small test
---end file---

the command

```

sed -i 's/a small/another big/g' /path/to/filename

```

Will yield this:

---begin file---
This is another big test
---end file---

The "-i" option means "in line", so it edits the file and saves the changes back to the file instead of saving changes to a new file.

I use "sudo sed -i 's/use-ssh-agent/* use-ssh-agent/g' /etc/X11/Xsession.options" to comment out the line "use ssh-agent" in /etc/X11/Xsession.options.

---

### Post by Darth_tater on 2007-01-14
> **aysiu said:**
> I have some general answers but nothing specific.

#1, there is a command called *sed* that can do find/replace within files. I don't know the syntax for it, though.

#2, you can specify with *wget* to go several (1, 2, 3, etc.) directory levels deep. I'm not sure if that's exactly what you're looking for.

1)  ill play arround with SED

2) not quite, i want wget to do something like this (im doing this manually now and i have another few hundred directories to go through.. its a PITA)

wget http:<address>/static/path/tofiles/<dynamic path to files>/[1-20].ext (example)

also, when i put "[1-20].ext" i want wget to download the files numbered 1-20 with the extension .ext only (as an example...)

soo, i want to have a list of those dynamic paths (comma separated, or W/e, it dosent matter; ill format it to however i need to)

so lets say that this was the contense of my list
list: 
example,jimbob,darth_tater

wget would go to the following URL's

http:<address>/static/path/tofiles/example/1.ext
http:<address>/static/path/tofiles/example/2.ext
ect...
http:<address>/static/path/tofiles/example/20.ext

and

http:<address>/static/path/tofiles/jimbob/1.ext
http:<address>/static/path/tofiles/jimbob/2.ext
ect...
http:<address>/static/path/tofiles/jimbob/20.ext

and

http:<address>/static/path/tofiles/darth_tater/1.ext
http:<address>/static/path/tofiles/darth_tater/2.ext
ect...
http:<address>/static/path/tofiles/darth_tater/20.ext


that clear it up?  sorry if my previous explanation was hard to understand.  



any idea how? or any download manager that will work ?

---

