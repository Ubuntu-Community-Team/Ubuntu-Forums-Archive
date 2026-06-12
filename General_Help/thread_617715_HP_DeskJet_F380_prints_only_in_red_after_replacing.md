---
title: "HP DeskJet F380 prints only in red after replacing ink cartridge"
date: 2007-11-19
forum: General Help
---

### Post by FrozenFlame22 on 2007-11-19
I have a HP DeskJet F380 All-in-one Scanner/Copier/Printer. It was working near perfectly until the black ink ran out. I replaced the ink cartridge, ran through the automatic alignment (it prints a test page and then asks me to scan it), and then I used HP Device Manager to make sure that it was reporting ink levels correctly. The problem is now it will only print in red.

I've tried everything I know and I've exhausted my knowledge of how to get this working. I've tried printing from different programs, printing the Ubuntu "Printing" test page, printing the HP Device Manager test page, I've even tried setting it so that it will print in black ink only gray scale. Regardless of the settings it will only print in red!

Easy things out of the way first. I've made sure that it is the correct ink cartridge for this printer: HP Black Print Cartridge 21. I've also checked drivers; I'm using the driver recommended by HP on their support webpage and forums: HP DeskJet F300 Foomatic/hpijs.

Any suggestions on what I should try now?

---

### Post by FrozenFlame22 on 2007-11-22
Bump?

I'm still having problems with this printer, and I'm running out of color ink! I'm already completely out of blue and the red is getting patchy. I've tried setting the print settings to grayscale, but the best result that I can get from that is it starts the next page in black, but switches to red ink halfway down the page. All subsequent pages are in red. Help?

---

### Post by FrozenFlame22 on 2007-11-22
Any ideas anyone?

I really need to be able to use my printer. Any ideas on how I can get it to recognize my black ink cartridge and use it instead of red?

---

### Post by LaRoza on 2007-11-22
I would remove the colour cartridge to see what happens.

I have the same printer, and recently ran out of black ink, so I am interested in this thread.

---

### Post by FrozenFlame22 on 2007-11-22
I tried it and this time it did print in grayscale, so I've got a sort of temporary fix. (I could've sworn I'd tried just removing the color cartridge before, but I've been out of town and had a week long gap in the middle of trying to troubleshoot this.)

I checked my ink levels before I pulled out the color cartridge, and it's showing cyan is out, magenta is almost out, and yellow is half down.

---

### Post by LaRoza on 2007-11-23
Well, I don't know what to do, but keep us posted, and I will let you know how my ink replacement goes when I do it on this thread.

---

### Post by FrozenFlame22 on 2007-11-23
Will do, and I appreciate your input! I've been wondering if this is a problem that is isolated to me and my system, or if it is more common.

---

### Post by LaRoza on 2007-11-23
> **FrozenFlame22 said:**
> Will do, and I appreciate your input! I've been wondering if this is a problem that is isolated to me and my system, or if it is more common.

No offense, but I hope it is just you....

---

### Post by FrozenFlame22 on 2007-11-23
:lol: None taken. ;)

---

### Post by Spaced on 2008-01-19
I have a similar problem: I've replaced the black ink cartridge, and I cannot print anything. I've removed the color cartridge to be sure... the printer works, but there's no ink on the page... the solutions proposed in this topic don't help me... what can I do? Other suggestions?

---

### Post by FrozenFlame22 on 2008-01-19
That's exactly what was happening with mine the first time I tried removing the color cartridge. Then I restarted the printer with only the black ink cartridge and it grudgingly printed in black. After a couple of weeks, I tried the color again and the ink had dried up, so I went and got a new color ink cartridge. After installing the color ink cartridge, the black and color started playing nice again.

I know this has no rhyme or reason. I really don't know how I got it working again, but there it is.

---

### Post by Xanderfoxx on 2008-01-19
I have an HP Deskjet F340 All-in-one myself, and here is what I would do (unless I'm corrected):

```

sudo apt-get install hplip

```

This may solve it. HP recommends this package, but you probably already have it, just an older version.

Hope it works out!:lolflag:

---

### Post by Spaced on 2008-01-21
> **maurin.alex@gmail.com said:**
> I have an HP Deskjet F340 All-in-one myself, and here is what I would do (unless I'm corrected):

```

sudo apt-get install hplip

```

This may solve it. HP recommends this package, but you probably already have it, just an older version.

Hope it works out!:lolflag:

Of course I have hplip installed on my computer... I also updated to the latest version, but nothing has changed...

The strange thing is that if I run 'hp-toolbox', it detects correctly the black cartridge, and prints the test page! But when I return to a document to print it, the printer gives me again the same result: a blank page... I'm getting confused... :confused:

---

