---
title: "bash scripting"
date: 2008-07-09
forum: General Help
---

### Post by wcminor on 2008-07-09
im writing a script to install all of the multimedia stuff for new installs. how do you "pause" the script for human intervention? so that you would have to hit enter to continue or quit. hope that this makes sense and have a good week.

wcminor


#!/bin/sh
echo "multimedia install for hardy 8.04, 4-26-08"
echo "**adding the medibuntu repositories**"
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
echo
////////////want human intervention here/////////////////////

echo "**installing adobe flash**"
sudo apt-get purge flashplugin-nonfree gnash gnash-common && sudo apt-get install flashplugin-nonfree
echo

---

### Post by justleen on 2008-07-09
```

#!/bin/bash
echo "Free input! type here!!"
read userinput
echo "You have entered: $userinput" 

```

```

echo "continue? (y/n)"
read answer
if [ "$answer" = "n" ]; then 
exit 
else
echo "very sure???"
fi

```

---

### Post by wcminor on 2008-07-09
thanks for the quick reply and have a good weekend coming up.

wcminor

---

### Post by bodhi.zazen on 2008-07-09
```
read -p 'wake up fool' INPUT
```

---

