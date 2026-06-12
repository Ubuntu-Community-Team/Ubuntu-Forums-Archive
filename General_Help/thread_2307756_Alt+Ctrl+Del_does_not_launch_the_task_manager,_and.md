---
title: "Alt+Ctrl+Del does not launch the task manager, and I can' t find lubuntu-rc.xml"
date: 2015-12-28
forum: General Help
---

### Post by Arvidos on 2015-12-28
Hello!

Rather than launching the task manager, Alt+Ctrl+Del locks my screen/goes to the screen saver.

I've googled for a solution, and found out that one solution is to correct the file [COLOR=#000000]/home/{user}/.config/openbox/lubuntu-rc.xml[/COLOR], but I have no such file! I don't even have the openbox folder (and yes, I've enabled viewing hidden files)

Confusing! :)[COLOR=#000000][/COLOR]

---

### Post by tea for one on 2015-12-28
Ctrl+Alt+Del is a Windows keyboard instruction to launch the task manager when you are using Windows.

If you are logged into Lubuntu, what task do you want to accomplish? 

Kind regards

---

### Post by tea for one on 2015-12-28
You could add the Task Manager application to the panel in Lubuntu:-

Right click on panel > Add/Remove Panel Items > Application Launch Bar > Edit > System Tools > Task Manager > Add > Close

Any good?

---

### Post by vasa1 on 2015-12-28
> **Arvidos said:**
> Hello!

Rather than launching the task manager, Alt+Ctrl+Del locks my screen/goes to the screen saver.

I've googled for a solution, and found out that one solution is to correct the file /home/{user}/.config/openbox/lubuntu-rc.xml, but I have no such file! I don't even have the openbox folder (and yes, I've enabled viewing hidden files)

Confusing! :)
Yes, indeed. Just to be sure, please post the output of the following commands each **between code tags**:
[LIST]
[*]ls ~/.config
[*]env | grep XDG_CURRENT_DESKTOP
[*]echo $DESKTOP_SESSION
[*]wmctrl -m
[*]lsb_release -a
[*]uname -r 
[/LIST]

---

### Post by Bashing-om on 2015-12-28
Arvidos; Hello;

In addition to the above, depending on the Desktop Environment that you have, Might be beneficial to look and see if this control file is present and what it contains:
```

cat /etc/init/control-alt-delete.conf

```
In my case - xfce4 - the key combo is mapped to restart the system .

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by vasa1 on 2015-12-28
> **Bashing-om said:**
> ...

In addition to the above, depending on the Desktop Environment that you have, Might be beneficial to look and see if this control file is present and what it contains:
```

cat /etc/init/control-alt-delete.conf

```
In my case - xfce4 - the key combo is mapped to restart the system .
...
Hi there!
```
$ cat /etc/init/control-alt-delete.conf
# control-alt-delete - emergency keypress handling
#
# This task is run whenever the Control-Alt-Delete key combination is
# pressed, and performs a safe reboot of the machine.

description	"emergency keypress handling"
author		"Scott James Remnant <scott@netsplit.com>"

start on control-alt-delete

task
exec shutdown -r now "Control-Alt-Delete pressed"
$ 
```is what I have on a "vanilla" fully updated Lubuntu LTS. 
I suspect that
[LIST]
[*]all official *buntus come with this file
[*]this file isn't used if the DE (or even just the window manager) provides an alternative
[/LIST]

What does C-A-Del do for you? For me, it launches the task manager (terminal name = *lxtask*) whether I'm in vanilla Lubuntu (LXDE+Openbox) or in an Openbox session (no DE).

Coming back to OP's issue. Something is very odd. There **should/must** be a *~/.config/openbox* folder. It's quite possible that some "accident" has caused it to vanish. And now, openbox, if it's functional, maybe using "system" files (such as an rc.xml somewhere) rather than user-specific files to get things done. I don't really know which files will be read if *~/.config/openbox* is missing.

```
$ locate rc.xml
/etc/xdg/openbox/rc.xml
/home/vasa1/.config/openbox/lubuntu-rc.xml
/home/vasa1/.config/openbox/rc.xml
/usr/share/lubuntu/openbox/rc.xml
$
```The code above is after cleaning up a bit to remove irrelevant "*rc.xml" finds. I suspect */etc/xdg/openbox/rc.xml* maybe used in case there's no local openbox folder. And I just searched */etc/xdg/openbox/rc.xml*: this file has _no_ Lubuntu-specific commands, no reference to a task manager, no mention of lxtask, and the key combo C-A-Delete isn't defined which would explain the use of the control file Bash pointed to.

If OP's interested, the way to go, IMO, would be this:
```
mkdir ~/.config/openbox
cp /usr/share/lubuntu/openbox/rc.xml ~/.config/openbox/lubuntu-rc.xml
openbox --reconfigure
```
and then to try the "fix" hinted at in the first post:> ... I've googled for a solution, and found out that one solution is to correct the file /home/{user}/.config/openbox/lubuntu-rc.xml ...

---

### Post by Bashing-om on 2015-12-28
@ vasa1 K;

Rebooting at this time to test various conditionals.
Will advise.

[INDENT][INDENT]inquiring minds need to know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-12-28
vasa1 has the right of it.

When I execute clt+alt+del from the GUI, the windows manager intercepts the key combo and I get a [s]log out[/s]/lock screen;
from terminal (TTY1) the behavior is the system has control and with the key combo execution the system is rebooted.

[INDENT][INDENT]it just depends
[/INDENT][/INDENT]

---

### Post by vasa1 on 2015-12-28
Bashing-om, thanks for checking :)

In case OP is interested, this is what vanilla Lubuntu has:```
    <!-- Launch task manager on Ctrl + Alt + Del-->
    <keybind key="C-A-Delete">
      <action name="Execute">
        <command>lxsession-default tasks</command>
      </action>
    </keybind>

```And this is what I use:```
    <keybind key="C-A-Delete">        # Task manager
      <action name="Execute"><command>lxtask</command></action>
    </keybind>

```Just remember that after modifying (and saving) lubuntu-rc.xml run **openbox --reconfigure** or in log out and log in.

Oh, and backing up of lubuntu-rc.xml helps as well ;)

---

