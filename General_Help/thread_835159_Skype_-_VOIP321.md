---
title: "Skype - VOIP321"
date: 2008-06-20
forum: General Help
---

### Post by toontastic on 2008-06-20
Hi,

I have the Phillips VOIP321 phone which works over the landline and with Skype. It works fine on windows but when I plug the phone in during a Linux boot I don't see any sign of my phone and I can't use it within Skype any more. Has anyone managed to get this phone to work on Linux ?

I know it's an oldish phone but I did a search on here and the only result was for how to install Skype which I've already done.

---

### Post by Opensource-student on 2008-06-20
I dont know much about skype but I might be able to help.
Does Skype work okay? Is this a phone that could require a special driver/special skype access - a program to install or is it plug and play? I dont know much but if it works on Windows give it a shot on Wine.
Maybe try a force mount/force search for usb command (if one exists).
I really dont know a lot about this kind of thing but is the issue you have plugging the thing in and nothing happening.
Good Luck and I hope this gets people thinking

... Look at this, might help > How to use internet by cell phone through USB or bluetooth [http://http://ubuntuforums.org/showthread.php?t=768413]("http://http://ubuntuforums.org/showthread.php?t=768413")

---

### Post by toontastic on 2008-06-20
> **Opensource-student said:**
> I dont know much about skype but I might be able to help.
Does Skype work okay? Is this a phone that could require a special driver/special skype access - a program to install or is it plug and play? I dont know much but if it works on Windows give it a shot on Wine.
Maybe try a force mount/force search for usb command (if one exists).
I really dont know a lot about this kind of thing but is the issue you have plugging the thing in and nothing happening.
Good Luck and I hope this gets people thinking

... Look at this, might help

Yeah Skype works fine. When used on Windows the program installs it's own program but not sure what that program really does.

Yeah the issue is really that I plug it in and nothing happens really.

Thanks for the link I'll have a look through it.

---

### Post by Opensource-student on 2008-06-24
Me thinks your issue could be related to two things.
1. Ubuntu does not recogise your device - try force mount usb, I have no Idea about these commands, I am still getting used to the terminal.
OR far more likely
The Plug-in controls the phone and does not install properly as it is used to windows (likely) or does not have the permissons to do what it needs to do (less likely likely if you install it with sudo)
Try Wine or look to see what the program does (boring) I have heard Wine has taken off with the 1.0 verson (or higher) and as VOIP is so popular they will at least have something.
Try Wine especally if the program runs/installs when you plug the phone into a Windows computer - I dont know much about Wine Sorry
I think the link has broken by the way
> program installs it's own program but not sure what that program does???
Good luck

---

### Post by GregFisk25 on 2010-04-01
What did you end up doing about this phone?

---

### Post by Gerarian on 2010-05-02
Just found promising project: [http://code.google.com/p/voip321/](http://code.google.com/p/voip321/)

---

### Post by toontastic on 2010-05-04
> **GregFisk25 said:**
> What did you end up doing about this phone?


I basically didn't end up using the phone as Skype lol not on Ubuntu anyway.

---

### Post by toontastic on 2010-05-04
> **Gerarian said:**
> Just found promising project: [http://code.google.com/p/voip321/](http://code.google.com/p/voip321/)

Your right, might have to see if I can help.

---

