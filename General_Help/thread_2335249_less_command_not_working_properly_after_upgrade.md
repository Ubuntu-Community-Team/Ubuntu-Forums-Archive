---
title: "less command not working properly after upgrade"
date: 2016-08-26
forum: General Help
---

### Post by chopra on 2016-08-26
After upgrading from Ubuntu 14.04 to 16.04.1 LTS on my laptop, the less command is behaving wierd.  Whenever I view a file whose text is smaller than the size of the termial window, it appears on the bottom of the screen instead of the top.  I have to use either the scroll wheel on my mouse or the arrow keys to fix it, after which, normal behavior returns.  This is something that also occurs even when I am using the less command on a remote terminal from my laptop, where the remote system is another distro of linux.

The other difference in behavior is that less is supposed to suppress viewing of binary files unless the -f option is used.  This now happens for a small fraction of binary files, but for the majority of them, it behaves as if the -f option had been used. (device files it will still refuse to open without the -f option, as it should.)  This seems to have no connection to the size of the file.  Ordinarily, the presence of the nil character is what the command has used to determine binaries, but this no longer seems to be the case, as all binary files I've tried have plenty of null characters in them.

Chopra

---

### Post by chopra on 2016-08-27
UPDATE:
The misbehavior of the -f option seems to be specific to the executable.  I have an older machine with ubuntu 14.04 on it, and I copied the less executable from that machine into the home directory of my current laptop (with ubuntu 16.04) and the old copy of less behaves properly as far as asking before opening a binary.  The other problem, however, still remains.

---

### Post by steeldriver on 2016-08-27
I don't know why it's changed, but you should be able to change the 

```

    -c or --clear-screen
           Causes  full  screen  repaints  to  be painted from the top line
           down.  By default, full screen repaints are  done  by  scrolling
           from the bottom of the screen.

```

You can hit -c inside an existing less session, as a command line option
```

less -c file

```

or by setting the value of the LESS environment variable

```

export LESS='-c'

```

---

### Post by chopra on 2016-08-27
Perfect.  Adding 
```

export LESS='-c'

```
to my .bashrc file fixes the screen behavior, although I must also do this in my home directory for remote accounts.
Also, moving the copy of the less executable from the older ubuntu 14.04 machine to my ~/bin directory fixes the problem of not supressing binary files.

I'm not sure what caused either of these problems, the first one in particular is rather odd, but at least it's solved now.

Thanks, Chopra

---

