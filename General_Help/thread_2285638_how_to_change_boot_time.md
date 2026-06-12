---
title: "how to change boot time ?"
date: 2015-07-07
forum: General Help
---

### Post by thomas52 on 2015-07-07
dear admin, i am using windows 7 32 bit and ubuntu 14.04.2 32 bit by dual booting my pc , while starting my computer and selecting the operating system to boot i only get a time limit of 7 seconds . i want to increase this time to 30 or 50 seconds can you please help me how should i make changes in this timer? thanks.

---

### Post by ajgreeny on 2015-07-07
See this long but very useful thread at [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

In the section on the /etc/default/grub file you will find this set of instructions for changing the timeout of the grub menu
> GRUB_TIMEOUT=10 - No change from Grub Legacy. This is the number of seconds before the default entry is automatically booted.

    Setting this value to -1 will cause the menu to display until the user makes a selection.
    To display the menu on each boot use a value of 1 or higher.
    This command defers to the GRUB_HIDDEN_TIMEOUT command. If the GRUB_HIDDEN_TIMEOUT option is interrupted by pressing the SHIFT key, the GRUB_TIMEOUT counter begins its countdown.
    Caution: Holding down the "SHIFT" key will not display the menu if "GRUB_TIMEOUT=" is set to "0" .
So set the value to -1 and it will wait for you to make a choice.

The **grub-customiser** package may also help you with this but I'm afraid I have never used it so I can not be sure about that.

---

### Post by Dennis N on 2015-07-07
> **thomas52 said:**
> dear admin, i am using windows 7 32 bit and ubuntu 14.04.2 32 bit by dual booting my pc , while starting my computer and selecting the operating system to boot i only get a time limit of 7 seconds . i want to increase this time to 30 or 50 seconds can you please help me how should i make changes in this timer? thanks.

Besides changing the time in /etc/default/grub, you can get all the time you want by hitting a key (like spacebar) before time runs out on the grub countdown. This will stop the count until you choose an option.

I prefer the -1 option though, as I often start the computer and walk away.

---

### Post by nerdtron on 2015-07-07
After modifying the /etc/default/grub file, don't forget to run update-grub to update your changes

```
kenneth@nerdtron:~$ grep -i grub_timeout /etc/default/grub 
GRUB_TIMEOUT=10
kenneth@nerdtron:~$ sudo update-grub

```

---

### Post by thomas52 on 2015-07-11
okay sir,thanks this was very helpful

---

