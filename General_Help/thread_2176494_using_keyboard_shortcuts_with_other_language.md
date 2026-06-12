---
title: "using keyboard shortcuts with other language"
date: 2013-09-24
forum: General Help
---

### Post by koko0 on 2013-09-24
hi,
i'm using ubuntu for a while, and i was always bothered by the fact that when i'm on different language (Hebrew on my case), shortcuts (like ctrl+c) doesn't work.
i can see how it makes sense (ctrl + &#1489; is not ctrl + c), but in windows i don't need to switch keyboard layout to copy, which is much better.
there is a way to achieve that on ubuntu?

and btw, i'm on ubuntu 13.10 (daily), and i can't make ctrl+shift shortcut to switch layout (the gui doesn't accept it, no error msg). it is a known bug? 
i even tried on fresh ubuntu 13.10 live disk, same problem.

---

### Post by varunendra on 2013-09-26
> **koko0 said:**
> hi,
i'm using ubuntu for a while, and i was always bothered by the fact that when i'm on different language (Hebrew on my case), shortcuts (like ctrl+c) doesn't work.
i can see how it makes sense (ctrl + &#1489; is not ctrl + c), but in windows i don't need to switch keyboard layout to copy, which is much better.
there is a way to achieve that on ubuntu?

Interestingly, I just added "Hebrew" keyboard layout to my existing layouts, and I have no problems with Ctrl-C or Ctrl-V (only tried these two). How have you added the keyboard layout? And what is your input method.

I opened "System Settings" > Language Support" to see which input method is in use on my system *(I already have two different "Hindi" keyboard layouts besides default "English")*, and it showed "none". To add the keyboard layout I used "System Settings > Keyboard Layout". Of the four available options (Hebrew, Hebrew (Biblical Tiro), Hebrew (lyx), Hebrew (phonetic)), I chose the top one - Hebrew.

Also, the hotkey to change the layout in my system is "Alt-Shift", but I think I manually configured it that way sometimes ago *(Syetem Settings > Keyboard Layout > Options > Key(s) to change layout)*.

Maybe the problem is the method you are using to add the layout?

**PS:**
I am on 12.04 by the way. Since 13.10 is not officially released yet, bugs are to be expected.

---

### Post by koko0 on 2013-09-26
i think i have installed ubuntu with Hebrew.
as far as i remember, shortcuts never worked when i was on a different language input (since 10.04...).
to be sure, try to type some Hebrew letters ("asd" -> "&#1513;&#1491;&#1490;"), and then copy and paste using the shortcuts.

and when i try to make the shortcut for switching input to be  Alt Shift (Using All Settings -> Region & Language -> Text Entry) its just doesn't accept the new shortcut (same behavior as pressing Esc).
any other shortcut is accepted.
but thats a problem i have encountered only on switching to 13.10.

---

### Post by varunendra on 2013-09-26
> **koko0 said:**
> i think i have installed ubuntu with Hebrew.
as far as i remember, shortcuts never worked when i was on a different language input (since 10.04...).
to be sure, try to type some Hebrew letters ("asd" -> "&#1513;&#1491;&#1490;"), and then copy and paste using the shortcuts.
Did that in gedit, and now doing this here :
> asd (typed) -> "&#1513;&#1491;&#1490;"
asd (copied) -> "&#1513;&#1491;&#1490;"
&#1491;&#1493;&#1489;&#1489;&#1511;&#1491;&#1491; !
&#1491;&#1493;&#1489;&#1489;&#1511;&#1491;&#1491; !
The second line was full Ctrl-C --> Ctrl-V while being in the Hebrew keyboard layout (edited 'typed' to 'copied' later). The last two lines are "success !", the first one typed, the last one ctrl-c --> ctrl-v. So no problem here.

However, I have installed Ubuntu with default language (English (US)), didn't try to apply the language change "system-wide", so can't say if that may be a problem.

But I just booted a VM into live mode with 13.04 ISO and choose what I think was Hebrew (the language between "Gujrati" and "Hindi", confirmed to be hebrew when I tried 'asd' again) from the language selection screen in the advanced menu. Opened gedit and tried 'asd' there. Interestingly, the keyboard layout by default was English there, but Hebrew was already present as optional layout. So I had to change the layout there, and tried 'asd' again - it got typed in hebrew. Tried ctrl-c --> ctrl-v there and no problem again.

I think you should try it in the live session yourself and see how it is different than your installed setup.

---

### Post by koko0 on 2013-09-26
now i got confused.
i have installed gnome (not related), and on gnome alt-shift always shows that i switch layouts, but whats really happened thats from Hebrew to English Alt-Shift works, but from English to Hebrew W/E i have set in the settings works (still cant assign Alt-Shift).
i guess u have checked on Gnome?

screw this, i'm formatting...

---

### Post by varunendra on 2013-09-26
> **koko0 said:**
> i guess u have checked on Gnome?
Nope! Only Unity, both in my installed 12.04 and the live 13.04 (obviously).

> screw this, i'm formatting...
..and install either 12.04 (recommended) or 13.04, not 13.10 if your target is getting a working and stable system.

13.10 at this point is really meant for those who 'want to help the developers' by finding and reporting bugs in it. The official release in October may see some significant changes in both packages and overall behaviour.

---

### Post by koko0 on 2013-09-26
and as you see, i am finding a lot of bugs...
are you using the 64bit installations? it might be our difference.

---

### Post by varunendra on 2013-09-26
Yup, 12.04.1 64bit here, haven't updated for a long time either (currently am on kernel 3.2.0-36).

It's great if you are willing to contribute to bug fixing. I hope you already know that the correct place to file bug reports is launchpad. Developers never look into the forums, and they can't, since most of times, they are already overloaded with existing bug reports.

([Effective Bug Reporting HowTo]("https://help.ubuntu.com/community/ReportingBugs"))

---

