---
title: "[SOLVED] Uninstall tf-tool compiled"
date: 2008-05-22
forum: General Help
---

### Post by aliencam on 2008-05-22
I couldn't get tf-tool to work (this was about a month ago) so I compiled it from source and installed.  I first installed the 2.3 from source, then the 3.0.  Now I find out that the one in the repos works just fine, and I want to remove the ones I installed by compiling. 

I have tried to install tf-tool by synaptic and apt-get, but when i remove it through synaptic or apt-get (even with --purge) the program still runs if i type tf-tool into the terminal.  

I tried building a .deb with make and checkinstall, but that deb that I made cannot be installed because it can't overwrite files that are already there.  

would it be safe for me to just delete all the files that it shows in the "included files" tab of my deb install file?

---

### Post by latna on 2008-05-22
I'm not quite following this so maybe you could clarify some things.

> **aliencam said:**
> I couldn't get tf-tool to work (this was about a month ago) so I compiled it from source and installed.  I first installed the 2.3 from source, then the 3.0.  Now I find out that the one in the repos works just fine, and I want to remove the ones I installed by compiling. 

So now you have 2 of them installed? You installed 1 from source and the other from the repos? When you installed version 3.0 it prolly overwrote the previous version. That's not guaranteed though. That's why I don't install from source. Package management is messy.

You might be able to uninstall it by going into the source directory and typing:

```
make uninstall
```

> I have tried to install tf-tool by synaptic and apt-get, but when i remove it through synaptic or apt-get (even with --purge) the program still runs if i type tf-tool into the terminal.  

Is this because you still have the "compiled from source version" still installed? Try this:

```
which tf-tool
```

If it says /usr/local in the path, that's the copy that you installed from source.

> I tried building a .deb with make and checkinstall, but that deb that I made cannot be installed because it can't overwrite files that are already there.  

Did you use checkinstall from the start? If so you should be able to remove it with:

```
dpkg -r tf-tool
```

assuming tf-tool is the actual name of the package.

> would it be safe for me to just delete all the files that it shows in the "included files" tab of my deb install file?

I would say it's safe if you installed it in /usr/local. If not I would check to make sure each file doesn't belong to another package.

```
dpkg -S /path/to/filename
```

Use the full pathname to the file like /usr/bin/firefox

---

### Post by aliencam on 2008-05-23
thank you, 

the only one currently installed is the one installed from source, and i'm trying to remove that one.  It is installed in /usr/local/sbin/tf-tool,  so I will remove that directory.  

make uninstall does not work, I deleted the original installation directory a long time ago, and so all I have to make uninstall in is a new copy of what I downloaded.  


thanks again, I hope this works.

---

### Post by aliencam on 2008-05-23
everything worked great once i deleted that, thank you very much.

---

