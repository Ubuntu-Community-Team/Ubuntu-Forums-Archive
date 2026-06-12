---
title: "BOINC crashes everything"
date: 2005-07-01
forum: General Help
---

### Post by jnoreiko on 2005-07-01
I've just installed BOINC and tried to run the GUI app (boincmgr).
It has a bug in its menus, which don't close if you try to close them without choosing a command.
Not only that, but when I tried to minimize it, my whole system froze and stopped responding. I had to fore a logout with CTRL-ALT-backspace.

Is there a way to get just a single app to quit when the whole system is being unresponsive? Something like OS X's CTRL-ALT-escape that brings up the Force Quit dialog?

---

### Post by veehell on 2005-12-03
Hi

have you connect your boinc-client to any of the projects before you lunch boinc-manager ? Because behaving of clients also depends on how you set your project account on "seti" or "einstein" or "lhc" and so on. You have to specify how many cpu time, ram, disk space and when a how to act in your system. I had similar problems (it runs always, so a lot of apps froze, and sometimes if i override the settings parsed by xml from project homepage my X froze too so i ctrl+alt+backspace to push X to restart) ...after i always use the config settings.

If it is not your issue, sorry for flooding. 
Also go to [http://boinc.berkeley.edu/]("http://boinc.berkeley.edu/") and there are several clients and some 3rd party clients, managers, scripts and so on.

In fact you dont need to have official GUI manager, there are "xsetiathome" "KBoincspy" "Tkseti" gui managers as well. what you need 1st is correctly running client (as user or daemon). Some dudes from 3rd party executables have some scripts which lunch boinc really to be nice to system. ;) check the link and sources there it will help you. 
cheers

I found also: [boinc.dk]("http://www.boinc.dk/index.php?page=mirror_file_list") and there are some add-ons, for win32/*nix/macos platform ;) scripts, tools, guis, spies ....stats...etc :)

---

