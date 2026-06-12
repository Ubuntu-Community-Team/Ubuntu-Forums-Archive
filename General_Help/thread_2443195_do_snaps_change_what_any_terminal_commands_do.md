---
title: "do snaps change what any terminal commands do?"
date: 2020-05-12
forum: General Help
---

### Post by anotherChris on 2020-05-12
Sorry if this is a dumb question, but I am not a very knowledgeable Linux user...

Now that *buntu is incorporating snaps, does that change what any commands do?  
For example: does ```
apt-get update
``` function the same with snaps as it did before snaps?

Basically, I want to know if any terminal commands have to re-learned, ignored, or newly acquired because of snaps.

---

### Post by CelticWarrior on 2020-05-12
No, it doesn't work for snaps. Those are periodically updated in the background or manually via commands.

The "Updates" utility now incorporates snaps updates as part of the routine so you can use just that.

---

### Post by Dennis N on 2020-05-12
> Basically, I want to know if any terminal commands have to re-learned, ignored, or **newly acquired** because of snaps. 
_New command:_
The **snap** command is for managing snap packages. There are many options:

```
mn@Sydney:~$ snap --help
The snap command lets you install, configure, refresh and remove snaps.
Snaps are packages that work across many different Linux distributions,
enabling secure delivery and operation of the latest apps and utilities.

Usage: snap <command> [<options>...]

Commands can be classified as follows:

         Basics: find, info, install, list, remove
        ...more: refresh, revert, switch, disable, enable
        History: changes, tasks, abort, watch
        Daemons: services, start, stop, restart, logs
       Commands: alias, aliases, unalias, prefer
  Configuration: get, set, unset, wait
        Account: login, logout, whoami
    Permissions: connections, interface, connect, disconnect
      Snapshots: saved, save, check-snapshot, restore, forget
          Other: version, warnings, okay, ack, known, model, create-cohort
    Development: run, pack, try, download, prepare-image

For more information about a command, run 'snap help <command>'.
For a short summary of all commands, run 'snap help --all'.

```
Enjoy your snaps!

---

### Post by TheFu on 2020-05-12
Some Deb packages have been replace by a snap installer.  Chromium-browser is one of those.
On later releases, doing a **sudo apt install chromium-browser** will pull a package down that actually installs a snap version of chromium instead.  [https://snapcraft.io/blog/chromium-in-ubuntu-deb-to-snap-transition](https://snapcraft.io/blog/chromium-in-ubuntu-deb-to-snap-transition)

i wouldn't expect the normal, core, Unix commands to be snap-only.

Some CLI commands are only available as snaps from any repo.  Examples are wormhole and lxd.  There are others, almost certainly.  wormhole  is available as a source python package, but manually dealing with the dependencies is fun.  There are probably a number of server subsystems that are changing to snaps.  I&#8217;ve seen a nextcloud snap, for example.  

lxd is a container management front-end. Recently, they added a kvm management capability to it.  Think the most recent 2 major releases are only available as snaps - v3.x and v4.x.

---

### Post by anotherChris on 2020-05-12
Thanks for all the replies.

---

