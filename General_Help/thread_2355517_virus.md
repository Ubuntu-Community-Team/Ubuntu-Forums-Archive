---
title: "virus"
date: 2017-03-13
forum: General Help
---

### Post by pete1977x on 2017-03-13
has anyone had a thing where your desktop icon fonts change on their own after you reboot??

---

### Post by HermanAB on 2017-03-13
In my experience, funny things like that are usually an indication of a failing HDD, where the file system is slowly rotting.

---

### Post by RobGoss on 2017-03-13
Is this a new installation? did you make any changes to your system recently

---

### Post by ajgreeny on 2017-03-13
Rest assured that it will not be a virus; there are no Linux viruses in the wild.
Have you installed the kde system-settings package and used that to alter fonts in any kde applications that you may have on your xfce desktop?

Doing so can completely mess up font rendering in other applications as a result of creating a file **~/.config/fontconfig/fonts.conf** which can cause rendering to become thin and spidery.  Remove that file for proper gtk rendering again.

I have been caught out by this s few times in the past and spent a long time trying to figure out what was going on; I do not remember how I discovered the solution, but it always worked for me.  You can use the kde system-settings application without causing this as long as you don't make any changes in the fonts section.

---

