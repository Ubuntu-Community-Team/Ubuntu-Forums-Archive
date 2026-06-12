---
title: "web pages look terrible in firefox 3 (example: amazon)"
date: 2008-06-17
forum: General Help
---

### Post by os.getlogin on 2008-06-17
Hey all:

I'm noticing a problem with FF3 rendering webpages.  For example, consider amazon.com.  Notice in the attached screenshots that all GIF images look blurry from Amazon.  In particular, the logo "amazon.com" (top left), "carts" (top right), and "your lists" (top right) show the poor display.  In fact any image in FF3 looks bad.

Has anyone else seen this?  Should I tweak a setting?

Nate

---

### Post by sdennie on 2008-06-17
This looks like a font problem.  You may want to look in Edit->Preferences->Content and play with the font settings.  Particularly, I always uncheck the button "Allow web pages to specify their own fonts" under the Advanced button.

---

### Post by os.getlogin on 2008-06-17
> **vor said:**
> This looks like a font problem.  You may want to look in Edit->Preferences->Content and play with the font settings.  Particularly, I always uncheck the button "Allow web pages to specify their own fonts" under the Advanced button.

Yeah, I've tried this.  The fonts don't seem to be the problem.  The text is generally fine (still not as clean though).

---

### Post by sveterv on 2008-06-17
Maybe you are using page zoom? Try ctrl+0 (zero) and check if that helped.

---

### Post by Pjotr123 on 2008-06-17
Check this:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
Numbers 1,2,3,6,7. 

That should do it.  :-)

---

### Post by nittybitty on 2008-08-06
same problem here. gifs render terrible in firefox but look awesome in opera. .pngs render fine in firefox.

---

### Post by tk471 on 2008-08-14
Hello, just did a serch on this topic myself, using Ubuntu 8.04 with Firefox 3.0.1.  Seems when you do ctrl + or -, not only do your fonts change size, but all the graphics do to, and that's when they get messy looking!  Shouldn't just the 'font' change size?

hmm, a Windows site mentions this about Firefox 3:

"Page zoom improvements

In Firefox 2, page zoom only changed the size of text, not graphics, often with horrific results (Figure). Influenced by the dramatically better page zoom feature in IE 7, Mozilla has done the right thing: Now, when you zoom in and out, graphics scale right along with the text. The results, predictably, are excellent (Figure) and virtually indistinguishable from IE 7."

Which perhaps works 'OK' in Windows, but not in Ubuntu? 
[http://www.winsupersite.com/reviews/firefox3.asp](http://www.winsupersite.com/reviews/firefox3.asp)

---

### Post by os.getlogin on 2008-08-14
I would think that the whole page should scale.  Regardless, that wasn't the issue.  After one of the FF updates, the gifs started looking better.  Not sure what it was.

---

### Post by firegun9 on 2008-09-01
I have the same issue. My video card is Nvidia 8800GT.
Interestingly, in Vista, zoom-in pictures look great. (zoom-picture with text)

Is it firefox under vista doing a good job, or firefox under Ubuntu doing a bad job?

---

### Post by sveterv on 2008-09-01
From what I know, it's about X.org scaling algorithm and nothing related to the Firefox 3. New X's resolved this issue, but I don't have any links for you, I read about it few weeks ago somewhere in the net.

---

