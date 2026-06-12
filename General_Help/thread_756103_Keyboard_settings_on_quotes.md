---
title: "Keyboard settings on quotes"
date: 2008-04-15
forum: General Help
---

### Post by Sh4wn on 2008-04-15
Hi,

In my old Windows time, I had a keyboard setting which acted like this:

- When I pressed ", it didn't apear yet
- When I press a random character after a ", for example the e, it would become ë.
- This only happens when there's a special character variant of it (like there's no b with dots above it)
- When there's no special variant of it, for example the character b again, it would result in "b

You can replace " with any of these charaters, which often apear above characters: ~ ' ^

 I currently have the keyboard layout US English International alternative, which comes close to this behaviour, but not for full 100%:

- When I press a ", and then a character without any variant of it, it just does nothing, instead of returning "b, it just does nothing. I explicitly have to press space if I want a ".

Is there anyway how I can fix this?

Thanks in advance.

---

### Post by EnsignExpendable on 2008-05-25
I'am experiencing this issue also.  However for me it affects text editing in Eclipse and Emacs.  It also affects typing into this window I´ve just found out.  

When I try to run a perl script I get an unrecognised character \x<ff> marker where <ff> represents the character after the quote, if and only if, I repress the quote symbol. 

I've just found out that pressing space after the first <shift>2 gives the quote I was after but this is a real pain as I have to relearn to touch type when I'm sure it´s just a setting.  I'm assuming this is a configuration issue but can't track it down.  I've changed code pages to no avail (within an application), and been through the preferences and admin menu, but can't track this one down.   Does anyone have any ideas where this setting is ?  

In short I have a work around but not a solution.

---

### Post by EnsignExpendable on 2008-05-26
Solved it,

Went to <system preferences< -> <Keyboard> -> <layouts>
reset to defaults
add layout 'United Kingdom'
variants <default>
removed keyboard layout USA

All seems to be back to normal (for me at least)

---

### Post by lamps06 on 2008-06-03
I have the exact opposite problem:  I seem to be set up for an international keyboard and I cannot turn off the accent functionality.  Whenever I press the ¨ ' ¨ key it does not print an apostrophe but instead waits to see what letter I press next and whether or not it can add an accent.  This is extremely annoying as I never need to add accents to letters.  I went to System -> Preferences -> Keyboard -> Layouts and here is what is listed as default:

Keyboard model:  Generic 105-key (Intl) PC
Layout:  Generic International (with dead keys)

Since I have a Microsoft Internet keyboard I tried changing to:

Keyboard modeal:  Microsoft Internet Keyboard
Layout:  USA

But this did not change anything.  It is extremely frustrating trying to type without quotes or apostrophes.  I can type them but it takes an extra step.  Does anyone know how I can turn off this feature?  Thank you.

---

### Post by mr_niceguy on 2008-06-09
> **lamps06 said:**
> Keyboard model:  Generic 105-key (Intl) PC
Layout:  Generic International (with dead keys)

Since I have a Microsoft Internet keyboard I tried changing to:

Keyboard modeal:  Microsoft Internet Keyboard
Layout:  USA

Just had the same issue. Changed to:

Keyboard model: Generic 105 key (Intl) PC
Layout : USA

Also removed any other layouts.

---

### Post by lamps06 on 2008-06-12
Does anyone know of a bug related to this issue?  I have tried changing my keyboard to the settings listed by Sh4wn, but this does not resolve my issue.  I tried changing to United Kingdom and this seemed to solve the issue...until I restarted.  Then I am back to being stuck with accents and weird quotation marks.  Has anyone else encountered this issue?  Is there a solution that anyone has found?  Thanks.

---

