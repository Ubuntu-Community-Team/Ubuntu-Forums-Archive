---
title: "how do you use shell scripts?"
date: 2006-10-25
forum: General Help
---

### Post by EagleX on 2006-10-25
I'm working with Fluxbox, and want to install the idesktool so I can have icons on my desktop (link [here]("http://www.jmurray.id.au/ideskconf.html")). It says to download the script, copy to /usr/bin and then make it executable. Does that mean like .exe? I'm a little confused on this, I thought Windows executables didn't work in Ubuntu (except with wine).

I've seen allot of scripts for various things I'd like to use, so can someone please explain how you set them up so you can run them as programs?

Thanks!

~ Justin

---

### Post by po0f on 2006-10-25
EagleX,

```
$ sudo mv wherever/you/downlaoded/script.sh /usr/bin
$ sudo chmod a+x /usr/bin/script.sh
```

---

### Post by matthewstory on 2006-10-25
um . . . you can't run .exe files in Ubuntu . . . not even if you make them executable, but the previous post is pretty much right on how to make a script executable, then all you need to know is how to run it:

cd /path/to/script
./script.sh

That will do the trick nicely

---

### Post by po0f on 2006-10-25
EagleX,

If there are some scripts that you want to use but don't want all the users on the system to be able to use, you can make a directory in your home folder (~) called bin:
```
$ mkdir ~/bin
```
With a default ~/.bash_profile, this directory will automatically be prepended to PATH.  You can drop your scripts in here, and run them just like any other program.

```
$ mkdir ~/bin
$ echo "echo boo" > ~/bin/boo.sh
$ chmod +x ~/bin/boo.sh
$ boo.sh
```

[EDIT]

You'll have to close the terminal and open a new one for the change to take effect.

---

