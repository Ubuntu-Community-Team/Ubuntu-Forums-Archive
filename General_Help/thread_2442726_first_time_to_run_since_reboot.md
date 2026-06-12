---
title: "first time to run since reboot?"
date: 2020-05-06
forum: General Help
---

### Post by Skaperen on 2020-05-06
i want to have a script that can determine if this is the first time it is running _for this user_ since the system has rebooted.  if it can get the time of the last reboot, it could keep track of times it runs in a file in _the user home directory_.  if the last time it ran is before the last reboot then it knows this is the first time.  i would need to figure out a way to lock the file to be sure i don't have 2 scripts started in parallel each believing it is the first.  2 different users starting it at the same time would not be an issue since they each have separate home directories and separate date files.

---

### Post by erind on 2020-05-07
To my knowledge the scripts run times don't get logged in the log files, unless one manually makes the script to write to a file. However to make sure your script runs only once there are generally two exact ways to make sure it doesn't happen: 

1) Test for the creation of a temporary **directory** in the beginning of your script.
2) Use **flock** command.

For the first way (mkdir name_of_dir):

```
## mkdir in say /tmp
LOCKDIR=/tmp/lock_dir_any_name

if mkdir $LOCKDIR
then
    # Your commands of script go here ...
    # here ...

    # Then remove your created directory
    if rmdir $LOCKDIR
    then
        echo "Good"
    else
        echo "Could not remove lock dir" >&2
    fi
else
    # Handle error condition
    ...
fi

```

For the second way (flock):

```
[ "${FLOCKER}" != "$0" ] && exec env FLOCKER="$0" flock -en "$0" "$0" "$@" || :
```

The above code comes directly from the examples section of manual pages of flock.

P.S. Both codes are found online.

---

### Post by ActionParsnip on 2020-05-07
Could have a text file in /tmp (Which is empty at boot) with the user's names in who have ran the script.

---

### Post by SeijiSensei on 2020-05-07
> **ActionParsnip said:**
> Could have a text file in /tmp (Which is empty at boot) with the user's names in who have ran the script.

How would this work?  /tmp is completely rewritten and empty after a reboot.

---

### Post by Skaperen on 2020-05-08
> **SeijiSensei said:**
> How would this work?  /tmp is completely rewritten and empty after a reboot.

maybe **ActionParsnip** is just figuring a way to limit to just one script at a time.  once *that* is done, then it could check its _last-ran file_ in the home directory to get and update that timestamp.  i think that could work.  but i still like **erind**'s mkdir idea.

of course, there could be more than one kind of script doing this so each would need unique directory and/or file names.

---

