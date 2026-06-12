---
title: "Uninstalling Kiba dock"
date: 2008-05-21
forum: General Help
---

### Post by azizzle on 2008-05-21
How would I uninstall kiba-dock? I installed using this method: [http://tomateotra.wordpress.com/2007/02/04/howto-desktlets-en-ubuntu-kibadock-gdesklets-y-cairoclock/](http://tomateotra.wordpress.com/2007/02/04/howto-desktlets-en-ubuntu-kibadock-gdesklets-y-cairoclock/)


Thanks

---

### Post by EXCiD3 on 2008-05-22
Try searching Synaptic for kiba-dock, you might be able to install it from there.

If that doesnt work, open terminal and change directories to where you extracted kiba-dock to and run ```
sudo make uninstall
```

---

### Post by bob_hilton on 2008-06-22
I've just tried this method and it dosen't work for me. There's no kiba dock in synaptic and the command gives me ;

> usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...


i then tried putting 'sudo make uninstall' into the terminal;

> make: *** No rule to make target `uninstall'. Stop.


what am i missing?

---

### Post by EXCiD3 on 2008-06-22
> **bob_hilton said:**
> I've just tried this method and it dosen't work for me. There's no kiba dock in synaptic and the command gives me ;



i then tried putting 'sudo make uninstall' into the terminal;



what am i missing?

Heres a link how to uninstall it, seeing that its a bit more complicated then just the generic uninstall method from the source folder because there are multiple packages that it installs. [http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)
or this link has removal instructions also: [http://ubuntuforums.org/showthread.php?t=726155](http://ubuntuforums.org/showthread.php?t=726155) Last 2 posts are what you are looking for. :)

---

