---
title: "azureus &quot;not a file&quot; error"
date: 2007-08-30
forum: General Help
---

### Post by kidstar64 on 2007-08-30
i get this error every time i try to open a torrent file in azureus. any clue on how to fix this?

also when i just try to open azures it boots up and then suddenly closes.

---

### Post by bashologist on 2007-08-30
What's the exact command you're using to launch Azureus? Did you get Azureus from the repo's or their website? Where is this message displayed? 

Try searching google for?
```
azureus "not a file"
```

Here seems to be a similar thread [http://ubuntuforums.org/archive/index.php/t-186625.html](http://ubuntuforums.org/archive/index.php/t-186625.html)

---

### Post by kidstar64 on 2007-08-30
i right click the file and click open with azureus

---

### Post by bashologist on 2007-08-30
Assuming you're using nautilus goto -> "Open With" -> "Open With Other Application..." -> "Use a custom command" -> then enter then your path to Azureus. Now after you've done that try the "Open with Azureus" thing again. That might fix it, I don't know.

 In any case, next time maybe try to give some more information like "I'm using Nautilus" or "The system Admin installed Azureus, so I don't know where it came from!".

---

### Post by kidstar64 on 2007-08-30
i think im using Nautilus. im using Ubuntu 7.04 with gnome. i installed azureus with the add/remove button under applications. i used to be able to at least open azureus and not have it suddenly crash after 3 seconds. so even when i try to open azureus without a torrent file, it still crashes.

---

### Post by bashologist on 2007-08-30
You could download and install Azureus from the official website, or maybe use another torrent client. What version of java? ```
java -version
```

It couldn't be easier to install Azureus from the official website, just follow the instructions.
[http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)

---

