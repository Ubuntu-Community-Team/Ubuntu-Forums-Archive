---
title: "HowTo make Midnight Commander remember the working directory"
date: 2012-12-23
forum: General Help
---

### Post by hzFVOW00pw on 2012-12-23
Midnight Commander, by default does not remember its parent working directory (pwd), which is sometimes quite annoying. There is a workaround script in /usr/share/mc/mc-wrapper.sh, but I believe that it is broken.

Putting the next line in a script in /etc/profile.d does **not** work:

```
alias mc=/usr/share/mc/mc-wrapper.sh
```

Copying the script to /etc/profile.d and then sourcing it does work:

```
sudo cp /usr/share/mc/mc-wrapper.sh /etc/profile.d/mc-wrapper.sh
. /etc/profile.d/mc-wrapper.sh

```

**...but** then it shows the pwd always in **both panels** of MC, and the pwd is not remembered when you close the terminal. It doesn't not work with sudo as well.

So i want a more flexible solution. I want the pwd remembered in the **first panel** between terminal sessions/reboots and to have a standard 'fallback' directory in the **second panel**. I also want be able to change to a specific directory upon starting MC with an alias.

Create a file /usr/local/bin/mcdir with gedit:

```
sudo gedit /usr/local/bin/mcdir
```

Paste the following code in gedit:

```
#!/bin/bash
#
# Description: Workaround to save current working directory in MC.
# /usr/lib/mc/mc-wrapper.sh is broken, it does not write out the
# MC_PWD_FILE file when sourced. Putting this as a function in
# a file in /etc/profile.d, works, but not with sudo, as it will
# not find the function and complain about command not found.

# Start script

# You can specify an alternative skin for root if you wish. Comment out the next line if you want the default skin.

SKIN="modarcon16root.ini"

MCSKIN="-S ${SKIN:=default.ini}"

# Save to standard directory

MC_PWD_DIR="${HOME}/.local/share/mc"

[ -d "${MC_PWD_DIR}" ] || mkdir -p "${MC_PWD_DIR}"

# Read pwd file if it exists

MC_PWD_FILE="${MC_PWD_DIR}/pwd"

[ -f "${MC_PWD_FILE}" ] && MC_PWD="$(cat "$MC_PWD_FILE")"

# Remove pwd file, because MC will not overwrite the file

rm -f "${MC_PWD_FILE}"

# MC starts and creates a new pwd file. MC defaults to / or $HOME for the second panel

[ ${UID} = "0" ] && /usr/bin/mc ${MCSKIN} -P "${MC_PWD_FILE}" "$@" "${MC_PWD}" "/" || /usr/bin/mc -P "${MC_PWD_FILE}" "$@" "${MC_PWD}" "${HOME}"

exit 0
```

Save the file, close gedit, and make the file executable:

```
sudo chmod +x /usr/local/bin/mcdir
```

You can run the script directly in a Terminal, or put aliases in /etc/profile.d/mcdir.sh:

Create a file with gedit:

```
sudo gedit /etc/profile.d/mcdir.sh
```

Paste the following code in gedit:

```
[ -z "$BASH_VERSION" -o -z "$PS1" -o -n "$BASH_ALIASES" ] && return

BASH_ALIASES="1"

alias mc="mcdir"
alias mcm="mcdir /media ~/Desktop"
alias mcr="su-to-root -H -c mcdir"
alias mcl="su-to-root -H -c 'mcdir /usr/local/bin'"

```

Save the file, close gedit, and source the file:

```
source /etc/profile.d/mcdir.sh
```

**mc** will now change to the **pwd  in the first panel** and to **~/ in the second panel**, and remember the pwd in the active panel on exit
**mcm** will change to **/media in the first panel** and to **~/Desktop in the second panel**, and remember the pwd in the active panel on exit
**mcr** will run mc as root, change to the **pwd  in the first panel** and to **/ in the second panel**, and remember the pwd in the active panel for root on exit
**mcl** will run mc as root, change to **/usr/local/bin in the first panel** and to **the pwd in the second panel**, and remember the pwd in the active panel for root on exit

Note that you need the -H option if you have setup sudo, to prevent mcdir writing a temp file with root permissions in $HOME/.local/share/mc. Such a file cannot be overwritten if you start mcdir as normal user.

---

