---
title: "Incorrect Url Opened In Firefox (feisty)"
date: 2007-04-16
forum: General Help
---

### Post by jvaudrey on 2007-04-16
I'm currently using feisty and if a program opens a URL in this example I'm using Musicbrains picard but this also crops up when reporting a program error via launchpad etc

An example url is below as you can see file:///home/john/%22 is prefixed to the beginning of the line and I cannot seem to fix it

file:///home/john/%22http://musicbrainz.org:80/taglookup.html?tport=8000&artist=Gwen%20Stefani&release=The%20Sweet%20Escape&track=&tracknum=0&duration=0&filename=&puid=%22

Does anyone have any ideas

thanks

John

---

### Post by computerease on 2007-04-16
Have you cleared your cache, off-line content, history in your browser, cookies, etc.  Clean it all out. Close it.  Re-open it and try again.  May not help but can't hurt.  I've seen this in M$ when it sometimes indicates a hijack--not likely here I suspect.  In some ways it looks like a redirect gone awry.

---

### Post by luks on 2007-04-17
> **jvaudrey said:**
> I'm currently using feisty and if a program opens a URL in this example I'm using Musicbrains picard but this also crops up when reporting a program error via launchpad etc

An example url is below as you can see file:///home/john/%22 is prefixed to the beginning of the line and I cannot seem to fix it

file:///home/john/%22http://musicbrainz.org:80/taglookup.html?tport=8000&artist=Gwen%20Stefani&release=The%20Sweet%20Escape&track=&tracknum=0&duration=0&filename=&puid=%22

Does anyone have any ideas
It's a bug in the standard library of Python 2.5. If you are using a custom BROWSER variable, make sure you have no quotes around %s.

---

### Post by jvaudrey on 2007-04-17
Thank you for your help, i went to the prefered applications and changed it to the firefox option in the drop down rather than letting firefox set itself as default and it works fine now

thanks again

John

---

