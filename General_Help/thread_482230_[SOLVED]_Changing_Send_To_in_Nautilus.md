---
title: "[SOLVED] Changing Send To in Nautilus"
date: 2007-06-23
forum: General Help
---

### Post by bob-linux-user on 2007-06-23
I use Mozilla Thunderbird for email. The computer also has Evolution installed but I have never used it or set it up. When I right click on a file in Nautilus and follow "Send to" I get the (useless to me) option to send as "Email(Evolution)".

How can I change this to an option to send the file as an attachment using Thunderbird please?

Regards to all

Bob

---

### Post by reclusivemonkey on 2007-06-24
System --> Preferences --> Preferred Applications

In there, set Thunderbird as your default email reader. I'm not 100% sure that will work, but it should...

---

### Post by hardyn on 2007-06-24
no, it doesn't, this is a LOOOONG standing complaint.

you can get the gnome menu editor, and add another send to however; its on the forum how to do this.

---

### Post by reclusivemonkey on 2007-06-24
> **hardyn said:**
> no, it doesn't, this is a LOOOONG standing complaint.

Has it been reported on Launchpad?

> **hardyn said:**
> you can get the gnome menu editor, and add another send to however; its on the forum how to do this.

Would you like to post the link?

---

### Post by hardyn on 2007-06-24
yes,

[http://ubuntuforums.org/showthread.php?t=91377](http://ubuntuforums.org/showthread.php?t=91377)

---

### Post by bob-linux-user on 2007-06-26
Thanks for the link. When I downloaded the package it suggested I use "Nautilus-Actions" which I installed using add/remove. I think the instructions refer to an earlier version of Ubuntu-I am using Feisty.

I installed Nautilus actions but could not get send to Thunderbird to work.

??

Regards

Bob

---

### Post by bob-linux-user on 2007-06-26
I have this working now.
This is what I did in Feisty

-Using Add/Remove Programs[COLOR="Blue"] installed "Nautilus Actions Configuration"[/COLOR]
-I went to System-Preferences-Nautilus Actions Configuration
-Press the [COLOR="Blue"]+ [/COLOR]button
-In the label box put in [COLOR="Blue"]Send Attachment via Thunderbird[/COLOR]
-In the icon box i used (for no massively good reason ) [COLOR="Blue"]gtk-edit icon[/COLOR]
-In the path box I put [COLOR="Blue"]mozilla-thunderbird[/COLOR]
-In the parameters box I put [COLOR="Blue"]-compose "attachment=%u"[/COLOR]
-In the filenames and mimetypes box I put[COLOR="Blue"] *[/COLOR]
-I selected the [COLOR="Blue"]only files[/COLOR] radio button
-I [COLOR="Blue"]ticked all the boxes[/COLOR] on the advanced conditions tab

I can't really claim any credit for this I slightly rejigged the earlier posting on this thread

Regards

Bob

---

### Post by reclusivemonkey on 2007-06-26
> **bob-linux-user said:**
> I have this working now.

Thats great =] Can you mark the thread as resolved? This should be an option in the "Thread Tools" now.

---

