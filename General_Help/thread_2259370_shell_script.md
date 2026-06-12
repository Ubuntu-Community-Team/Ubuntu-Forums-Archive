---
title: "shell script"
date: 2015-01-04
forum: General Help
---

### Post by jimbo10 on 2015-01-04
just tried writing a short "shell script" to automate a log in to a VPN......

format:
cat > filename
cd VPN_dir;
sudo open_vpn_client <argument>
^d

i then used chmod +x to make the file executable......but....comes up "no such command or file-name"   :(

should the exe file be in the /usr/bin dir ?

any help much appreciated.....its a bit frustrating having to 'tap in' several lines of code for the VPN start-up sequence......  :frown:


ta!

---

### Post by steeldriver on 2015-01-04
In order to execute it without prepending the path, you will need to put it in a directory that's on your executable $PATH

For a homebrew script such as this, probably the best location is your $HOME/bin - if that doesn't currently exist, you will need to create it and then log out and back in in order for it to be added to $PATH.

You should also add a 'shebang' to the top of the script to tell the system what shell interpreter to use e.g. 

```

#!/bin/sh

cd VPN_dir
sudo open_vpn_client <argument>

```

---

### Post by nerdtron on 2015-01-04
Or you can put you script on the /usr/local/bin

I think this folder is intended for custom made scripts.

---

### Post by jimbo10 on 2015-01-04
thnx, youse blokes..... ):P
it worked like a 'charm', eh?

now....i don't hafta 'tap in' a heap of malarkey every time
(eh.....helps if you done a computer course 25-odd yrs or so ago that was 'top heavy' with DOS and UNIX, eh?) 


cheers!

---

