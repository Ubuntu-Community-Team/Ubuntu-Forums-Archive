---
title: "Using akregator as default FireFox 2.0 feed reader."
date: 2006-12-06
forum: General Help
---

### Post by Cronjob on 2006-12-06
Has anyone figured out how to use akregator as the default feed reader for when you click on "subscribe to this feed using" in Firefox 2.0? I know that akregator uses the "-a" switch to indicate the url to subscribe to via the command line, but that doesn't work via Firefox (if nothing else, it automatically inserts a *%20* between the */usr/bin/akregator* and the *-a*.

---

### Post by wadehel on 2007-02-04
Bump

any answer please?

---

### Post by flim on 2007-02-14
Add a shell script containing the following:

#!/bin/bash
/usr/bin/akregator -a $1

I saved it to ~/bin/feed and used that script within firefox. Once saved, don't forget to chmod 755 the file.

Cheers
flim

---

### Post by ym4546 on 2007-06-17
> **flim said:**
> Add a shell script containing the following:

#!/bin/bash
/usr/bin/akregator -a $1

I saved it to ~/bin/feed and used that script within firefox. Once saved, don't forget to chmod 755 the file.

Cheers
flim
That didn't work for me... I chmoded and put the file in the right directory. What am I missing?

---

### Post by Vermyndax on 2007-07-11
It doesn't work if you use akregator integrated into Kontact.  That's a known bug dating all the way back to 1.2.2 of Akregator.

---

### Post by trishacupra on 2007-07-23
Cool, this works for me. As a newb, I had to guess to add the .sh to the end of the file (feed.sh) and that I had to sudo gedit (open the text editor as root) to be able to save the file in usr/bin. And I almost forgot to make the file executable.

I'm so happy it works. Thanks!

---

