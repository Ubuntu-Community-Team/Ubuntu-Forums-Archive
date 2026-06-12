---
title: "zip multiple folders with password"
date: 2015-08-18
forum: General Help
---

### Post by sohlinux on 2015-08-18
Hi,

I have 200 folders which I want to zip to individual zip files and password protect but each time it zips a new folder it asks me to make a password. so how can I make it use the same password for each folder? so I dont have to enter the password 200 times.

```

for i in */; do zip -r --encrypt "${i%/}.zip" "$i"; done

```

---

### Post by papibe on 2015-08-18
Hi sohlinux.

You can use the --pasword option (or -P for a short version). For example:
```
zip -e -P mypassword  destination.zip  /path/to/file 
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by sohlinux on 2015-08-18
thanks, that works OK but it shows the password on the screen and in the history.

---

### Post by papibe on 2015-08-18
Put the code on a script:
```
#!/bin/bash
for i in */; do
    zip -r -e -P mypassword "${i%/}.zip" "$i"
done
```
Remove all permissions for others:
```
chmod 700 ./myscript.sh
```
And run it like this:
```
./myscript.sh
```
That should keep the password out of the history.

Let us know how it goes.
Regards.

---

### Post by nerdtron on 2015-08-18
Or you can also clear the history/remove history entry after you are finished with your one time command.

---

### Post by sohlinux on 2015-08-19
thanks :)

---

