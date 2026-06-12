---
title: "Last Chance Saloon - help please!"
date: 2007-01-17
forum: General Help
---

### Post by treb0r on 2007-01-17
Hey All,

I've posted about this twice now with no replies, and I'm coming to the end of my tether.

Basically, after a year or so using Ubuntu successfully, I decided to install it for a non technical friend on his brand new Dell Inspiron 6400 laptop. As a result, I've had nothing but problems and now my friend is no longer my friend, in fact he's accusing me of sabotaging his machine by installing Linux. It all comes down to a simple problem: copy and paste only works intermittently in both evolution and openoffice. I've observed this behavior myself and am at a total loss to explain it. 

I've reinstalled edgy from scratch twice, and applied all the updates to no avail. Could this be a problem with X?

Any ideas gratefully received.

---

### Post by Hagar Delest on 2007-01-17
Can you precise what is the context when it fails pasting ? Is the other app closed ?

See here for example :
- [sharing clipboards between applications]("http://www.oooforum.org/forum/viewtopic.phtml?p=174202#174202")
- [Can't copy to clipboard]("http://www.oooforum.org/forum/viewtopic.phtml?p=4415#4415").

---

### Post by floke on 2007-01-17
I've notices a similar problem when trying to copy and paste from OOo to gmail. Cut and paste works fine though!

---

### Post by treb0r on 2007-01-17
Hello, thanks for the replies...

> **Hagar de l'Est said:**
> Can you precise what is the context when it fails pasting ? Is the other app closed ?

Evolution seems to be the worst culprit - it allows copying using the right click contextual menu, but then paste is not highlighted when one tries to paste to a new window. Occasionally paste is highlighted, but gives no output when clicked. I've also tried pasting into tomboy notes from evolution without success.

My friend is trying to paste data from an email into a calc spreadsheet, and that won't work either....

---

### Post by Hagar Delest on 2007-01-17
Seems to be related to Evolution. Many hits on the web about this issue. In this thread : [ Hoary: Copy/Paste Not Working in Evolution]("http://ubuntuforums.org/showthread.php?t=41994"), someone proposed to use Klipper to fix it. You can try it.

---

### Post by treb0r on 2007-01-17
This is unbelievable - Ubuntu is supposed to be one of the more friendly and advanced distros, and many people are having problems copying and pasting in the default mail app?

How on earth are we supposed to spread the word when such basic features are so buggy?

I guess I'll have to tell him to try Thunderbird or just stick Windows back on.

Thanks for your help...

---

### Post by kbuel on 2007-01-17
try installing and running **glipper**. it captures cut and paste actions from any application, and saves these on its clipboard even if the application closes.

---

### Post by treb0r on 2007-01-17
> **kbuel said:**
> try installing and running **glipper**. it captures cut and paste actions from any application, and saves these on its clipboard even if the application closes.

Thanks dude, I shall give it a try...

---

### Post by treb0r on 2007-01-17
OK, Glipper seems very cool indeed. Now to test it on my (ex)friends system. I missed klipper from my KDE days, and this is a perfect copy...

---

### Post by videodrome on 2007-01-18
The first thing I do with every Ubuntu install is UNINSTALL Evolution!

Install Thunderbird instead.

---

