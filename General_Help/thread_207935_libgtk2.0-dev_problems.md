---
title: "libgtk2.0-dev problems"
date: 2006-07-02
forum: General Help
---

### Post by TriggerHappyChewie on 2006-07-02
When trying to install libgtk2.0-dev, I'm running into some errors.

```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
                 Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxfixes-dev but it is not going to be installed
E: Broken packages

```

So, I tried installing libcairo, but I'm getting the same kind of error.

```

The following packages have unmet dependencies:
  libcairo2-dev: Depends: libcairo2 (= 1.0.4-0ubuntu1) but 1.1.10-0ubuntu1 is to be installed
E: Broken packages

```

Any ideas?

---

### Post by Kilz on 2006-07-02
[QUOTE=TriggerHappyChewie]When trying to install libgtk2.0-dev, I'm running into some errors.

```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
                 Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxfixes-dev but it is not going to be installed
E: Broken packages

```

So, I tried installing libcairo, but I'm getting the same kind of error.

```

The following packages have unmet dependencies:
  libcairo2-dev: Depends: libcairo2 (= 1.0.4-0ubuntu1) but 1.1.10-0ubuntu1 is to be installed
E: Broken packages

```

Any ideas?[/QUOTE]

[You may have to activate the universe and multiverse repositories for those packages.]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096")

---

### Post by TriggerHappyChewie on 2006-07-02
Oh my....

I'm an idiot.
I know how to add repos, thanks for the help!

---

### Post by kpkeerthi on 2006-07-02
Even the libtypefree6 **binary** which is required for the latest cairo2 is missing in the repo.
```

libcairo2:
  Depends: libfreetype6 (>=2.2.1) but 2.1.10-1ubuntu2.1 is to be installed

```

```

xxx:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libcairo2
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 437kB of archives. After unpacking 193kB will be used.
The following packages have unmet dependencies:
  libcairo2: Depends: libfreetype6 (>= 2.2.1) but 2.1.10-1ubuntu2.1 is installed.

```

More references of the same problem:
[http://www.ubuntuforums.org/showthread.php?t=207779&highlight=libfreetype6](http://www.ubuntuforums.org/showthread.php?t=207779&highlight=libfreetype6)
[http://www.ubuntuforums.org/showthread.php?t=207810&highlight=libfreetype6](http://www.ubuntuforums.org/showthread.php?t=207810&highlight=libfreetype6)
[http://www.ubuntuforums.org/showthread.php?t=207906](http://www.ubuntuforums.org/showthread.php?t=207906)

---

### Post by TriggerHappyChewie on 2006-07-02
Yea, that didn't work.
Thanks for reminding my to add my repos though!  (Just reformatted)

---

### Post by OlineSixtyOne on 2006-07-04
I need libgtk2.0-dev to compile mplayer from SVN with --enable-gui. Are there any solutions for this?

---

### Post by billyfoxtrot on 2006-07-19
I get a different error:

> libgtk2.0-dev:
  Depends: libgtk2.0-0 (=2.8.17-1ubuntu5) but 2.8.18-0ubuntu2 is to be installed
 Depends: libglib2.0-dev but it is not going to be installed
 Depends: libpango1.0-dev but it is not going to be installed
 Depends: libatk1.0-dev but it is not going to be installed


I'm running the PPC version of Dapper, if that makes a difference.

Anyone know how to fix this issue?

---

### Post by TriggerHappyChewie on 2006-07-19
If you have XGL installed, you need to uninstall it and reinstall libcairo from the repos.  That's how I fixed it.  Dunno if your problem can be solved that way.

---

### Post by Jonix on 2006-08-07
Previously I had XGL/Compiz installed, and now I had the same problem as described above. In Synaptic I managed to downgrade my version of libcairo2 back to 1.0.4 and now I can install libcairo2-dev.

---

### Post by granjerox on 2006-08-10
i have the same problem. i've mannaged to install libcairo2-dev but now I have this problem

```
No se satisfacen las dependencias de los siguientes paquetes:
  libxft-dev: Depende: libxft2 (= 2.1.8.2-0ubuntu2) pero está instalado 2.1.8.2-0ubuntu2patched.
Resolving dependencies...
Las acciones siguientes resolverán estas dependencias

Desactualizar los paquetes siguientes:
libxft2 [2.1.8.2-0ubuntu2patched (now) -> 2.1.8.2-0ubuntu2 (dapper)]

La puntuación es -40

```

I need libgtk2.0-dev for compiling Superkb that needs gdk-pixbuf-2.0. I've readed that it's included in libgtk2.0-dev

---

