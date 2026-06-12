---
title: "Ubuntu Collecting Information Without My Consent?"
date: 2012-10-27
forum: General Help
---

### Post by Khufucius on 2012-10-27
In All Settings --> Privacy, on the Diagnostics tab at the top, I see a small paragraph of text:  >  Ubuntu can collect anonymous information that helps developers improve it. All information collected is covered by our privacy policy.  

  That doesn't make any sense to me, and doesn't sound very Linux-y in spirit. I have a few questions about it:    

1. What information is being collected? 

2. When is it being sent?  

3. How can I opt out of this information collection (i.e. turn it off)?  

4. Are there any other times when Ubuntu phones home without my knowledge or consent?   

One of the reasons I use Linux is because it's an OS that doesn't have any privacy leaks to third parties. Ubuntu's main advantage over other distros several years ago -- ease-of-use for newbies and people coming from Windows and Mac OS -- isn't too pronounced anymore. If my Ubuntu installs are automatically phoning home by default, then Ubuntu has now chosen to place itself far behind 99% of the other distros on the privacy front.  What's the deal here?  Can someone clear this up for me?    -K

---

### Post by 3rdalbum on 2012-10-27
> **Khufucius said:**
> 1. What information is being collected?

Tracebacks - this is information of exactly what is occurring in a program.

> 2. When is it being sent?

When a program crashes, and Ubuntu asks you if you want to submit a bug report, and you click Yes.

> <br>3. How can I opt out of this information collection (i.e. turn it off)?

Click "No" instead of "Yes" at the prompt.

> 4. Are there any other times when Ubuntu phones home without my knowledge or consent?

The Shopping lens, Music lens and Video lens send your search queries to Ubuntu servers, but that's kinda what you'd expect them to do. They wouldn't work too well at searching the internet if you didn't allow them to contact the internet.

In Ubuntu 12.10 you can turn off network searching in Unity, or you can uninstall each lens.

The other time Ubuntu contacts its own servers is if you participate in "Popularity Contest", which transmits your package list so Ubuntu can gather statistics about the most well-used software packages worldwide. Easily toggled from the Software Sources settings program. So people don't raise a big fuss over this, I'll just add that Ubuntu ships with Popularity Contest disabled, and it has always had Popularity Contest, and in fact it's something Ubuntu inherited from Debian.

---

### Post by nothingspecial on 2012-10-27
Fixed formatting.

---

### Post by Khufucius on 2012-10-27
Thank you!

Question answered.

-K

---

### Post by claracc on 2012-10-27
> **Khufucius said:**
> Thank you!

Question answered.

-K

Please, mark the thread as solved with "thread tools" in the right upper part of the page.

---

