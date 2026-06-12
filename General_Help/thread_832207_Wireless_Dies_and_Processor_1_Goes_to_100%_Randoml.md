---
title: "Wireless Dies and Processor 1 Goes to 100% Randomly"
date: 2008-06-17
forum: General Help
---

### Post by Sneachtuil on 2008-06-17
When I'm on my laptop and it is connected wirelessly to the internet, every so often it will randomly disconnect from the wireless and the CPU usage of one of the two cores in my processor will shoot to 100%.  All programs function perfectly and nothing else is wrong except I can no longer connect to the internet and my computer is putting out more heat than my fireplace.

I tried to see what was causing the spike in CPU by going into the gnome system monitor, but it shows all processes are using 0% processing power - even the internet-related ones.  I'm comfortable with the command line, but I don't know many internet-related commands to run and so I don't even know what log files or anything to look at.  I also attempted to search these forums for a fix, but wasn't sure what to look for.

Anyone able to point me in the right direction, if not offer a solution outright?

I'm using the ipw2200 driver for an Intel PRO/Wireless 2915ABG mini-PCI card in my laptop and am running Hardy, if that information helps.

Thanks!

---

### Post by pytheas22 on 2008-06-17
The next time it happens, run the command:
```

dmesg
```

which will dump to the terminal information about what's going on.  If you see anything that looks out of the ordinary, google for it and see if you can figure out whether it's the cause of your problem.  If you can't find anything, post the dmesg output here and someone can take a look.

---

