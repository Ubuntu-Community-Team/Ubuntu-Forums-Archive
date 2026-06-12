---
title: "Some applications stop working"
date: 2023-01-18
forum: General Help
---

### Post by rodride on 2023-01-18
hi,
I'm on ubuntu 22.04.1 and I'm having a problem with some applications (gnome-terminal,bleachbit, timeshift, synaptic) that no longer launch. 
TTY consoles don't work either. 
The last action I performed before was to scan my system with LMD.
Any ideas to solve that?
Thanks

---

### Post by rodride on 2023-01-19
gnome-terminal, bleachbit and synaptic work with Alt+F2 and sudo app name

these applications do not launch as user

---

### Post by ActionParsnip on 2023-01-19
If you press CTRL + ALT + T does a terminal launch OK?

---

### Post by rodride on 2023-01-19
No CTRL + ALT + T don't work

---

### Post by ActionParsnip on 2023-01-19
If you run a terminal using sudo, then use "su foo" to become your user (Replace "foo" with your actual username) then try to run the GUI apps from there.

I suspect you went a bit hard with Bleachbit and now apps won't run because you "cleaned" too much

---

### Post by rodride on 2023-01-19
nothing happens with "su username"

---

### Post by TheFu on 2023-01-19
What do the system logs say?
It is amazing that you can login with all those programs refusing to launch.
Any chance you've been abusing sudo and some critical files were created with root ownership under the $HOME directory?  This command will find them:
```
$  find ~ -user root
```

There really aren't **any** files that should be owned by root in a user's HOME.  If you find **any**, fix them.

---

### Post by rodride on 2023-01-19
here is a snippet of the output of "journalctl -xe" :

L'unité (unit) UNIT a terminé son démarrage, avec le résultat done.
janv. 19 18:08:56 ubuntu systemd[2145]: vte-spawn-7b9d19ef-23eb-4ff2-9833-031bc4699227.scope: Couldn't move process 13807 to requested cgroup '/user.slice/user-1000.slice/user@1000.service/app.slice/app-org.gno>
janv. 19 18:08:56 ubuntu systemd[2145]: vte-spawn-7b9d19ef-23eb-4ff2-9833-031bc4699227.scope: Failed to add PIDs to scope's control group: No such process
janv. 19 18:08:56 ubuntu systemd[2145]: vte-spawn-7b9d19ef-23eb-4ff2-9833-031bc4699227.scope: Failed with result 'resources'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; The unit UNIT has entered the 'failed' state with result 'resources'.
janv. 19 18:08:56 ubuntu systemd[2145]: Failed to start VTE child process 13807 launched by gnome-terminal-server process 13781.
&#9617;&#9617; Subject: L'unité (unit) UNIT a échoué
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)

---

### Post by rodride on 2023-01-20
I found a solution for gnome-terminal: launch it with ALT + F2 and "gnome-terminal -x bash"

For synaptic, bleachbit and timeshift I modified their .desktop file by adding "sudo" in the exec line.

These are the solutions I found to launch these apps.

---

### Post by TheFu on 2023-01-20
Please re-read post #7 above.
You probably want to use 'sudo -H' as the prefix, if you are going that direction.  I think for GUI programs, there's a better alternative to elevate permissions.  It was pkexec in older releases. I don't know what 22.04 uses, but there are probably examples in the gparted.desktop file.

---

### Post by ajgreeny on 2023-01-20
22.04 still uses ***synaptic-pkexec*** as the command for synaptic as it has done for some time now.

Gparted which I have installed is installed on my system uses **/usr/sbin/gparted %f** for the executable, ie, no mention of needing root permissions even though it then automatically asks for my password.

Perhaps this happens from the line **Categories=GNOME;System;Filesystem;** also in that .desktop file.

---

### Post by TheFu on 2023-01-20
I don't know most GUI programs, so I'm completely ignorant on how they elevate permissions.  Also, the default way that sudo does things seems to have changed - either in 20.04 or later. I don't keep up with those details, until they matter to me. No 22.04 in serious use here yet.  I'm afraid to use it for a desktop, but maybe for servers, it will be ok.

In the interest of "do no harm", when elevated permissions are needed, 'sudo -H {command}' should do no harm AND actually work, provided sudo has been unlocked, recently, already.  If the password cannot be entered because it was launched from a menu, I don't know what would happen if a password entry window doesn't happen.

---

### Post by rodride on 2023-01-20
TTY console still don't work

---

### Post by #&amp;thj^% on 2023-01-20
It may just need a little re-install:
```
sudo apt install --reinstall systemd gnome-settings-daemon gnome-settings-daemon-common
```
I'm assuming update has been previously ran recently.."apt update"

---

### Post by Impavidus on 2023-01-20
The synaptic.desktop file calls synaptic-pkexec, which is a one line shell script running pkexec synaptic. I dn't know what happens when you simply run it with sudo from the .desktop file. It has no terminal, so how should it ask the password?

It looks like the system has some difficulty finding your shell (as gnome-terminal works when you ask for a specific shell). I hope you haven't abused sudo and haven't messed with the passwd file, have you? It also looks like you try to solve your problem with a workaround that may have unknown and possibly unpleasant side effects. Actually, your workaround is considered sudo abuse. So, as asked in post #7, are there any root owned files in your home directory?

---

### Post by rodride on 2023-01-20
No there is no file owned by root in my home directory

---

### Post by rodride on 2023-01-20
after modifying the shell: chsh -s /bin/bash username
my applications now work normally without invoking sudo

---

### Post by rodride on 2023-01-20
Thanks for help

All works fine now

---

### Post by Impavidus on 2023-01-21
Sounds like the shell wasn't properly set in your /etc/passwd. You may want to know what caused this. I can think of playing with the chsh command, manually changing /etc/passwd or filesystem damage.

You can properly mark this thread as solved by clicking thread tools (near top of page) &#8594; mark thread as solved.

---

