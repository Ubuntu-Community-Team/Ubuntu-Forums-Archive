---
title: "controling firefox from terminal?"
date: 2013-04-09
forum: General Help
---

### Post by goof on 2013-04-09
hi iwas wondering iif there was a way to open a url in firefox copy its contents and paste it into text doc? all from the terminal or bash

---

### Post by stinkeye on 2013-04-09
> **goof said:**
> hi iwas wondering iif there was a way to open a url in firefox copy its contents and paste it into text doc? all from the terminal or bash
Why is it necessary to open the url in firefox?
Can't you just use wget or curl.
eg
```
curl --retry 4 "http://www.some-webpage" > some-webpage.txt
```

...and if it's just the text your after you can remove the html code using sed...
```
curl --retry 4 "http://www.some-webpage" | **sed -e :a -e 's/<[^>]*>//g;/</N;//ba'** > some-webpage.txt
```

---

### Post by papibe on 2013-04-09
Hi goof.

Take a look at the command **wget**.

Hope it helps.
Regards.

---

### Post by goof on 2013-04-10
i have tryed both of these and alot of text browsers the problem is it doesint grab inbeded code from javascript for example it only gets parts of the page i nedd everything as if copied and pasted from browser there must be a clipbord addon wtih auto save or something

---

### Post by markbl on 2013-04-11
Perhaps [Selenium](http://docs.seleniumhq.org/) is what you are looking for?

---

### Post by Habitual on 2013-04-11
> **goof said:**
> i have tryed both of these and alot of text browsers the problem is it doesint grab inbeded code from javascript for example it only gets parts of the page i nedd everything as if copied and pasted from browser there must be a clipbord addon wtih auto save or something[http://add0n.com/quickfox.html](http://add0n.com/quickfox.html)

---

### Post by goof on 2013-04-13
thasnk there great tools but selinium doesint recodnise quickfox if i open a page select all copy and pste to quickfox in threplay it just opens the page any suggestions how i could automate copy and pasteing to what should be a txt file in the end? thanks

---

### Post by goof on 2013-04-13
sorry forgot to mention the best tool i found was "texttofile" this allws you to right click and save highlighted text to file it even allows you to append another file but imacros and sellenium dont record it is there any tool out there that will? thanks

---

### Post by schragge on 2013-04-13
If you could point us to a web page in question, I'm sure somebody would suggest a solution be it [perl](http://search.cpan.org/~claesjac/JavaScript-1.16/lib/JavaScript.pm), edbrowse, Selenium, or something else.

---

### Post by goof on 2013-04-14
any sock list site i dont know python but have te feelin im gona have to learn :( its a pain somethin as simple as copy and paste is so difficult

---

