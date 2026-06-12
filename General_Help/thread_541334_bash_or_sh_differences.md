---
title: "bash or sh differences?"
date: 2007-09-02
forum: General Help
---

### Post by stlouis1 on 2007-09-02
well. i think i read somewhere that ubuntu's bash or sh scripting is different in someway....im not sure

but anyway, i had the linux version of heroes 3, on a retail disc, it came like that.

anyway, i wasnt able to install it on ubuntu, it kept giving me errors when i tried to run the sh install script.

but i've a spare computer running arch linux for a few days, and when i ran the sh script on the heroes 3 disc, it installed just fine

even for quake 2 on ubuntu, i had the change the first line in the sh script from sh to bash, and even that only sorta got it working. but i tried that for the heroes 3 install with no luck

anyway, basically, is there a way to get ubuntu to know how to use those scripts. im having a really hard time with arch linux, way too technical for me. but if its the only one that will run the games i bought for my desktop, ill have to install it instead of ubuntu.

does my question make sense?

---

### Post by cwaldbieser on 2007-09-03
```

$ ls -l $(which sh)
lrwxrwxrwx 1 root root 4 Jun  4  2006 /bin/sh -> bash

```
"sh" is a symbolic link to bash on my Dapper Ubuntu system.  When invoked this way, bash behaves in POSIX mode.  At some later version of Ubuntu, "sh" was changed to a symlink to "dash", which is a more streamlined shell, but apparently not quite as compatible.

I think if you reconfigure dash, you can choose not to make it replace "sh".

---

### Post by nitro_n2o on 2007-09-03
under my feisty it's a symbolic link to dash :)

---

### Post by stlouis1 on 2007-09-06
ya, im running feisty cwald, but from what you're saying, i think thats exactly what i was asking about. so now how would i configure it not to replace SH

---

### Post by chrisccoulson on 2007-09-06
You could modify the top of the Heroes 3 installer script from
```
#!/bin/sh
```

to
```
#!/bin/bash
```

That will cause the script to be executed by BASH instead of DASH.

---

### Post by stlouis1 on 2007-09-06
i had tried that, and ended up getting errors on different lines

---

### Post by pmg on 2007-09-06
Could it be the first script calls other scripts that also have "#!/bin/sh"?  You could try replacing the /bin/sh symlinks and making it point to /bin/bash and see what that does (sudo ln -sf /bin/bash /bin/sh) but I wouldn't leave it that way as some things on the system may depend on /bin/sh being dash.  (Running "sudo ln -sf /bin/dash /bin/sh" will put it back.)

If that doesn't help, post some of the errors and the script lines that go with them.  With that we might be able to see why it's failing.

---

### Post by stlouis1 on 2007-09-07
k, cool. ill give that a try tonight when i get off work. only nice thing about working til 1am is its guiet when i get home

but anyway, ill try tonight, cuz i have SOF and another game i wanted to install too. and so far, aside from this small thing, kubuntu is just working for me, this arch linux is killing me, all i can do is burn cd's on it

---

### Post by chemist109 on 2007-09-08
Issuing:

```
sudo dpkg-reconfigure dash
```

and choosing no will point /bin/sh to /bin/bash and fix your problems.

This has been posted on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/dash/+bug/61463](https://bugs.launchpad.net/ubuntu/+source/dash/+bug/61463)

but the devs have decided that software should break so that Ubuntu can claim POSIX compliance.

---

### Post by stlouis1 on 2007-09-09
well, i tried SOF like that, i hadnt tried it on my arch linux box.....i think my disc is damaged, doesnt seem to work on either, it runs the setup, but cant seem to unpack the archive, theres a big scratch on it....im not pleased, oh well, i have the windows version as well i can take the pak files from, maybe that will work

but bottom line is, the setup runs that way at least. thanks

---

