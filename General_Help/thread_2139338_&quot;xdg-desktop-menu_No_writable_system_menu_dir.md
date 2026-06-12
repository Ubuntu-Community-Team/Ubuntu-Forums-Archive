---
title: "&quot;xdg-desktop-menu: No writable system menu directory found&quot; (Mathematica install)"
date: 2013-04-26
forum: General Help
---

### Post by chellrose on 2013-04-26
I'm trying to install Mathematica 9.0.1 on my work laptop, running Maverick.  (I know, I know... ](*,))

The result:

```

Enter the installation directory, or press ENTER to select /usr/local/Wolfram/Mathematica/9.0:
> 

Now installing...

[*************************************************************************************************************************]

Type the directory path in which the Wolfram Mathematica script(s) will be created, or press ENTER to select
/usr/local/bin:
> 

Installation failed. See /usr/local/Wolfram/Mathematica/9.0/InstallErrors.

```

The InstallErrors file has one line:
```

xdg-desktop-menu: No writable system menu directory found.

```

I found a whole pile of mostly confusing Google results.  What I've gathered is that this error apparently has *something* to do with the installer trying to install a .desktop file.  But I'm not sure just what the fix is.  Can anyone offer a suggestion?

Thanks :)

---

