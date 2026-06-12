---
title: "Alt function for special characters in Feisty"
date: 2007-06-21
forum: General Help
---

### Post by GerryB on 2007-06-21
I write in different languages. I've learned many special characters using the Alt function on the number keyboard in Windows. For example, if I want é I punch in Alt 0233, for ö Alt 0246 and even for ¾ Alt 0190. Is there such a thing in Linux? There is a lot of international experience on this forum and this would be extremely useful to me and maybe to a lot of other users out there.

---

### Post by MEW on 2007-06-21
I'm not sure if/how you can use Alt+numpad, but there are other ways to type international characters. Go to System > Preferences > Keyboard, and look around in the "Layout Options" tab.

---

### Post by GerryB on 2007-06-22
Thanks for answering. I've got a little system set up in a drawer on the top panel. It works well in Abiword and OpenOffice but not for e-mail (Yahoo, Hotmail). For now, I copy and paste and that works. I posted this thread from within XP where the Alt functions work and it would be nice to have a quick way of doing this in Ubuntu. There might be a way on a keyboard layout like you suggest. I'll explore some more. Thanks again.

---

### Post by ezrollers on 2007-06-22
try this

[http://wiki.linuxquestions.org/wiki/Accented_Characters](http://wiki.linuxquestions.org/wiki/Accented_Characters)

---

### Post by der_joachim on 2007-06-22
What I did, is configure my right Alt key as a compose key. That way, pressing R-alt+'+e will give you é. It beats having to remember the alt-codes. :)

It is a breeze to configure. Open /etc/X11/xorg.conf (do not forget to sudo) and add (or edit) the following line to your keyboard section:
```

	Option         "XkbOptions" "compose:ralt"

```

You can separate different XKB options wint a comma. Restart X and you're set.

---

### Post by GerryB on 2007-06-22
Eh! you are all great. Problem solved. Under keyboard layout options you can choose your "compose" key. I chose the right Alt key since I don't have an Alt Gr key, but there are many choices according to the type of keyboard you have. It's simplicity itself. I now press the right Alt key + apostrophe + any letter to get the accented letter like é, á. You can punch in the letter first or the accent first. Same thing for the other signs, à ù ã À È etc...These were all made in Ubuntu this time. Got to find all the ones I need now.... Thanks a million.

---

### Post by konungursvia on 2007-08-02
Can this be honed and improved to different 2-key combinations for each accent? Without having to press 3 and 4 keys? Thanks

---

### Post by der_joachim on 2007-08-03
> **konungursvia said:**
> Can this be honed and improved to different 2-key combinations for each accent? Without having to press 3 and 4 keys? Thanks

Some internationalized keyboard layouts use the right alt key for such things. I do not know whether US-intl does, but the dutch keyboard layout apparently does. IIRC, RightAlt+e gives you an é etc.

---

