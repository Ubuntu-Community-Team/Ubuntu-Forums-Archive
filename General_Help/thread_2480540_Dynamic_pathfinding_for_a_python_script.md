---
title: "Dynamic pathfinding for a python script"
date: 2022-11-02
forum: General Help
---

### Post by Arunomi on 2022-11-02
Hi, I'm trying to create a python shell script that needs a path in it but the path is different depending on where the script is executed.

I have three projects that have a file this script needs. These projects have a couple of subdirectories and I want to be able to execute this script anywhere inside these projects.

So the script needs to know which project it's being executed in and to get the path to the file from where in the project it's executed from.

---

### Post by TheFu on 2022-11-02
There are multiple different methods, but none are 100%.  It is relatively easy to get 95% accurate versions using bash as the startup:

```

# Determine the directories
SCRIPT_DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" >/dev/null 2>&1 && pwd )"
if [ -h "${BASH_SOURCE[0]}" ] ; then
   SCRIPT_DIR=$(stat "${BASH_SOURCE[0]}" |grep File: | sed -e 's#^.*-> ##go')
fi
echo $SCRIPT_DIR

```

Of course, the commands uses in that snippet really should point to the full absolute path of those commands, to ensure the sysV or bsd versions are found, depending on your need.  That means  'grep' ---> '/bin/grep'.

There are more complex versions of this code that get slightly higher accuracy levels.  The issue is mainly caused by using symbolic links in odd ways, which is sometimes necessary.  It is also common to check for files in specific locations, in order.  This is because we expect a certain priority for settings for all Unix-like programs.  That priority is usually:
0. Command line option
1. Environment variable
2. ~/.some-file-rc
3. ~/.local/program/config
4. /etc/some-file-rc
5. /etc/program/config
6. Compile time defaults

If someone goes to the effort of using a command line option, then that should override anything else.  The defaults set in the code should be last, but still reasonable, whenever possible.

---

### Post by MAFoElffen on 2022-11-02
For Python
```

import os

print(os.path.dirname(os.path.realpath(__file__)))

```

---

