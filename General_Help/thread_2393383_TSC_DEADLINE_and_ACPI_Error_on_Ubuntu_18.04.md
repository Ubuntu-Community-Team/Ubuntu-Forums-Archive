---
title: "TSC_DEADLINE and ACPI Error on Ubuntu 18.04"
date: 2018-06-02
forum: General Help
---

### Post by hasquitor on 2018-06-02
[IMG]https://imgur.com/a/WNsnI2i[/IMG]Hey guys. I really need some help. I upgrade my Ubuntu from 16.04 to 18.04, 2 weeks ago. It was having no problems at all, but today, after restart my Notebook(Lenovo G40-80) this error ocurred: [IMG]https://imgur.com/a/WNsnI2i[/IMG]https://imgur.com/a/WNsnI2i i can't boot the Ubuntu, everytime this happens. I tried to update the microcode but I don't know if i'm doing wrong, but can't conect to wifi or cable from the terminal. I saw some foruns about this but all they said it was on Ubuntu 7.10, and that it was fixed. I tried to make a clean install of 18.04 either, but didn't fixed. So, I really need my notebook but I'm getting out of ideas, any tip? And I'm so sorry about my English, I know It sucks, doing my best :/

---

### Post by hasquitor on 2018-06-03
So, I made it to connect to a WEP and updated microcode. The first error is gone but I still can't boot 'cause of the ACPI errors. But when I try to boot in recovery mode I can get to the login screen, but after I put my password the screen turns black and gets back to the login screen.

So, I heard about the ACPI=off but I guess I'm doing it wrong because it didn't do anything in this case. How to use this right?

---

### Post by #&amp;thj^% on 2018-06-03
See if you can follow this link to add "acpi=off" at grub.
[https://askubuntu.com/questions/160036/how-do-i-disable-acpi-when-booting/160056](https://askubuntu.com/questions/160036/how-do-i-disable-acpi-when-booting/160056)
The thread with the green check mark.
And make sure it reads like:
```
Change line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
```
But I hesitate to say that will solve your login bounce. :(
If you make this change permanent it will break your window's boot option if you are dual booting with windows.

---

