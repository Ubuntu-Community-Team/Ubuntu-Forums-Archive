---
title: "[SOLVED] Bluefish editor question"
date: 2007-11-04
forum: General Help
---

### Post by geovino on 2007-11-04
I just installed Gutsy and I was using Bluefish in Feisty. I have forgotten to save  the command to add so I can preview Firefox with the preview button. Does anyone know what it is?

---

### Post by Maestro23 on 2007-11-04
> **geovino said:**
> I just installed Gutsy and I was using Bluefish in Feisty. I have forgotten to save  the command to add so I can preview Firefox with the preview button. Does anyone know what it is?

Section 8.1 of the manual: Customizing Browsers
[http://bluefish.openoffice.nl/manual/ch07s08.html](http://bluefish.openoffice.nl/manual/ch07s08.html)

---

### Post by geovino on 2007-11-04
Thanks, but I'm trying to find what the right command for firefox. I got the preview button to open firefox, but its not opening firefox in the html page I'm working on. 

Here's the command I'm using now that opens firefox,but not opening the preview of the page I'm working on:

firefox -x %s&

What needs to change?

---

### Post by geovino on 2007-11-05
After a little trail and error I found the correct command to open the page you're working on. 

This is it:

firefox -remote 'openURL(%s, new-window)' || firefox %s&

Problem Solved!

---

### Post by Maestro23 on 2007-11-05
> **geovino said:**
> After a little trail and error I found the correct command to open the page you're working on. 

This is it:

firefox -remote 'openURL(%s, new-window)' || firefox %s&

Problem Solved!

Good deal man.  Don't forget to mark this SOLVED using the Thread Tools.

Thanks.:)

---

