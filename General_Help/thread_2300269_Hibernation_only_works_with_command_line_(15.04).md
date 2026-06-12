---
title: "Hibernation only works with command line (15.04)"
date: 2015-10-24
forum: General Help
---

### Post by Sebastin_Perez on 2015-10-24
Hi People. I have a problem with the hibernation in Ubuntu 15.04. I know is common to have problems with this feature (it has been disabled at default), but this is strange. I enabled again the option to hibernate in the menu, following a tutorial that i read. But using that, the **hibernation is unstable** and only work 50% of the times. When it dont work, after restart the machine stops loading before showing the "Ubuntu logo" (the screen freezes with the purple ubuntu color).

BUT, i can use the hibernation good with a console comand: **echo disk | sudo tee /sys/power/state** 

I dont remember where i read it, but it works fine. Why is possible that it fails with the menu and using this comand works flawlessly?

IS there a way to create a shorcut for that command? Thanks to all!!!!!!

PD: Sorry for my bad english.

---

### Post by tgalati4 on 2015-10-24
Welcome to the forums.

Does suspend/sleep work OK?

```
sudo pm-suspend
```

Check the log files (/var/log/pm-suspend and /var/log/pm-powersave.log) and see what is causing the interference.  I don't find hibernation useful because it takes the same amount of time as a cold boot.   I use sleep exclusively.   You could spend a lot of time troubleshooting a problem for a feature that you may feel is not useful.

---

