---
title: "Increasing battery life with Laptop Mode Tools"
date: 2014-10-02
forum: General Help
---

### Post by hfsb on 2014-10-02
Hi!

Since I'm in Lubuntu, I noticed that my battery lasts less time compared in Windows.

So, I decided to install Laptop Mode Tools to increase the battery life. However, I have some doubts about the options that I should or not tick. Can you help me please?

By the way, I have a Lithium-ion battery. How do you charge and discharge this kind of battery? Which are the best practices?

Thanks.

---

### Post by tgalati4 on 2014-10-02
To maximize battery life, buy a second battery and rotate them every 3 months.  Lithium batteries have 3 years or 300 charge-discharge cycles, whichever occurs first.  So examine your usage patterns and figure out how long one battery will last then devise a strategy that fits your usage patterns.  If you use a laptop at work, plugged in all the time, and only travel once a month, your battery will degrade as it ages, even though it is not being used much.  If you commute on a train and you use your battery every day, then your battery will hit the 300 cycle life limit in 18 months--so rotating batteries will get you 3 years for both batteries and give you a spare when you need it.

Most laptops have an optimal charging strategy.  I know with an IBM Thinkpad, there are scripts that you can write to stop charging at 95% and start charging at 85% (levels can be customized) to give a little more life--perhaps 10%?

Leaving a laptop plugged in all the time causes the Lithium battery to be at top charge all the time which reduces life through chemical oxidation and higher temperatures.  Some say you should store the batteries at 40%, but then that's not much charge when you need to run.  If you leave the batteries flat, they age as well--something about crystalization and chemical changes which reduce charging capacity.  The batteries need to be exercised--but not too much.

When I played with Laptop Mode tools a few years ago, I was only able to get ~10% improvement.  I got 20 to 25% improvement with undervolting--but that required recompiling the kernel and a lot of testing to find the best settings.  With undervolting, I was able to get close to WindowsXP battery life on a Thinkpad--but it was a lot of work.

If you click on the battery icon, you can get some statistics.  Pay attention to the watts when running on Battery and take accurate notes.  Then look at the Processor Wake-ups.  Note which applications cause the most wake-ups.  Close those applications down if you are not using them.  If you find that you can't close any more applications, then you are at your minimum power level.

The biggest power users:

CPU  (reduce wakeups from programs that you are not using)
Screen (lower brightness as much as you can stand)
Wifi and Bluetooth (any antenna uses power--shut off if you are not using)
Cooling Fans  (try to manage heating so that you minimize fan use)
Hard disks (set useful spin-down parameters or use solid-state disks)

Sometimes in BIOS you can declock your computer--reduce Frontside Bus Speed, or overall CPU clock multiplier--Say from 17 times to 14 times.  That gives you slower performance but some power savings.  Some argue that a slower computer takes longer to complete a task, so the total power for that task is the same.  But, your CPU will run cooler and there will be less fan use--which does save power.

You will find that after lots of testing, you will be lucky to get a 10% improvement--at a cost of having a slow computer, not connected to the web, that you have to squint to see.

You can't change crappy laptop design.  Poor battery life in a laptop has been a continual complaint.

---

