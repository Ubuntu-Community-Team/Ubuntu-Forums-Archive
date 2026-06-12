---
title: "Can someone please explain /etc/xdg/openbox/autostart"
date: 2014-01-19
forum: General Help
---

### Post by vasa1 on 2014-01-19
I don't understand the contents of */etc/xdg/openbox/autostart* found in Lubuntu 13.10:

```

 1	#
 2	# These things are run when an Openbox X Session is started.
 3	# You may place a similar script in $HOME/.config/openbox/autostart
 4	# to run user-specific things.
 5	#
   
 6	# If you want to use GNOME config tools...
 7	#
 8	#if test -x /usr/lib/x86_64-linux-gnu/gnome-settings-daemon >/dev/null; then
 9	#  /usr/lib/x86_64-linux-gnu/gnome-settings-daemon &
10	#elif which gnome-settings-daemon >/dev/null 2>&1; then
11	#  gnome-settings-daemon &
12	#fi
   
13	# If you want to use XFCE config tools...
14	#
15	#xfce-mcs-manager &
   
16	if [ "$DESKTOP_SESSION" != 'gnome' ]; then
17	    DESKTOP_ENV="OPENBOX"
18	    if which /usr/lib/openbox/xdg-autostart >/dev/null; then
19	       /usr/lib/openbox/xdg-autostart $DESKTOP_ENV
20	    fi
21	fi

```
In particular, what do lines 8, 10, 18 and 19 mean?

Also, does "xfce-mcs-manager" exist in current versions or is it something from the past?

---

### Post by varunendra on 2014-01-21
```
 8	#if test -x /usr/lib/x86_64-linux-gnu/gnome-settings-daemon >/dev/null; then
 9	#  /usr/lib/x86_64-linux-gnu/gnome-settings-daemon &
```
**IF** the file "/usr/lib/x86_64-linux-gnu/gnome-settings-daemon" exists and is executable, **then**..
.. execute it in the _background_ *(the "**&**" in the last sends it to the background).*

The "test" command is same as using "[ ]" with "if" condition (e.g., "*if [ -x /usr/lib/x86_64-linux-gnu/gnome-settings-daemon ]; then...*")
You can see the manpage for 'test' (man test) to see its detailed usage.

The ">/dev/null" in the test condition is there to mute the stdout, if any. Usually we redirect the error messages (stderr, or "2>") to **/dev/null** (you may call it a "black-hole" ;)), but the above usage is okay too (for the 'test' command, it doesn't matter whether the result is displayed or not).

If the "IF" condition above fails (either the file doesn't exist, or is not executable), then the ELSE IF part is executed -
```
10	#elif **which gnome-settings-daemon** >/dev/null 2>&1; then
```
"which" command returns the path of the executable file which provides the command supplied with "which". So the above test (the part after 'elif') returns the path of the executable (gnome-settings-daemon) in case it is in the system but not at the default path (thus failing the "IF" test previously).

The ">/dev/null 2>&1" part is implemented in reverse direction by the shell. Means, first the stderr (2>) gets pointed to the address of stdout (&1), thus now showing whatever stdout would be (it otherwise would have shown error messages, if any). Then, the stdout is sent to /dev/null (the 'black-hole').

I'm not very confident about it, but this arrangement is probably meant to mute both stdout and stderr (same thing achieved by "*>/dev/null 2>/dev/null*")

```
18	    if which /usr/lib/openbox/xdg-autostart >/dev/null; then
19	       /usr/lib/openbox/xdg-autostart $DESKTOP_ENV
```
Now this one doesn't make much sense to me. In the first line, either "which", or the path are unnecessary (the 'which' command already returns the path). But anyway, this is what it seems to be testing/doing -
**IF** the file "/usr/lib/openbox/xdg-autostart" exist and is executable, **then**..
..execute it with argument "$DESKTOP_ENV" (which according to the script, evaluates to "OPENBOX" if the current Desktop Session is _not_ "gnome")

**_So the summary of the script is_ -**

**1) The commented, thus now disabled part :** If gnome-settings-daemon exists in the system, and is executable, run it.
**2) The active part :** If the current Desktop Session is NOT gnome, start OPENBOX with xdg-autostart.

> **vasa1 said:**
> Also, does "xfce-mcs-manager" exist in current versions or is it something from the past?
Have no idea about that, probably a regular Lubuntu user can answer that.

---

### Post by vasa1 on 2014-01-21
@varunendra, thanks for walking me through that.

As you guessed, I didn't really follow why there had to be redirection of "test". I ran the command
```
test -x /usr/lib/x86_64-linux-gnu/gnome-settings-daemon
``` and a few others and there was no screen output so why there was need to mute anything puzzled me. 

```
>/dev/null 2>&1
```seemed like overkill ...

The business of the session not being GNOME, gives me the impression that this particular autostart has been brought in from "elsewhere" as there should be no question of a GNOME session in Lubuntu at least by default.

"xfce-mcs-manager" is outdated and dates back to Xfce 4.6 or thereabouts. I can't figure out what the current equivalent is.

So my understanding of your explanation is ... 
assuming that one (gnome-settings-daemon) or the other (xfce-something) is installed
and assuming that one of the two is uncommented
and assuming that the environment isn't GNOME
then Openbox will be launched with gnome-settings daemon or xcfe-something as a "helper". If neither is uncommented, the user will have a "pure" Openbox session (which is what I'm using).

---

