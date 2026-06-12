---
title: "[SOLVED] Installation Issues"
date: 2008-06-16
forum: General Help
---

### Post by maretard on 2008-06-16
Hi, everybody!
I'm relatively new to the Linux scene (tried Knoppix and Ubuntu before, but never grew into them), and I recently decided to try Wubi for a spin. However, I'm running into some serious installation issues.

The Windows portion of the installer ran perfectly fine and asked me to reboot; I did so, and booted into Ubuntu.

Ubuntu startup page, blahblah, and I reached the time zone page.
I selected my time zone and pressed Forward.

About 30 seconds pass with the spinning busy cursor.

ERROR: Something about Packman encountering error code 10. Asks me to quit the installer, continue anyway, or try again. I try again. It stays there, at the time zone page with the busy cursor, for about half an hour before I click Cancel and get booted into Live user mode.

I restart my computer and boot into Ubuntu again, and it again asks to install, because obviously it didn't finish. I do the same, except I click "Continue Anyway" instead of retry on the Packman error. I get taken to the next screen with all my personal info, but then I run into ANOTHER error, and once again, it freezes with Try Again, and boots me into Live mode with Continue Anyway.

Now I'm absolutely positive that there's something wrong here. :)

Any ideas? I'm willing to do whatever it takes and learn whatever (veteran programmer, not a noob to computers and tech, just a noob at Linux :D) because it's high time I started working with Linux.

Any help would be greatly appreciated!

Random (useful?) information:
HP Pavilion dv5000
Running Windows XP (not for long, hopefully :D)
1G RAM
Radeon x200 Mobility Express (POC i know T_T)
80G hard drive, 8G left BEFORE installation, 3G remaining (which means it installed, just not... completely? o_O)
AMD Turion64, but I'm running the 32-bit Wubi to avoid any potential issues, which shouldn't be a problem.

Thanks a million!

---

### Post by ago on 2008-06-17
Are you installing with a physical CD in the tray?
What windows version do you use (is it a non-english one?)

You should not see the time zone page at all...

---

### Post by maretard on 2008-06-17
I installed through the Wubi executable, with a downloaded ISO (it's real and verified).
Windows XP, English, came with the laptop. =/
Really? My friend said he encountered the time zone page... o_O

---

### Post by ago on 2008-06-17
if you see the timezone selector in wubi press ctrl+alt+f2 and run

sudo sh /custom-installation/hooks/failure-command.sh

Then post the logs in c:\ubuntu\installation-logs.zip

---

### Post by maretard on 2008-06-17
Wow, uh, I've been on the receiving end of a computing miracle. I uninstalled Wubi and reinstalled it, and the installation ran through fine without any screens or anything. ^_^
Ubuntu boots/runs fine now, the only issue is with my wireless card, but I'll start that up in another thread.

Thanks for all the help, guys!
(For future reference, one possible fix for installation errors: Uninstall and reinstall. :P)

---

