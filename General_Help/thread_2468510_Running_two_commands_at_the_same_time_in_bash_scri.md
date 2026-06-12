---
title: "Running two commands at the same time in bash script"
date: 2021-11-01
forum: General Help
---

### Post by uros-likar on 2021-11-01
Hi,

For my work I need to create ssh tunnels to remote server and sometimes sync some files using lsyncd. 

I created a bash script with three options. 
1 => create ssh tunnel
2 => start lsyncd
3 => create ssh tunnel and start lsyncd

Option 1 and 2 are working fine but option 3 it doesn't because second command run after I close the first one. How I can run both at the same time? Probably each command should run in separate konsole window? If yes, how I do that? .... if no, what are other options?

Thanx

---

### Post by Holger_Gehrke on 2021-11-01
You need to end the command to create a tunnel with a '&'. This tells the shell to run the command in the background and not wait for it to finish. See the section 'Lists' in the bash manual page.

Holger

---

### Post by uros-likar on 2021-11-01
ah, so simple :) it works, thanx

---

### Post by HermanAB on 2021-11-01
There is also more complex job control possible with the batch command, which has subcommands like bg, fg, jobs, kill etc.

---

