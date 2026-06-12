---
title: "Firefox crashes on download"
date: 2007-05-28
forum: General Help
---

### Post by Aulden on 2007-05-28
Hi all, 

Got a problem. Whenever I go to download something firefox crashes. (Same for saving of course)

Even when trying to open the download tab or history it crashes. 

Very frustrating... Any ideas?

Thanks,

I'm using Dapper Drake btw.

---

### Post by Lucifiel on 2007-05-28
Does this occur with a certain site or does this occur with all sites? Also, is there any site that's opened in your browser all the time when you're using the internet? 

Perhaps you can try using Swiftfox, Epiphany or Opera.

Swiftfox and Epiphany are Mozilla-based like Firefox. If your Mozilla-based browsers continue crashing, then it is likely that:

a) it could be a script or bad code that's causing your browser to crash. A lot of sites are very heavy on Flash and many load scripts that actually lock up your browser. 

b) it could a browser-related issue. 

If all browsers(including Opera, Konqueror, etc.) continue crashing, then it is likely the problem is likely not with your browsers.

---

### Post by Aulden on 2007-05-30
Thanks for the reply.

I installed Epiphany and it seems to be working fine. 

So it must be something to do directly with firefox. 
Also... it's not with the same sites, but ALWAYS on download or saving. 

Could it have something to do with the folder for downloading being moved or something?

Where are the configuration files for Firefox... maybe I could snoop around there or something?

Thanks again,

---

### Post by genXesis on 2008-06-11
Ya know.  I've had this same exact problem with Firefox ever since they released Firefox 3 RC 1.  

It doesn't matter what site I'm downloading from or anything.  The second the downloaded file completes, Firefox closes immediately with no warning. 

VERY STRANGE :confused:

---

### Post by wersdaluv on 2008-06-12
> **genXesis said:**
> Ya know.  I've had this same exact problem with Firefox ever since they released Firefox 3 RC 1.  

It doesn't matter what site I'm downloading from or anything.  The second the downloaded file completes, Firefox closes immediately with no warning. 

VERY STRANGE :confused:

Same here. I'm using Firefox 3 on Hardy

---

### Post by hossiam on 2008-06-16
Having the same problem.  Has anyone figure it out yet?  I am losing my mind over this.   Love Firefox but I might have to move to another browser for a while.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by lync on 2008-06-17
Same here. After upgrading FF3 Beta5 to RC1 this problem started on Hardy. There is no such problem while using Epiphany or Opera...

---

### Post by dimension128 on 2008-06-18
Well at least I figured out why it was crashing for me. It was an add-on called "Prisim for Firefox" disable that and everything works again.

---

### Post by relic70 on 2008-06-19
> **dimension128 said:**
> Well at least I figured out why it was crashing for me. It was an add-on called "Prisim for Firefox" disable that and everything works again.
Thanks dimension128. That also solved the problem for me. Curious what the reason. I do have Prism as a separate application. Maybe there's a conflict.

---

### Post by CFBauer on 2008-06-25
Disabling Prism fixed the issue for me as well.

edit: Here's a bug report
[https://bugzilla.mozilla.org/show_bug.cgi?id=431546](https://bugzilla.mozilla.org/show_bug.cgi?id=431546)

---

