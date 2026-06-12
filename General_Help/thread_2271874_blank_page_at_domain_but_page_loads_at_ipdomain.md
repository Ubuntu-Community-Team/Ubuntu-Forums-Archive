---
title: "blank page at domain but page loads at ip/domain"
date: 2015-04-02
forum: General Help
---

### Post by astarmathsandphysics on 2015-04-02
I am trying to save £100 a month by home hosting.
I have updated dns and configured files at /etc/apache2/sites/available/ 
I have enabled the websites
When I load the studentforums.biz I get a blank page, but the website loads at ip/stidentforums/

I am probably missing something very simple, but what?

---

### Post by dino99 on 2015-04-02
maybe its what you are loking for: [http://stackoverflow.com/questions/8755229/how-to-download-all-files-but-no-html-from-a-website-using-wget](http://stackoverflow.com/questions/8755229/how-to-download-all-files-but-no-html-from-a-website-using-wget)
httrack can also be usefull, install it from ubuntu archive  [http://ubuntuforums.org/showthread.php?t=1253784](http://ubuntuforums.org/showthread.php?t=1253784)

---

### Post by nerdtron on 2015-04-02
Probably the DNS has not propagated yet. 

Your page studentforums.biz loads on my browser.

---

### Post by astarmathsandphysics on 2015-04-02
Resinstalled apache2 and wortks nnow

---

