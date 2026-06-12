---
title: "Having issues with opening .7zip files?"
date: 2013-06-03
forum: General Help
---

### Post by Moose on 2013-06-03
I want to open .7zip files, and I tried to download 7zip using the Ubuntu Software Centre, and it came up with a prompt saying something about it requires restricted files or something (I can't remember exactly as I am not on my home computer right now). And it had two buttons "Okay" and "Repair." And neither one of those buttons did anything.

Someone give me some help here?

Cheers,
Anthony.

---

### Post by searchfgold6789 on 2013-06-03
Anyways, it might be helpful to do things the down-and-dirty terminal way. To use 7zip capabilities, you probably want the p7zip-full package, which file-roller (the main GUI interface that Ubuntu uses for archives) will then use to open 7zip files.
I think this package is included in the ubuntu-restricted-extras (it's a package name which will then automatically install a bunch of other packages) bundle, which could be throwing the Software Center for a loop. What you probably want to do is open up the terminal (ctrl-alt-T) and go:```
sudo apt-get install p7zip-full
``` Type your password, press enter, press enter again when prompted for y/N, and 7zip capabilities will be installed. Or, if it fails, it will provide more information and insight as to why things are failing.
(When it's serious, I use Internet Explorer, too. After all, we all need a good laugh once in a while ;) )

---

### Post by Moose on 2013-06-04
Thank you!

(And I got the idea for the joke from my dad because whenever he is in a hurry to find something on the web, he consults internet explorer, I don't even know why. It's like his emergency browser. >< )

---

