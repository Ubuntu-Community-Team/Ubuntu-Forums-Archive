---
title: "Keyboard - Quotation Marks not working?"
date: 2007-01-04
forum: General Help
---

### Post by Ninkul on 2007-01-04
Well, ive found that a few buttons on my keyboard arent working such as quote marks and af ew others i have to press the button twice before it puts anything on the screen and ¨ isn´t the same as the usual one when pressed on other OS´s.

Ive tried setting the keyboard to all the different english ones and i believe its a US keyboard.

The other keys would be a couple of the ones up the top (shift+number).

Does anyone know a solution to get them working? :S

---

### Post by bapoumba on 2007-01-04
Hello,

that may not be _exactly_ the answer you are looking for. But if you have tried all kind of keyboard layouts, you may want to give a shot to the "compose key" (Layout Options tab in > System > Prefs > Keyboard) and look what characters you can get with AltGr key.
Having an azerty laptop, I choose the PC105 intl layout, and some characters were not easy to find :
" ; “ ; ” ; ' ; ` ; « ; »

---

### Post by mvanzante on 2007-01-16
I have had this same issue and have tried multiple layouts. I have to try some more as well as the compose key. Seems odd that a standard US 108-key QWERTY layout isn't supported well.

---

### Post by srai on 2007-02-04
I am having the same problem with the quotation marks key on an AMD64 machine using Kubuntu desktop environment. You have to press twice to get a quotation character which is not the same as I have discovered while trying to insert a varchar with quotes in MySQL ... it fails.

Anyone have ideas how to fix this?

Thanks.

---

### Post by ivanbev on 2007-02-16
Having tried numerous other things, I fixed this by using a keyboard layout setting without "dead keys"; in my case this was "united kingdom" rather than "united kingdom international (with dead keys)".

In Gnome (Ubuntu menus):
 System -> Preferences -> Keyboards
  Layout (tab) -> Add (button)

Then make this the default layout. For info, I am using "generic 105-key (intl) PC" keyboard model.

- Ivan

---

### Post by boyhowdy on 2007-06-09
The ¨ symbol you're seeing is called a diaeresis (or umlaut for German, I believe).  The international keyboard layouts apparently use the quote key as a switch for adding letters modified with the diaeresis and other special characters.  I couldn't find a way to turn that switch off, so I switched my keyboard layout to U.S. English > Macintosh (the United Kingdom > Macintosh layout appears to be identical, btw).  I haven't run into any problems with it yet, even though I'm using a Microsoft OEM keyboard, but I'll update if I run into anything.  Hope this helps.

Update:

I just got what ivanbev was saying.  Selecting "U.S. English" rather than one of the variants under it gets rid of the problem.  Pretty unintuitive if you ask me.  It looks like U.S. English is a group/menu rather than an option.  Thanks, ivanbev.

---

