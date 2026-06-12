---
title: "Installed ies4linux and installed just ie6"
date: 2007-07-14
forum: General Help
---

### Post by sjpritch25 on 2007-07-14
However, i can't use the address bar.   For some reason there is the letter **h**, and nothing else in the address bar.   When i type in **[http://www.google.com](http://www.google.com)**, i get page cannot be displayed.   Not sure why??  I can click on links fine, but can't seem to type anything in the address bar.   Any help would be wonderful.   Thanks.

Here is a screenshot.

[http://www.castlecops.com/zx/sjpritch25/Screenshot-20.png](http://www.castlecops.com/zx/sjpritch25/Screenshot-20.png)

[http://www.castlecops.com/zx/sjpritch25/Screenshot-21.png](http://www.castlecops.com/zx/sjpritch25/Screenshot-21.png)

[http://www.castlecops.com/zx/sjpritch25/Screenshot-22.png](http://www.castlecops.com/zx/sjpritch25/Screenshot-22.png)

---

### Post by obadiah on 2007-07-16
I too experienced this same problem. I'm not sure what's going on but I found a solution that is working for me by installing an older version of wine. Here's what I did.

1. Remove current 0.9.41 version of wine
2. Download 0.9.38 version of wine [here]("http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.38~winehq0~ubuntu~7.04-1_i386.deb") 
3. Open the downloaded version of wine with GDebi Package Installer
4. Ignoring suggestions to use newer versions of the package, I installed Wine 0.9.38 

After doing the above, I was able to start up IE 6.0 and it worked perfectly. Hope this helps someone.

---

### Post by Damiel on 2007-07-17
Same problem here. Guess 0.9.41 is bugged. As obadiah, my solution was to downgrade.

---

### Post by sjpritch25 on 2007-07-17
Thanks

---

### Post by st|kkz on 2007-07-29
This fix did not work for me.  I installed the older version of wine, and removed/re-installed ies4linux.  Same problem.  Any other suggestions?

---

### Post by Damiel on 2007-07-31
Which wine version are you using? Mine is v0.9.40 and IE6 is working fine. Got it from [here]("http://wine.budgetdedicated.com/archive/ubuntu/feisty/").

Also there is a workaround at the [bug report @ winehq]("http://bugs.winehq.org/show_bug.cgi?id=8974")

---

### Post by st|kkz on 2007-07-31
Maybe I have 2 issues.  I am getting zero web page results.  My network works fine, but ies4linux does not find any web sites.  I also have the "h in the address bar" issue.  Apparently these are 2 separate problems.  I care more about not getting any web pages.  

I just upgraded my wine to v0.9.42 yesterday.

---

### Post by Damiel on 2007-07-31
Try downgrading to v0.9.40 or below. I can confirm that v0.9.42 also has the address bar bug, as I tried it today.

---

### Post by st|kkz on 2007-07-31
That did it!  *.40, baby.  Thanks!

---

### Post by figgles on 2007-07-31
I basically followed this recipe, but used 0.9.40 not 9.38 works great! thanks!

---

### Post by Unicast on 2007-08-04
Thanks guys, I had exactly the same "h" in address bar issue as the OP.

Works like a charm with wine 0.9.40

These forums are a life saver!

---

### Post by David Floyd on 2007-08-11
0.9.43 is now out and has solved the problem of the 'h' in the address bar, but still no ActiveX.

Anyone got ActiveX to work?

David

---

