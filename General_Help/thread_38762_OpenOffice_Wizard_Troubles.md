---
title: "OpenOffice Wizard Troubles"
date: 2005-06-01
forum: General Help
---

### Post by m0biu5 on 2005-06-01
I am quite new (few days now) to Ubuntu/Linux in general, and I came across this. My gurufriend said that I should post it up here, so here goes. Anyone ever seen this before?

---

### Post by jonrkc on 2005-06-02
I'm afraid I don't understand what the problem is supposed to be.  That's the normal dialog box for building a presentation in OpenOffice.org.  You start from there and set up your slides and whatever effects you want, etc.

---

### Post by mglukhovsky on 2005-06-03
The problem is that the window isn't adjusting for the font size. See how the combo box and frames overlap the text? While this is purely cosmetic, it's a valid concern.

My Ubuntu laptop is coming back Tuesday, so I'll take a look then to see if I have a similar problem.

---

### Post by jonrkc on 2005-06-03
[QUOTE=mglukhovsky]The problem is that the window isn't adjusting for the font size. See how the combo box and frames overlap the text? While this is purely cosmetic, it's a valid concern.

My Ubuntu laptop is coming back Tuesday, so I'll take a look then to see if I have a similar problem.[/QUOTE]
 I agree wholeheartedly that I fret about such things too; cosmetics matter a lot when you use a computer several hours a day.  (That's one reason there are so many window managers.)

But I'm afraid I still don't see what's wrong.  My Auto-Pilot dialog corresponding to yours looks exactly the same.  I think that's the way the OOo folks have it set up.  I'm not trying to be difficult, but I honestly don't see anything wrong with it.  I'm more than willing to be shown the light, though!
:)

Edit:  Something just occurred to me.  Have you looked at the box in question, and at your screenshot, on ANOTHER COMPUTER?  It just could be a problem with the way your display is set up, or, just as likely, the way OOo, an enormously complex program, interacts with your particular display.  That would certainly account for your seeing what I don't see.

---

### Post by m0biu5 on 2005-06-03
Okay, here it is with lovely mouse drawn red circles for your viewing pleasure. :grin:

---

### Post by jonrkc on 2005-06-03
[QUOTE=m0biu5]Okay, here it is with lovely mouse drawn red circles for your viewing pleasure. :grin:[/QUOTE]
 OK, thanks.  I see what you mean.  Here is a screen shot of the same dialog box on my OpenOffice.org setup: [www.jonrkc.com/my_images/Wizards.jpg](www.jonrkc.com/my_images/Wizards.jpg).  It looks to me as though you have a Gnome-enabled version (to judge from the shape of the buttons, etc.) and that may be why it's not looking quite right.  I had a terrible time with the Gnome-enabled Firefox and got rid of it and got the regular version from Mozilla.org and it works and looks fine.  

I'd just about be willing to bet that's the problem.

By the way, my version of OpenOffice.org is 1.1.3.

---

### Post by mglukhovsky on 2005-06-04
Mobius, is your version of OpenOffice 1.1x or is it the 2.0 beta?

---

### Post by m0biu5 on 2005-06-04
[QUOTE=mglukhovsky]Mobius, is your version of OpenOffice 1.1x or is it the 2.0 beta?[/QUOTE]
 1.1.3 - packaged with Ubuntu 5.04

---

### Post by GTKpower on 2005-06-05
I'm running OO 2.0, but my box looks different, and it seems to look fine.

Here's an odd sggestion:  When your box looks incorrect, quickly drag it down to well past the bottom of your desktop (all the way), and then back up again.  Have some of the offending lines disappeared?

---

### Post by jonrkc on 2005-06-05
How about Lethargic Lemming?

---

### Post by m0biu5 on 2005-06-05
[QUOTE=GTKpower]I'm running OO 2.0, but my box looks different, and it seems to look fine.

Here's an odd sggestion:  When your box looks incorrect, quickly drag it down to well past the bottom of your desktop (all the way), and then back up again.  Have some of the offending lines disappeared?[/QUOTE]
 Not odd at all. Used that trick many times to force a repaint when I was writing my Java GUIs. Didn't work though...

What is Lethargic Lemming?

---

### Post by jonrkc on 2005-06-05
[QUOTE=m0biu5]Not odd at all. Used that trick many times to force a repaint when I was writing my Java GUIs. Didn't work though...

What is Lethargic Lemming?[/QUOTE]
 Oh, I was only adding to GTKpower's list of suggested Ubuntu release names with the lemming one.  "Muddled Mongoose" would be good, too.

Re: your dialog box, I still feel strongly it's a Gnome issue--because of the shape of the widgets.  I think it would be worth renaming your existing OOo directory temporarily, and installing OOo from their website, which only takes a couple of minutes (very nice installer) though you do have to follow some specific instructions, namely root goes into /whatever-the-path/OpenOffice.org1.1.3/program directory and runs "./setup net" first, then the normal user enters that same directory and runs simply "./setup."

It may sound like more trouble than it's worth, but I believe it's the one surefire way to diagnose the problem.  That's how I had to fix Firefox, after the "save file" dialog box was hijacked by Gnome into a completely worthless form.  Getting the program from the Mozilla.org website gave me back the standard stuff I was used to and wanted.

---

### Post by m0biu5 on 2005-06-05
Hmm okay. I will give that a shot later this weekend.

GTK's list of names is in his signature btw. :smile:

---

