---
title: "What's Wrong With Vim?"
date: 2005-09-30
forum: General Help
---

### Post by polo_step on 2005-09-30
Man, I can't buy a break!

Even freakin' *Vim* doesn't work for me!  Worked once or twice, now doesn't:

Run vim on command line, it opens.  

Start to type.  Two characters (possibly more) don't show.  "INSERT" shows at bottom, then 
characters show and I can enter text.

The various :* commands are dead though.  Won't quit, won't do squat.

WTF is this all about?

I need to use Vim as it's a part of another program.

Yes, I just updated it with Synaptic.

No improvement.

Thanks for any help.

---

### Post by polo_step on 2005-09-30
Narrowing it down a bit more, as soon as I start entering text the problem starts.

I can enter :* directives fine, but as soon as I start writing text, it crashes.  Can't exit, can't invoke :q to get out, nothing.  It's just stuck.

---

### Post by az on 2005-09-30
Dumb question:

Are you familiar with Vim?


Hit "i" as soon as you open a document and you are insert mode.  Hit escape to exit Insert mode and you are back in normal mode.

:q!
:wq

They do not work?

---

### Post by bored2k on 2005-09-30
polo_step, i suggest you use vim for gtk and launch it with the evim command ..

---

### Post by az on 2005-09-30
[QUOTE=polo_step]Narrowing it down a bit more, as soon as I start entering text the problem starts.
I can enter :* directives fine, but as soon as I start writing text, it crashes.  Can't exit, can't invoke :q to get out, nothing.  It's just stuck.[/QUOTE]

Are you doing this from a gnome-terminal in X or from a virtual console?

---

### Post by polo_step on 2005-09-30
[QUOTE=bored2k]polo_step, i suggest you use vim for gtk ...[/QUOTE]
As I said in the first mesage, this is not an option.
Vim is part of (or invoked by) another program, and I'm stuck with it.

---

### Post by polo_step on 2005-09-30
[QUOTE=azz]Are you doing this from a gnome-terminal in X or from a virtual console?[/QUOTE]
Gnome terminal in X.

---

### Post by polo_step on 2005-09-30
[QUOTE=azz]Dumb question:
Are you familiar with Vim?[/quote]
No.
> 
Hit "i" as soon as you open a document and you are insert mode.  Hit escape to exit Insert mode and you are back in normal mode.
:q!
:wq
They do not work?
Let me see.  This may be the solution.

[later...] So "insert mode" is where you have to be to write a file?

It's too early to tell whether this is working properly within the program, but it might be.  We'll know shortly!

---

