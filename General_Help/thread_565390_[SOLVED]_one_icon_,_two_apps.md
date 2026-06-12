---
title: "[SOLVED] one icon , two apps"
date: 2007-10-02
forum: General Help
---

### Post by banda on 2007-10-02
how can i make one icon launch two applications at the same time??..
i want to do this to launch audacious and another app which acts as a media library for audacious together

---

### Post by McNils on 2007-10-02
Create a shell script that starts your programs. Somthing like this...

```

#!/bin/sh

program1&
program2&

```

---

### Post by banda on 2007-10-02
i am not too good with linux...
is there any easier way??

---

### Post by Onyros on 2007-10-02
That's as easy as it gets, mate ;)

Just open up gedit, paste that code (with the specific programs replaced, that is), and save as (e.g. operapidgin).

Then, right click on that file, head to Properties --> Permissions --> enable "Execute" on Owner/Group/Others.

Copy that very file to /usr/local/bin (for example, by using the terminal command "sudo cp kazehakaseclaws /usr/local/bin"), and then just create a menu item on your Applications list, at the location you prefer (Internet, Accessories, etc). At "Command", all you have to do is insert the name of the script you just created (e.g., lifereapsi), and then choose the name you want listed, as well as the icon, if you have one.

Seems more complicated than it is, really, just give it a try ;)

note: script names are just examples, operapidgin, kazehakaseclaws and lifereapsi - they're just for reference, let that be clear)

---

### Post by banda on 2008-01-28
thanks.. that worked well

---

