---
title: "Shell scripts not working?"
date: 2007-04-01
forum: General Help
---

### Post by deadowl on 2007-04-01
Well, I've been trying to install some software that uses shell scripts. 

However, this is not working. Every time I try to run a shell script, it tells me it found a ) or something before it found an fi. I look in the different shell scripts and it seems that symbols are balanced. I just don't get it :(.

How do I make it so shell scripts won't break like this?

---

### Post by KyleCardoza on 2007-04-01
open a terminal, and check the output of this command:

ls -l /bin/bash

If the output of that command looks something like this:

lrwxrwxrwx 1 root root 9 2007-03-10 02:12 /bin/sh -> /bin/dash

Then you probably need to run these commands to fix it:

sudo rm /bin/sh

sudo ln -s /bin/bash /bin/sh

This will replace the /bin/sh link to dash with a link to bash, which may be the problem.

---

### Post by yabbadabbadont on 2007-04-01
A simpler method would be, "sudo dpkg-reconfigure dash".  Answer "no" when asked if it should be used for /bin/sh.

---

### Post by deadowl on 2007-04-05
Still having problems. Right now I'm trying to run another shell script.

It references $appdir and $topdir a bit.
When it runs, it seems to look into usr/local/, when the stuff it needs is in usr/

The only things in usr/local/bin seem to be mathematica-related, but for the entire usr/local folder, there's only eclipse stuff, ocaml stuff, python stuff, ruby stuff, emacs stuff, and one other thing that I'm not going to mention.

ex. This happens when I try running continuum.sh
([http://wine.getcontinuum.com/](http://wine.getcontinuum.com/))

wine: failed to initialize: /usr/local/lib/wine/ntdll.dll.so: cannot open shared object file: No such file or directory

Let me add, to determine appdir, I'm guessing it's using this script:

appdir=""
case "$0" in
  */*)
    # $0 contains a path, use it
    appdir=`dirname "$0"`
    ;;
  *)
    # no directory in $0, search in PATH
    saved_ifs=$IFS
    IFS=:
    for d in $PATH
    do
      IFS=$saved_ifs
      if [ -x "$d/$0" ]
      then
        appdir="$d"
        break
      fi
    done
    ;;
esac

---

### Post by deadowl on 2007-04-08
Can anyone help me at all?

---

