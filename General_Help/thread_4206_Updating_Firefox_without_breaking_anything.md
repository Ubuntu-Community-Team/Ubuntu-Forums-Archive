---
title: "Updating Firefox without breaking anything"
date: 2004-11-12
forum: General Help
---

### Post by mdweezer on 2004-11-12
I would like to update Firefox to the new 1.0 release.  I'm currently using the 0.9.3 release that came with the Ubuntu install.

Can I safely download the install and run it without breaking any links or any of the stuff to I did to make it work with java and such?

Thanks!

---

### Post by adbak on 2004-11-12
I think you may have to uninstall FFx 0.9.3 first, but don't quote me on that.

And make sure you back up your plugins directory and your bookmarks.

---

### Post by DyDx on 2004-11-13
I just installed Firefox 1.0 to whatever directory and made a symlink to /usr/bin/firefox... works a charm.

You _can_ uninstall Firefox 0.9.3, but then you also have to remove "ubuntu-desktop," which I didn't want to mess with -- I've heard since then that "removing" that doesn't actually break anything, but I have yet to try.

---

### Post by ubik on 2004-11-13
I just confirm that removing ubuntu-desktop and firefox-0.9.3 doesn't break anything, the only problem i found is that during updates, the system reinstall ubuntu-desktop and firefox with it. But that's not a problem since firefox 0.9.3 and 1.0 can work together if they're not installed in the same dir (i put 1.0 in /opt/firefox) and if the symlinks in /usr/bin aren't the same...

---

### Post by HiddenWolf on 2004-11-13
1.0 should be in the hoary repostries very soon by the way.

---

### Post by Artiom on 2004-11-13
[QUOTE=DyDx]I just installed Firefox 1.0 to whatever directory and made a symlink to /usr/bin/firefox... works a charm.

You _can_ uninstall Firefox 0.9.3, but then you also have to remove "ubuntu-desktop," which I didn't want to mess with -- I've heard since then that "removing" that doesn't actually break anything, but I have yet to try.[/QUOTE]

did the same and it worked. 
 \\:D/

---

### Post by triad169 on 2004-11-13
The only problem I have by doing the symlink trick is that when I click on a link in a email message (in Evolution) firefox wont open.  

Triad

---

### Post by HungSquirrel on 2004-11-13
[QUOTE=triad169]The only problem I have by doing the symlink trick is that when I click on a link in a email message (in Evolution) firefox wont open.  

Triad[/QUOTE]
 Computer -> Desktop Preferences -> Preferred Applications

In the Web Browser tab, select Custom Web Browser.  In the Command field, enter *firefox %s*.

---

### Post by HiddenWolf on 2004-11-13
[QOUTE]In the Web Browser tab, select Custom Web Browser.  In the Command field, enter *firefox %s*.[/QUOTE]

actually, that should be 'mozilla-firefox %s'  right?

---

### Post by HungSquirrel on 2004-11-13
Not if he is doing the symlink trick that another user described.

> I just installed Firefox 1.0 to whatever directory and made a symlink to /usr/bin/firefox... works a charm.

However if he made his symlink at /usr/bin/mozilla-firefox , that would work.

---

### Post by scoon on 2004-11-15
Hey there, 

The way I am using warty and firefox 1.0 was to create a trivial (local) repository.  I followed this link 

[http://www.debian.org/doc/manuals/repository-howto/repository-howto.html](http://www.debian.org/doc/manuals/repository-howto/repository-howto.html) 

and then found the debs on an debian.org search. The nice thing with doing this is that I do NOT have to uninstall ubuntu-desktop.  So everything else is just as it should be.  Nice and stable. 

scoon

---

### Post by Telep on 2004-11-17
[QUOTE=scoon]Hey there, 

The way I am using warty and firefox 1.0 was to create a trivial (local) repository.  I followed this link 
and then found the debs on an debian.org search. The nice thing with doing this is that I do NOT have to uninstall ubuntu-desktop.  So everything else is just as it should be.  Nice and stable. 
scoon[/QUOTE]

That worked fine, thanks for the tip. In addition to the firefox deb I also needed to download the latest libpng12 from the debian site.

---

### Post by ynef on 2004-11-18
Is that the latest libpng?

[USN-1-1: PNG library vulnerabilities](http://www.ubuntulinux.org/support/documentation/usn/usn-1-1)

---

### Post by Telep on 2004-11-18
[QUOTE=ynef]Is that the latest libpng?

[USN-1-1: PNG library vulnerabilities](http://www.ubuntulinux.org/support/documentation/usn/usn-1-1)[/QUOTE]

No, the latest libpng is not available through warty, you'll need to download it (here: [http://packages.debian.org/unstable/libs/libpng12-0](http://packages.debian.org/unstable/libs/libpng12-0)) and install it the same way as Firefox. I hope it didn't brake anything, though :)

---

