---
title: "I cant't see flash or video in the browsers."
date: 2013-06-05
forum: General Help
---

### Post by lampadron on 2013-06-05
Hi everyone!  
 I'm using lubuntu 12.04 and I have a problem with my browsers. I can't see flash on the web pages. 
It's look like that flash player has been installed correctly. 
My computer is quite old, may this be problem for running the flash player?
 p.s.
Sorry for my english.

---

### Post by vadimkolchev on 2013-06-05
Hi and welcome.
How do you know that flash player is installed correctly?
Run mozilla and in the address bar type ```
 about:plugins
```
Does it show flashplugin installed? What version if positive?

---

### Post by greatsirkain on 2013-06-05
open synaptic and search for flash and install it (if it has a green box next to it it's already installed).
Your computer being old shouldn't be a problem, one of my computers was made in 2005 and runs flash fine with the onbord graphics

---

### Post by Charlotte18 on 2013-06-05
> **lampadron said:**
> Hi everyone!  
 I'm using lubuntu 12.04 and I have a problem with my browsers. I can't see flash on the web pages. 
It's look like that flash player has been installed correctly. 
My computer is quite old, may this be problem for running the flash player?
 p.s.
Sorry for my english.
The age of your computer is not an issue.

I recently installed lubuntu 13.04, and I had to apply a "workaround" to get flash working because it would not work with the version from the ubuntu repositories. 

I had to  purge the flash installation that came from the repositories.

After that, I went to adobe's archive site and downloaded the zip archive for the older flash 10.3. I had to unzip the archive and open the folder. Then, I had to unzip the tar.gz "linux" archive. In that folder, there's a file called libflashplayer.so. I had to copy that file into the appropriate folders for my web browsers (/usr/lib/chromium-browser/plugins and /usr/lib/firefox/browser/plugins).

After all that, flash was working.

[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

---

### Post by lampadron on 2013-06-08
> **vadimkolchev said:**
> Hi and welcome.
How do you know that flash player is installed correctly?
Run mozilla and in the address bar type ```
 about:plugins
```
Does it show flashplugin installed? What version if positive?

Thanks for you reply vadim :D, however the shockwave flash has been installed. Its versione is 11,2,202,285.[h=2][/h]

---

### Post by lampadron on 2013-06-08
Thank you all for replies, I've found the problem. I've removed the correct plugin, and instaled another one. Now flash works!

---

