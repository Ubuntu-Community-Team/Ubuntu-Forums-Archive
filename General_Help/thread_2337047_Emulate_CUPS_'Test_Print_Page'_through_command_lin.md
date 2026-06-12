---
title: "Emulate CUPS 'Test Print Page' through command line."
date: 2016-09-13
forum: General Help
---

### Post by kwngeaw on 2016-09-13
Hi, is there a way I can emulate the function 'Test Print Page' through the command line (I really mean the real emulation)? I'm using ubuntu mate 16.04 on raspberry pi with bixolon srp-350ii thermal printer. Bixolon have only provided me with a partially function driver. It only can test print successfully and printing through other interfaces had failed. I've tried printing through lpr command. It print successfully only on the first time and after that, it will print something nonsense. It only become normal after I restarted the printer. I've told them about the driver's problem and it took them like forever to fix it. I'm using an application written with java to print. Therefore, I tried to overwrite the test-print.pdf file with files I want to print but I just don't know how to emulate test print through command line.

---

### Post by ian-weisser on 2016-09-15
You mean like the following?
```
lp -d my_printer_name /usr/share/cups/data/default-testpage.pdf
```

See 'man lp'

---

### Post by kwngeaw on 2016-09-19
> **ian-weisser said:**
> You mean like the following?
```
lp -d my_printer_name /usr/share/cups/data/default-testpage.pdf
```

See 'man lp'

Nope, it doesn't work.....

---

### Post by ian-weisser on 2016-09-19
That's a bit vague for us to help you with.

Does it return an error message?
Did you use your actual printer instead of 'my_printer_name'?
Is CUPS installed?
Does that file exist?
What does /var/log/cups/* say?

---

### Post by kwngeaw on 2016-09-19
> **ian-weisser said:**
> That's a bit vague for us to help you with.

Does it return an error message?
Did you use your actual printer instead of 'my_printer_name'?
Is CUPS installed?
Does that file exist?
What does /var/log/cups/* say?

Sorry, I also find it weird. There's no error at all. Just that I think the Bixolon SRP-350II thermal printer doesn't work along with the raspberry pi. I already type in the command correctly like [lp -d "SRP-350II" /home/kwngeaw/ha.pdf"] and it print out perfectly. Just that when I issue another print command, it will print out something nonsense. I need to keep on restarting (off & on) the printer for it to work correctly. The only way I can print out smoothly without restarting it is through CUPS test print. Therefore I want to emulate this test print so that I don't need to restart the printer.

---

