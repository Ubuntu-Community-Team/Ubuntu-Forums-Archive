---
title: "Capturing keystrokes in BASH"
date: 2006-11-28
forum: General Help
---

### Post by thomasaaron on 2006-11-28
Hey, folks.

I've been looking for a way to capture keystrokes in BASH.
I've logged quite a few hours figuring it out, and I just wanted to ensure there was information on it on the forum.

Here is the script:

#!/bin/bash
# Capture keystrokes without needing to press ENTER.

old_tty_setting=$(stty -g)        # Save old terminal settings.
stty -icanon -echo                # Disable canonical mode and echo

keys=$(dd bs=1 count=1 2> /dev/null)

echo you pressed $keys
stty "$old_tty_setting"           # Restore old terminal settings.

exit 0


Changing the count sets how many keys you want to press before the program moves on.

---

### Post by bettlebrox on 2006-11-28
There is a command called script that will copy everything the user types. Just type script and off ye go! ;)

---

### Post by der_joachim on 2006-11-29
I am getting a bit rusty, but have you tried the command "read"?

---

### Post by thomasaaron on 2006-11-29
Yes. But you have to press enter with the read command. I needed something where you just pressed a key.

---

### Post by der_joachim on 2006-11-29
> **der_joachim said:**
> I am getting a bit rusty, but have you tried the command "read"?

Whoops! Sorry for quoting myself. ](*,) I searched my bookmarks for a viable [example]("http://www.tldp.org/LDP/abs/html/internal.html#READREF").

```

#!/bin/bash
# "Reading" variables.

echo -n "Enter the value of variable 'var1': "
# The -n option to echo suppresses newline.

read var1
# Note no '$' in front of var1, since it is being set.

echo "var1 = $var1"


echo

# A single 'read' statement can set multiple variables.
echo -n "Enter the values of variables 'var2' and 'var3' (separated by a space or tab): "
read var2 var3
echo "var2 = $var2      var3 = $var3"
# If you input only one value, the other variable(s) will remain unset (null).

exit 0

```

---

