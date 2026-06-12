---
title: "Firefox, Gnome-panels, Opera problem with 100 percent CPU time used"
date: 2008-01-24
forum: General Help
---

### Post by sageb1 on 2008-01-24
I don't know how much information a Linux guru here would need to help me debug Firefox and sometimes Gnome Panel regarding occassional 100% CPU use, most of the time. Currently this is the Gnome desktop.

As it stands now I am reduced to typing for about 5-10 minutes, only to have whatever is controlling either application to use all the CPU cycles.

I don't know what is common between the two either, because Gnome System Monitor does not name what is running the parts of either application which address virtual memory and real memory.

This program also plagues me when I run XFCE4. Epiphany and Opera are also affected by it - partly because of the Firefox Mozilla library, but Konqueror isn't affect by it.

As well, both Konqueror and Opera have been known to crash and exit, but only Konqueror gives me debugging feedback.

My guess is it is partly to do with Javascripts. Though, when I look at top I get this:

top - 17:26:44 up 6:22, 4 users, load average: 1.19, 1.07, 0.88
Tasks: 120 total, 3 running, 115 sleeping, 1 stopped, 1 zombie
Cpu(s): 8.8% us, 2.6% sy, 34.3% ni, 48.5% id, 5.6% wa, 0.1% hi, 0.0% si
Mem: 254684k total, 234972k used, 19712k free, 4004k buffers
Swap: 361420k total, 197940k used, 163480k free, 81172k cached

Most of the time the CPU spends in lalaland consists of being in nice 96% of the time and 0% in idle.

Is this all a side effect of implementing Gnome-vfs?

---

### Post by sageb1 on 2008-01-24
i cannot believe no one else is experiencing this problem.

in firefox and opera, i get 100% CPU cycles occurring every 10 minutes. at first i thought it was due to java. now i think it's probably kde interacting with gnome or xfce4, and might be a kernel problem.

while dillo never crashes, it does not use cookies and jscript isn't properly enabled.

my "fix" for the 100% cpu cycles used is to quit firefox and wait 30 minutes before I try again. i usually have a gnome-terminal window open to practise using BASH's cryptic commands.

my "fix" for konqueror crashing is to use another browser, quit  when the cpu cycles problem happens, putting around in gnome-terminal, then switch back to konqueror, work until the crash happens again and start over.

to avoid having to start my browsing from scratch i have saved my tabs in my bookmark in each browser.

---

### Post by darkazurka on 2008-05-14
Wrong! The below I wrote first, before I changed a setting in the System Monitor:
1. In the tab "Processes" I select from menu view->All processes. (before it was view->My processes)

As I said (below) I'm using 100% of processing power. 
**In 1st place** comes the process called "gnome-panel" (running) with 51:29, no 51:32, no 51:36. It changes rapidly.
**In 2nd place** comes "Xorg" (sleeping) with 7:52, no :53.
**In 3rd place** comes "Xorg" (sleeping) (another xorg?) with 3:25.
**4th place** "gnome-panel" (sleeping) with 1:13.
**5th** is the System Monitor I run to see all these things "gnome-system-monitor" (running) with 1:18, it took the lead to become 4th place just now. :)

Old:
Now I also see I'm using 100 percent, and at top 1st (CPU time tab) it says gnome-panel with 1:11. 2nd place multiload-applet-2 with 0:38, and 3rd place metacity with 0:36. Firefox is 4th but is gaining on them.

---

### Post by SammyBoy247 on 2008-05-25
Using firefox 3.0b5 under 64bit hardy I get 0% zombie.

The only reason I mention it here is that it seems to be cyclic like the original post.

Had the problem a while no solutions found.  Using 2.0 instead.

---

