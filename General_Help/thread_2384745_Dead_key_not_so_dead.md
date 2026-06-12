---
title: "Dead key not so dead"
date: 2018-02-11
forum: General Help
---

### Post by skamarla on 2018-02-11
Hello,

I just upgraded to 17.10, and everything went fine, except for a weird behavior I have just observed. When I press a dead key (for an accent), I get a strange character instead. If I'm really-really fast and type the accented letter, it's fine, but most of the time I get the weird letter.

To be specific:
Pressing the acute accent gives me &#944; 
Pressing the grave accent gives me &#8162;
The circumflex gives &#7889;
The umlaut gives &#1255; (without typing the o)

If I want à, è, ó, I have to type the dead key, and then the letter, really fast.

Any ideas? I have a Lenovo ideapad 700

---

### Post by skamarla on 2018-02-11
Now, that's strange. After a reboot, the behaviour has changed slightly.

Now, I still see the weird character when the dead key is pressed, but when I press the "real" letter, it substitutes the weird character, so everything works fine.

This is only happening in the browsers: Firefox, Chromium. The weird character doesn't ever appear in Terminal or in Libreoffice.

Not really a problem, then, I guess I will mark it as solved. I'm still curious as to what was happening, though.

---

### Post by wildmanne39 on 2018-02-11
*Thread moved to **General Help, a more appropriate forum**.*

---

### Post by skamarla on 2018-02-12
Just for the record. There was indeed a problem. I noticed that "repeat keys" wasn't working, and found [this thread]("https://askubuntu.com/questions/975174/repeat-keys-doesnt-work-after-upgrade-from-17-04-to-17-10") on askubuntu. Now, weird characters have disappeared, and repeat keys work.

---

