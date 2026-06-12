---
title: "ClamAV causes 100% CPU usage."
date: 2019-03-06
forum: General Help
---

### Post by Brent_Santin on 2019-03-06
I'm running Lubuntu 16.04.6 on an older 2-core computer. Over the past two days, I noticed that my computer fan was constantly whirring and the computer seemed sluggish. The CPU meter on my taskbar showed that my computer had 50% of it's total CPU power occupied even while idling. 

Calling [FONT=courier new]**TOP**[/FONT] from the command line indicates that the process "CLAMAV" (antivirus) is taking 100% CPU (I guess that means the entire processing power of one core - so 50% of my two-core system).

[FONT=courier new]**sudo kill <PID>**[/FONT] 

...immediately fixes the problem, but now I am running without anti-virus.

This problem seems to have developed in the past few days - I think after a Software Updater update to Lubuntu. I have used CLAMAV for the past three years  without issue, so don't know why the problem has suddenly developed now. I tried un-installing and re-installing CLAMAV and components through Synaptic Package Manager but it did not help.

Can anyone help me fix this. If you need more info about my system just let me know what you need and I will post it. The computer is a 2-core Pentium-D with 3GB RAM.

Thanks!

---

### Post by mastablasta on 2019-03-07
is the PC a server (e.g. email server) to windows machines? 

of not the easiest solution could be to remove the clamav.

second solution could be to use another (proprietary) AV. there are a couple that work on linux. 

clam av detection rate is rather low anyway. so i am not sure i would use it. furthermore, in my case all the windows machines connected to linux have their own antivirus.

a more important thing is to keep browser up to date.

---

### Post by monkeybrain20122 on 2019-03-07
Get rid of it. You don't need AV on linux, clam detects Windows viruses and is pretty crappy anyway (lots of false positives and false negatives, i.e useless)

---

### Post by Brent_Santin on 2019-03-07
No this is not a mail server, but a normal home desktop running Lubuntu for personal use. The ClamAV is started on bootup.
I've read back and forth opinions on needing AV for Linux. I will wait a week or so (killing ClamAV manually) to see if there is a bugfix, otherwise I guess I will remove it. Still would be interested to hear from anyone that can think of a solution. Thanks.

---

### Post by Autodave on 2019-03-07
I have 8 machines running Ubuntu/Xubuntu.  Several machines are open to the public.  Been running Linux for over 10 years.  Never ran an antivirus. Never had any problem.

---

### Post by SeijiSensei on 2019-03-07
As everyone has said, the solution is to stop running ClamAV.

---

