---
title: "Raspberry Pi for an achive manager - Final thoughts"
date: 2023-02-12
forum: General Help
---

### Post by Old Jimma on 2023-02-12
Folks:

Approximately 2 years ago, I started a thread asking for help for figuring out a way to reliably back up my laptop. Many people responded with superb suggestions, and among them was to: 
[LIST]
[*]use a Raspberry Pi to back up my laptop over ssh.
[*]
[/LIST]

It was a great idea, and I would give credit where credit is due to one of the best workers on Ubuntu Forums.

In making a Raspberry Pi to do that work, there were many twists and turns that included:
[LIST]
[*]learning that I had to used the same backup tool with the same version on both the Pi and my laptop, and
[*]vexing problems that included the Pi just quitting on the job with no explanation.
[*]
[/LIST]

I will comment here briefly on what I learned on those 2 issues.

**Common Backup Tools on the Pi and the Laptop**
People have strong opinions on what software to use to do this sort of back up. However, to get this to work you must have the same backup tool with the same version on both machines... or it just won't work. I found that the only "tool" that enabled me to do do this was **rsync**. Other tools like rdiff-backup, were offered for both the pi and the current version of Ubuntu on my laptop.... but they were different versions... and did not work, as a result.

Another key issue that was never covered in the forums discussion about this issue was why a Pi might just quit, and stop during a back up... or any other time, for that matter.

Yes, a pi will do this, and I've learned that there is documentation on this that can be traced to insufficient electric power being delivered to the Pi.

This means, that If you have to many old mechanical hard disks, or even too many SSDs being "attached" to a Pi... they all suck electric power, and the pi will compete for that electric power. If you hang too many of those devices off a Pi.... even, though they you may think that you are in the clear because you're giving those devices power thru a separate power strip.... there will come a time when the device will out-compete the PI... because they are attached thru the USB ports... and the pi will decide to turn off and take a long snooze.

When you find your pi turned off, or even if it seems to be alive, it got turned off during that competition for electric power.

And, you will tear your hair out trying to figure out what went wrong.

So, here is my advice: if you are going to use a Pi... use VERY few other periferal storage drives to do the back up... or the least power hungry devices you can get your hands on. 

... and even then, I think you are tempting fates.

Thank you for all of your help over the years, Forum People.

I bid you adieu for a time. Hope these comments help somebody else.

Old JImma from the Old Country

---

