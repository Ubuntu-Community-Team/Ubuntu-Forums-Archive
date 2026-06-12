---
title: "Print Server quick question"
date: 2007-02-25
forum: General Help
---

### Post by HW_Hack on 2007-02-25
I'm smack in the middle of writing our 07-08 budget / technology plan for a large Oregon high school -- so I'm just looking for some comments here not  full how to ...

As to network size - we're talking about 600 computers - 75% Mac - 25% XP


I'd like to install a color laser printer or 2 but I may also want a cheap way to control access to them or get reports as to whos printed the most jobs etc 

- Can a basic Ubuntu system be set up for this task ?

- Of course one big question is print drivers -- in this case for a new HP color laser -- not all 600 machines would need to print on these printers -- any ideas on how easily this is handled ?   


THANKS FOR YOUR TIME !!!!!

And yes getting Linux into the school is in the plan :-)

---

### Post by UltraMathMan on 2007-02-25
CUPS should be able to handle this, although I'd check to make sure like you said the print drivers work. I'm in the middle of setting up a print server for about 130 Macs, using Ubuntu Server with XFCE, although you could use a desktop install too. CUPS webadmin, accessed via ```
http://localhost:631
``` lets you view and manage jobs. For more information [check the wiki]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/cups.html") or [http://www.cups.org/]("http://www.cups.org/")

-Hope this helps :)

---

### Post by HW_Hack on 2007-02-26
Thanks - if you find a slick ( fast - painless) way to get the drivers setup please post a note:)

---

### Post by UltraMathMan on 2007-02-26
You could check [http://www.cups.org/ppd.php]("http://www.cups.org/ppd.php") to see if CUPS includes a print driver for the printer model(s) you have.

---

### Post by UltraMathMan on 2007-02-26
So I got the print server set up today, and successfully printed from the test Mac. [This Guide]("http://www.ubuntuforums.org/showthread.php?p=1831119") was helpful, something to bookmark for when configuring CUPS on your server.

---

