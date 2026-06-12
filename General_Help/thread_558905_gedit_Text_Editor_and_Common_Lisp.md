---
title: "gedit Text Editor and Common Lisp?"
date: 2007-09-24
forum: General Help
---

### Post by deadowl on 2007-09-24
Does the gedit text editor have a plugin for common lisp highlighting? I mean, it has pretty much every other programming language I've used. 

C, C++, Java, OCaml, Scheme, as well as a variety of markup and scripting languages I've used.

I'm trying to avoid Emacs at all costs here.

---

### Post by y-lee on 2007-09-27
As far as i can tell no.  I did find this :[Gemini Gedit Plugin ]("http://www.garyharan.com/index.php/2006/11/") but I haven't tried it. 

I've been playing around with common lisp myself and use emacs with slime. it's not as bad as it sounds. lol

Maybe ya could write your own gedit plugin for lisp, or ask somebody in the Ubuntu or gnome community to help ya. I don't have time myself right now tho it is an interesting idea, maybe this winter i'll have more free time then (hopefully)

---

### Post by capink on 2007-09-27
I think scite have support for lisp. Why not try it:

```
sudo apt-get install scite
```

---

### Post by Kadrus on 2008-07-20
Adding a syntax highlighting language to Gedit is easy,all you need to do is know all the keywords to the language.
The files that need to be added if you want to add Lisp are:
in the **/usr/share/gtksourceview-1.0/language-specs/** directory and in the **/usr/share/gtksourceview-2.0/language-specs/** and the **/usr/share/mime/text/**
```
gksudo gedit /usr/share/gtksourceview-1.0/language-specs/lisp.lang
```
and you need to add all the keywords with the appropriate styles,same goes with ```
gksudo gedit /usr/share/gtksourceview-2.0/language-specs/lisp.lang
```
and in the **/usr/share/mime/text/** dir you need to create a file called ```
x-lisp.xml
``` and add all the languages.
Lisp keywords according to GeSHi
[PHP]  'not','defun','princ',

		  'eval','apply','funcall','quote','identity','function',

		  'complement','backquote','lambda','set','setq','setf',

		  'defun','defmacro','gensym','make','symbol','intern',

		  'symbol','name','symbol','value','symbol','plist','get',

		  'getf','putprop','remprop','hash','make','array','aref',

		  'car','cdr','caar','cadr','cdar','cddr','caaar','caadr','cadar',

		  'caddr','cdaar','cdadr','cddar','cdddr','caaaar','caaadr',

		  'caadar','caaddr','cadaar','cadadr','caddar','cadddr',

		  'cdaaar','cdaadr','cdadar','cdaddr','cddaar','cddadr',

		  'cdddar','cddddr','cons','list','append','reverse','last','nth',

		  'nthcdr','member','assoc','subst','sublis','nsubst',

		  'nsublis','remove','length','list','length',

		  'mapc','mapcar','mapl','maplist','mapcan','mapcon','rplaca',

		  'rplacd','nconc','delete','atom','symbolp','numberp',

		  'boundp','null','listp','consp','minusp','zerop','plusp',

		  'evenp','oddp','eq','eql','equal','cond','case','and','or',

		  'let','l','if','prog','prog1','prog2','progn','go','return',

		  'do','dolist','dotimes','catch','throw','error','cerror','break',

		  'continue','errset','baktrace','evalhook','truncate','float',

		  'rem','min','max','abs','sin','cos','tan','expt','exp','sqrt',

		  'random','logand','logior','logxor','lognot','bignums','logeqv',

		  'lognand','lognor','logorc2','logtest','logbitp','logcount',

		  'integer','length','nil'[/PHP]
and this is needed to the highlighting 
```

'(', ')', '{', '}', '[', ']', '!', '%', '^', '&', '/','+','-','*','=','<','>',';','|'

```
Here are a couple of screen shots:

---

