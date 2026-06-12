---
title: "WYSIWYG Editor for Kubuntu"
date: 2008-06-01
forum: General Help
---

### Post by gvanto on 2008-06-01
I was wondering if there's a good WYSIWYG Html editor which
also incorporates good PHP development, for kubuntu.

I usually use eclipse for development (mostly java right now):
Is there a php add-on for it? Does this perhaps accomodate WYSIWYG capabilities?

Help much appreciated!
Gerry
Linux web-dev newbie

---

### Post by Xiong Chiamiov on 2008-06-01
Bluefish has some WYSIWYG capability (which is why I dropped it), but I don't know about its PHP support.  You should really learn to code things yourself though; it gives you incredible amounts of flexibility.  If you're the kind that likes buying books, I'd recommend "Learning PHP5" from O'Reilly.

---

### Post by Joeb454 on 2008-06-01
You may want to look into BlueFish or Kompozer :)

---

### Post by loell on 2008-06-01
wysiswyg? maybe its just a matter of efficiently switching (back and forth) the browser and the non wysiswyg IDE of your choosing ;)

you know?

**Ctrl + s** then **Alt + TAB** then **f5** then **Alt + TAB**

redo the process again.. :)

---

### Post by Joeb454 on 2008-06-01
So your saying hand code pages? Personally I'd agree, though it's now more of

**:wq** &#8594; **Alt+Tab** &#8594; **F5**

Rinse, repeat

---

### Post by tamoneya on 2008-06-01
I agree with the non-wysiwyg editing since I feel it results in better more efficient code but considering that the OP requested wysiwyg I will second the kompozer recommendation.

---

### Post by loell on 2008-06-01
> **Joeb454 said:**
> 
**:wq** &#8594; **Alt+Tab** &#8594; **F5**

Rinse, repeat

you VI nuts!! :biggrin:

---

### Post by Joeb454 on 2008-06-01
Actually, VIM not VI ;)

And I'm all for hand coding, I find one way to learn is to use a WYSIWYG editor, and look at the code it generates. Then see how you can make it better by changing it and cutting other bits out.

Breaking it and fixing it, it's the best way to learn ;)

---

### Post by tamoneya on 2008-06-01
> **Joeb454 said:**
> Actually, VIM not VI ;)

And I'm all for hand coding, I find one way to learn is to use a WYSIWYG editor, and look at the code it generates. Then see how you can make it better by changing it and cutting other bits out.

Breaking it and fixing it, it's the best way to learn ;)

I think that is a pretty cool way for an intermediate programmer to move up a level but I think beginner programs should really stick with the basics.  They should be using basic text editors or VIM if they are adventurous.  I find that starting with a WYSIWYG will quickly build a dependency.

---

### Post by gvanto on 2008-06-02
hey guys, thanks for the feedback. Basically what I used to do, in Windows (before my eyes were opened to the wonderful world of linux :-) is generate the html forms and css stuff in Dreamweaver, then use a php-syntax highlighting text editor to do the php which does the processing of the form data.

So yeah, the php part is not a problem (and I know its coding quite well), was just wondering if perhaps eclipse (which I enjoy using as a dev. IDE) has a wysiwyg html editor... I'm pretty sure it'll do the php just fine - does it have autocomplete(intellisense) does anyone know? - that would be AWESOME). 

Since if eclipse has such a WYSIWYG editor, it'll just save me installing one and flipping between them while developing. BTW is Dreamweaver available on linux?

Perhaps I'm on the wrong track here altogether with wanting to use eclipse for php?

---

### Post by p_quarles on 2008-06-02
Eclipse was initially designed as Java IDE, with other languages added later. It does not have anything particularly special in the way of html support, as far as I know. 

Since everyone seems to have missed the Kubuntu-specific nature of this question, I'll go ahead and point out the top choice: Quanta+. I think that's what you're looking for, and it's in the repositories. 

Dreamweaver has never been built for Linux, but people have had good results running it in Wine.

---

### Post by gvanto on 2008-06-02
hey p_quarles,

Thanks alot. I just found the quanta package in the package manager - looks good!

Is quanta+ something different?

cheers
G

---

### Post by Xiong Chiamiov on 2008-06-02
Quanta+ and Quanta are the same, just differences in naming.

There is a plugin for Eclipse for PHP development, called eclipse-php or something.  A quick Google for "eclipse php" should find it.  I don't know how well it works though, since Eclipse's interface drives me nuts.

If you ever decide to go completely by hand, it took me a while to find an editor I liked, which I thought was odd, Linux being coder-saturated.  I ended up using Komodo Edit, which has recently become free in speech as well as beer.  It has project support, code folding and remote file editing over FTP, which is quite nifty.

---

