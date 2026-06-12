---
title: "emacs options"
date: 2005-06-21
forum: General Help
---

### Post by art on 2005-06-21
Hi folks!
The question is the following.
Whenever I open emacs, I dont have menu bar. I can open it with M-x menu-bar-mode, but after I close emacs session, the next time I open it the menu is gone again, even if I hit the save options button. Another thing is the zoning, I don't want emacs to zone, and again I can turn it off in each section, with M-x zone-leave-me-alone, but the next time it's there again . 
How can I save the options?
Thanks a lot.

---

### Post by Alexander Kirillov on 2005-06-21
[QUOTE=art]Hi folks!
The question is the following.
Whenever I open emacs, I dont have menu bar. I can open it with M-x menu-bar-mode, but after I close emacs session, the next time I open it the menu is gone again, even if I hit the save options button. Another thing is the zoning, I don't want emacs to zone, and again I can turn it off in each section, with M-x zone-leave-me-alone, but the next time it's there again . 
How can I save the options?
Thanks a lot.[/QUOTE]
 What is in your .emacs file?

---

### Post by art on 2005-06-21
This is my .emacs file in attachment.

---

### Post by Alexander Kirillov on 2005-06-22
[QUOTE=art]This is my .emacs file in attachment.[/QUOTE]
 Hmm.. . can't really see where it is set. Anyway: 

for menu bar, try 
menubar->Options->Customize Emacs->Options matching regexp
enter "menu-bar"
this will show you the values of options relevant for menubar, in particular "menu bar mode". If it is "off", toggle it and then do not forget to click on the button "save for future sessions". 

Something simialr should also work for your zone problem, but I am not knowledgeable enoguh here.

---

### Post by gentsquash on 2005-06-22
Let me use [color=olive]CF[/color] to mean "Customization File"; the file where
customizations are stored.  This is either your
[color=brown].emacs[/color] file or the file named in the emacs-var
[color=green]custom-file[/color], if you have set it.

> **art]
Whenever I open emacs, I dont have menu bar. I can open it with
M-x menu-bar-mode, but after I close emacs session, the next time
I open it the menu is gone again, even if I hit the save options
button. 
[/QUOTE]

Executing, in Emacs, the form
```
(customize-save-variable 'menu-bar-mode t "22Jun2005: AK set this")
```
will alter your CF, and will also set [color=green]menu-bar-mode[/color]
for the current session.  The [color=green]customize-save-variable[/color]
corresponds to "Save for Future Sessions" choice in a
Customization buffer.

Instead of Custom, you could put
```
(when (fboundp 'menu-bar-mode)
  (menu-bar-mode (if window-system 1 -1))  said:**
> .emacs[/color]; to handle the case when you invoked [COLOR=Green]emacs -nw[/COLOR].
[Note that here you are using the *FUNCTION* [color=green]menu-bar-mode[/color], not the variable].


[QUOTE=art]
Another thing is the zoning, I don't want emacs to zone,
and again I can turn it off in each section, with M-x
zone-leave-me-alone, but the next time it's there again .


On my system, [color=brown]zone.el[/color] is not controlled by Custom; so what is
loading this package?  Is it being loaded by the sysadmin in some
site-wide emacs file?

There are various ways to turn it off, but why is it being loaded
in the first place?    The emacs-var [color=green]features[/color] should show "zone",
if the pkg is loaded.  Its position in the list printed by
```

(prog1 "Eval this in *scratch*" (cl-prettyprint (reverse features)))
```

[or use [COLOR=Green](prog1 "Eval this in *scratch*" (pp (reverse features)))[/COLOR]
if you don't use the cl packages]
will show you *when* it was loaded and give you a hint as to _WHO_
loaded it.

---

### Post by art on 2005-06-24
Well thanks a lot guys!
The the menu bar is there now! Emacs runs on my computer locally, so no sysadmins are involved...

---

### Post by EsbenHaabendal on 2007-10-29
Looks like zone.el is getting pulled in by emacs-extra if you select the "Disable tool bar" option (sudo dpkg-reconfigure emacs-extra)

When selecting "Disable tool bar" the following change is made to
/usr/share/emacs/site-lisp/emacs-extra/emacs-extra.el /tmp/emacs-extra.el

```
@@ -213,6 +213,12 @@
 (global-set-key [C-mouse-5] 'up-a-lot)
 (menu-bar-mode nil)
 (set-scroll-bar-mode nil)
+(when (>= emacs-major-version 21)
+  (tool-bar-mode -1)
+  (blink-cursor-mode nil)
+  (require 'zone)
+  (setq zone-idle 300)
+  (zone-when-idle 300))
 (load "/usr/share/emacs-extra/misc/reindent.el")
 (load "/usr/share/emacs-extra/misc/std_comment.el")
```

I wonder if this is considered a feature or a bug...

---

