---
title: "Creating Links to WINE'd Applications"
date: 2007-07-09
forum: General Help
---

### Post by peepingtom on 2007-07-09
I would like to be able to call up uTorrent (running under wine) from the terminal by simply typing utorrent in terminal. The reason for this is so I can associate .torrent files with this application. Could someone please help me understand how to create a link in /usr/bin ?


Thanks  for considering this!

---

### Post by peepingtom on 2007-07-10
Is there a more appropriate place to ask this question, then? It isn't really that WINE specific, this would apply to any executable installed in a non-standard location. Any takers?

---

### Post by cookies on 2007-07-10
Make a plain text file (not in OpenOffice, in Text Editor)  and call it utorrent
In the text file type

#!/bin/sh
wine "C:\Program Files\uTorrent( (Or whatever folder it is)\utorrent.exe (Or whatever exe it is)"

And put this file in /usr/bin

---

### Post by peepingtom on 2007-07-12
ahh I forgot the "#!/bin/sh" :D

Thanks a tonne!

---

