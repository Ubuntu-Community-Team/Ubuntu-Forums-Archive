---
title: "Executing commands on startup"
date: 2006-07-25
forum: General Help
---

### Post by glinsvad on 2006-07-25
I wonder if there is an easy way to have a certain command executed automatically when a user - and I do mean **any** user - logs in.

Before you say System->Preferences->Session (to late huh?), I'd like to point out that I don't have time to perform this action to each individual user. Besides I'd like to be able to script this stuff. The equivalent for one user would look like this (I guess):
```

FILE="~/.gnome2/session-manual"
sudo touch $FILE
echo "[Default]" >> $FILE
echo "num_clients=1" >> $FILE
echo "0,RestartStyleHint=3" >> $FILE
echo "0,Priority=50" >> $FILE
echo "0,RestartCommand=$COMMAND $ARGUMENTS" >> $FILE
echo "0,Program=$COMMAND" >> $FILE

```

Is there an "universal" session-manual file I can edit, so the changes will apply immediately for all users?

---

### Post by Paerez on 2006-07-25
the file is:
/usr/share/xsessions/gnome.desktop

find the line that says:
Exec=gnome-session

and then make your own script somewhere, like
/usr/share/bin/custom_runner.sh

and replace the line with:
Exec=gnome-session & /usr/share/bin/custom_runner.sh

---

### Post by bricedebrignaisplage on 2006-08-03
can I do that to execute a script to create some nodes in /dev ? That requires root privileges. And would it be executed when I log in as root?

Thanks,
Brice

---

### Post by Paerez on 2006-08-03
only if the user has root privileges, in the way I mentioned. There may be other ways, I don't really know.

---

