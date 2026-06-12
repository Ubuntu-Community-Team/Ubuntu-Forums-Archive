---
title: "printing is crippled"
date: 2006-07-10
forum: General Help
---

### Post by lapsey on 2006-07-10
I have a parallel port Canon BJC-210 printer that, according to linux printing is supported by both CUPS and GIMP-Print.

I have configured CUPS using the gnome printer interface. For the first few times, printing caused just gibberish to print. There are 2 drivers for BJC-210/BJC 210 and I tried them both.

Now, although I send the item to the print queue, the printer starts and then locks up. The print queue remains 'printing' even after I have rebooted the machine. Even stranger is that the document prints when the machine is shutting down!

I tried GIMP-Print instead, yet with that I get nothing but an error message from lp: "error - no default destination available"



I know this is a parallel port printer but apparently it has been supported in linux for quite some time!

Are there any diagnostic programs or other printer handlers I can try?

---

### Post by lapsey on 2006-07-11
no-one?

---

### Post by coolclassic on 2006-07-11
Give turboprint a try they supply excellent drivers:

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

---

### Post by lapsey on 2006-07-11
> **coolclassic said:**
> Give turboprint a try they supply excellent drivers:

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

this is great, apart from a few gtk issues on installing it works really well!

best of all i don't need gnome to set up a printer, now

---

