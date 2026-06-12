---
title: "I cannot reboot my computer, when i try to i only see a black screen"
date: 2020-06-10
forum: General Help
---

### Post by bhasvic on 2020-06-10
Today i installed Ubuntu 20.04 LTS to my computer with dual boot. I used Ubuntu for couple hours. But after that i closed my computer and did not use it for a few hours.Now when push my computer's power button, only thing that i see is black screen and i can not do anything. So even i can not reach my main OS (Windows 8.1) also i can not reach Bios and boot manager etc. I tried several times to open my computer but always i see the same thing. I guess i should use only Windows OS. So how can i reach my Windows and erase Ubuntu&Grub Menu?

---

### Post by GhX6GZMB on 2020-06-10
> **bhasvic said:**
> But after that i closed my computer and did not use it for a few hours.Now when push my computer's power button, only thing that i see is black screen and i can not do anything.

Is this a laptop? Does "closed my computer" mean you just closed the lid? In that case, charging the battery might work.

---

### Post by bhasvic on 2020-06-10
> **ml9104 said:**
> Is this a laptop? Does "closed my computer" mean you just closed the lid? In that case, charging the battery might work.
Thanks for your reply. Yes its a laptop(Lenovo G510) But i mean i "shut down" directly from the Ubuntu. Also i can see the computer is working(i can hear the fan sound) but screen is just black .

---

### Post by grahammechanical on 2020-06-10
Do you have the Lenovo instruction manual? Does it tell you about the novo button and its location? From a video I just watched about the G510 the novo button or pinhole is a small hole in the left side edge of the keyboard unit. Pushing somethiing into the hole will switch on the machine and allow you to enter the UEFI/BIOS.

[https://support.lenovo.com/gb/en/solutions/ht062552](https://support.lenovo.com/gb/en/solutions/ht062552)

A further question. When you installed Ubuntu did you install it in UEFI mode or legacy mode? If Windows is installed in UEFI mode then Ubuntu must be installed in UEFI mode. If Windows is installed in Legacy mode then Ubuntu must be installed in Legacy mode. Mixing the two modes could be what is causing this issue.

Regards

---

### Post by bhasvic on 2020-06-10
> **grahammechanical said:**
> Do you have the Lenovo instruction manual? Does it tell you about the novo button and its location? From a video I just watched about the G510 the novo button or pinhole is a small hole in the left side edge of the keyboard unit. Pushing somethiing into the hole will switch on the machine and allow you to enter the UEFI/BIOS.

[https://support.lenovo.com/gb/en/solutions/ht062552](https://support.lenovo.com/gb/en/solutions/ht062552)

A further question. When you installed Ubuntu did you install it in UEFI mode or legacy mode? If Windows is installed in UEFI mode then Ubuntu must be installed in UEFI mode. If Windows is installed in Legacy mode then Ubuntu must be installed in Legacy mode. Mixing the two modes could be what is causing this issue.

Regards

Thank you for your reply. I checked my computer computer and there is no pinhole . However i have Novo Button next to my power button. But when i push the novo button, nothing changes. unfortunately i cannot do because its still black screen.
For your second question, unfortunately  i did not know that. As far as i remember Windows is installed in UEFI mode but i dont know about legacy and UEFI mode in ubuntu.

---

### Post by CelticWarrior on 2020-06-11
If you can boot Windows from the Ubuntu's Grub menu then Ubuntu is as well installed in UEFI mode (as it should be).

Re: the black screen after waking up from suspension, first let's try to reboot it cleanly with the "magic sys request": Press and keep pressing ALT+Print Screen and then type in order R E I S U B. If it doesn't work then the only option is a forced shutdown: Pressing the power button until it shuts down.

Please post your hardware specifications so we can take a look and eventually figure out why suspension isn't working as it should.

---

### Post by bhasvic on 2020-06-11
> **CelticWarrior said:**
> If you can boot Windows from the Ubuntu's Grub menu then Ubuntu is as well installed in UEFI mode (as it should be).

Re: the black screen after waking up from suspension, first let's try to reboot it cleanly with the "magic sys request": Press and keep pressing ALT+Print Screen and then type in order R E I S U B. If it doesn't work then the only option is a forced shutdown: Pressing the power button until it shuts down.

Please post your hardware specifications so we can take a look and eventually figure out why suspension isn't working as it should.
I tried "magic sys request" but i guess it did not work or i could not do it properly. Here is the specs of my computer: Lenovo G510 Laptop
processor : i5-4200M
graphics adapter: intel hd graphics 4600 + amd r5m230
Memory: 4GB
mainboard: intel hm86
storage:1TB

---

### Post by CelticWarrior on 2020-06-11
Are you or are you not able to boot Windows from the same Grub menu? Or do you use UEFI ("BIOS") settings instead?

---

### Post by bhasvic on 2020-06-11
> **CelticWarrior said:**
> Are you or are you not able to boot Windows from the same Grub menu? Or do you use UEFI ("BIOS") settings instead?
Right now, i am not able to boot Windows. But[COLOR=#242729][FONT=Arial] during this problem, i would be able to reach the windows earlier. You can check this video about that.(Sorry this video's purpose was just sending to my friend so it is not well recorded) [/FONT][/COLOR][https://www.youtube.com/watch?v=zpNbuJMX9Mg&feature=youtu.be](https://www.youtube.com/watch?v=zpNbuJMX9Mg&feature=youtu.be) [COLOR=#242729][FONT=Arial]What i say in the video, when you push the power button the screen is just like that then i press two times down arrow and i press enter(Selecting Windows from the Grub Menu). After that Windows Login Menu came up. But unfortunately, the same thing does not work now. [/FONT][/COLOR]Also i did not understand your second question but fyi i can not reach BIOS either.

---

### Post by CelticWarrior on 2020-06-12
Your video shows Windows shutting down and then booting normally. No Grub menu to be seen. And you MUST be able to open UEFI settings (what you call "BIOS" but is actually UEFI).

---

