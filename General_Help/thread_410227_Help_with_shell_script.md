---
title: "Help with shell script"
date: 2007-04-15
forum: General Help
---

### Post by NoUseForANick on 2007-04-15
Hello all,

perhaps anyone can help me with this little script: It works nice if used with directories with a single word name, but if used with a directory with spaces in its name, it does not succeed. If there is somebody who can help me with this, I'd be very grateful!
Thanks,

NoUseForANick

```

#!/bin/bash

user="tmp:tmp"

echo "Gewaehlter User/Gruppe:" $user
echo "Gewähltes Verzeichnis/Datei:" $1
echo "[enter]..."
read a

chown -R $user $1
echo "Files..."
find $1 -type f -execdir chmod a=-rwx {} \;
find $1 -type f -execdir chmod u=+rw {} \;


echo "Directories..."
find $1 -type d -execdir chmod a=-rwx {} \;
find $1 -type d -execdir chmod u=+rwx {} \;

```

---

### Post by bashologist on 2007-04-15
Quote your variables; That's very important to do correctly. Variable names are important also, you should choose something meaningful especially when showing people your script.

Maybe this:
```
#!/bin/bash

user="tmp:tmp"

echo "Gewaehlter User/Gruppe: $user"
echo "Gewähltes Verzeichnis/Datei: $1"
read -p "[enter]..." a

chown -R "$user" "$1"
find "$1" -type f -exec chmod a=-rwx,u=+rw {} \; -type d -exec chmod a=-rwx,u=+rwx {} \;
```

---

### Post by NoUseForANick on 2007-04-16
Cool, bashologist,

thank you very much! Works great and your version is of course also much faster! Nice to have people like you around!

Bye,

NoUseForANick

---

