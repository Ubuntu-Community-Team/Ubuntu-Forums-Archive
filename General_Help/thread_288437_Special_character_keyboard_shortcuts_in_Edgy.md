---
title: "Special character keyboard shortcuts in Edgy?"
date: 2006-10-29
forum: General Help
---

### Post by jem7v on 2006-10-29
Okay. Um, so, back in the days of yore, when Dapper still ruled the world that is my computer, you could use special characters with <ctrl>+<shift>+<unicode, uh, code> and they'd just pop up.

And then tonight I went to type something in Spanish and, well, the <ctrl>+<shift> thing didn't do anything.

Did the command to do special-character shortcuts Change, or is this a bug? Does anyone know? Is anyone else having this problem?

---

### Post by Anbaric on 2006-10-30
Yeah, I've spotted that, too.  I haven't been able to work out yet whether it's a deliberate feature change or a bug &#8212; I can't find anything on it in the release notes for either Edgy or GNOME 2.16.

---

### Post by MattJ100 on 2006-11-19
Same problem here, on Xubuntu. No solution found yet :/

---

### Post by Anbaric on 2006-11-23
Found it — it's moved to Control-Shift-U.  The comment in the code that handles this (see [http://cvs.gnome.org/viewcvs/gtk%2B/gtk/gtkimcontextsimple.c?view=markup](http://cvs.gnome.org/viewcvs/gtk%2B/gtk/gtkimcontextsimple.c?view=markup)) says:

/* In addition to the table-driven sequences, we allow Unicode hex
 * codes to be entered. The method chosen here is similar to the
 * one recommended in ISO 14755, but not exactly the same, since we
 * don't want to steal 16 valuable key combinations. 
 * 
 * A hex Unicode sequence must be started with Ctrl-Shift-U, followed
 * by a sequence of hex digits entered with Ctrl-Shift still held.
 * Releasing one of the modifiers or pressing space while the modifiers
 * are still held commits the character. It is possible to erase
 * digits using backspace.
 *
 * As an extension to the above, we also allow to start the sequence
 * with Ctrl-Shift-U, then release the modifiers before typing any
 * digits, and enter the digits without modifiers.
 */

---

### Post by Smylers on 2006-11-23
> **jem7v said:**
> Did the command to do special-character shortcuts Change?

Yes, [it changed to [FONT="Courier New"]Ctrl+Shift+U[/FONT] followed by the code]("http://bugzilla.gnome.org/show_bug.cgi?id=341783#c1").

---

### Post by MattJ100 on 2006-11-24
Oh wow! Great find, thanks :D I was struggling without it :)

---

### Post by durand on 2007-01-22
:Dbeen searching for half an hour for this damn change...they should publicise it more!](*,)

---

