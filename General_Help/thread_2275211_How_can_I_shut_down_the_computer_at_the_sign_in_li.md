---
title: "How can I shut down the computer at the sign in line?"
date: 2015-04-24
forum: General Help
---

### Post by ross4 on 2015-04-24
I'm playing around with different live versions of Linux and I regularly get to a point where I have turned on or re-booted the machine and realize it is not doing what I want, for example it's booting from the hard drive and not from the USB or CD, or I've forgotten to put in/take out the correct USB or CD. When this happens I would like to shut down the machine as quickly as possible so I can start again. I was wondering if there is some way to shut it down when the sign-in screen comes up rather than signing in, waiting for a minute and then shutting down.

Ideally I'd like to shut it down even before I get to the sign-in screen but my guess is that this is not possible without causing some kind of problem.
Regards,
Ross

---

### Post by Dennis N on 2015-04-24
Yes you can shut down or restart from the "sign-in" window (also called login screen). That screen has a panel with some icons on it -  one of them is for shutdown or restart without signing in.

---

### Post by Bashing-om on 2015-04-24
ross4; Hey;

On my box I have the key combo ctl+alt+del mapped to "shutdown -r now" . It does function from  almost any point after the system begins loading.
Do you have this file :
```

cat /etc/init/control-alt-delete.conf

```

[INDENT][INDENT]sometime it is as handy
[INDENT][INDENT][INDENT]as a pocket on a shirt
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ross4 on 2015-04-24
Thanks to both of you. 
Dennis, yes, there it was in front of my face. Obviously too much of a hurry to read the screen. Actually, have to press Alt-F4 to execute it. Thanks again.
Bashing-om, yes, I have that file. Does it shut down or re-boot? It seems to say it reboots.
Ross

---

### Post by oldfred on 2015-04-24
I often have same issue, and added entries to grub's 40_custom. So if you realize it at grub menu you can reboot.
       gksudo gedit /etc/grub.d/40_custom
            sudo update-grub
           ```

 # spacer line
menuentry " " {
set root= 
}

   menuentry "System restart" {
    echo "System rebooting..."
    insmod reboot
    reboot
  }    
  
 menuentry "System shutdown" {
  echo "System shutting down..."
         insmod halt
         halt
  }

```

---

### Post by Bashing-om on 2015-04-25
@ross4; Yeah;

With that config :
> 
Does it shut down or re-boot? It seems to say it reboots.

it does reboot. I have not tested but maybe if the 'r' option were changed to 'h' then the system would (H)alt .

@oldfred ; Wonderful.

Another tool to put in the tool box.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]many paths to an end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ross4 on 2015-04-25
Bashing-om: Ok, It looks as though changing r to h or H will do what I want. I'll check out these options.

oldfred: I'll try this out too. It looks very helpful.

Thanks to everyone. I'll mark this as solved.

---

### Post by Bashing-om on 2015-04-25
ross4; Great;

Pleased it works out.

[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

---

### Post by sammiev on 2015-04-25
I have my power button map to shut down my computer with a quick tap. I never tried it from the log in screen but will try on next reboot.

Edit: It works with the power button mapped to shut down on a quick tap.

---

