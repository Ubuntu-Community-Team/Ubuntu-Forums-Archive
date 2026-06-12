---
title: "This desktop file is not working"
date: 2017-04-05
forum: General Help
---

### Post by raleigh3 on 2017-04-05
This is not working. 

I must have missed something.

#!/usr/bin/env xdg-open
```

[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Icons Dir
Comment=
Keywords=
Exec=thunar /home/andy/Icons/
Icon=
Categories=
Terminal=false
StartupNotify=true
```

---

### Post by again? on 2017-04-05
I copied your desktop file, changing only the Exec path, saved as "Icons Dir.desktop" and made the file executable.
Works.
```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Icons Dir
Comment=
Keywords=
Exec=thunar /home/[COLOR=#ff0000]glen[/COLOR]/Icons/
Icon=
Categories=
Terminal=false
StartupNotify=true

```
Test your Exec line in terminal.
```
thunar /home/andy/Icons/
```

---

### Post by raleigh3 on 2017-04-05
My back and neck is in great pain.

So my response may be less than adequate.

I did that and it worked.

But that is what is the same as in my desktop file.

---

### Post by again? on 2017-04-05
Don't know then.
Make sure you save it with the .desktop extension.
After you make a .desktop file executable the extension is not shown.

---

