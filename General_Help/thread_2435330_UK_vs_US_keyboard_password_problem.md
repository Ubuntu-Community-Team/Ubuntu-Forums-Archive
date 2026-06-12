---
title: "UK vs US keyboard password problem"
date: 2020-01-19
forum: General Help
---

### Post by ikerrin1 on 2020-01-19
Hi, 

I'm hoping someone can help me here. When I set up my new Ubuntu XPS from Dell, I choose the uk keyboard assuming it was the same at the US standard one. After a while I realized that all the weird characters I was getter were the result of my UK keyboard so I set it back to the US. Then the next time I tried to log in, it would't accept my password. I think this is because I thought my password had a ~ symbol, but since it was a UK keyboard setting, it would instead read the [¬]("https://en.wikipedia.org/wiki/%C2%AC") symbol. So, now my password doesn't work.

Not a problem, I thought, I'll just type in the unicode symbol for [¬]("https://en.wikipedia.org/wiki/%C2%AC") "ctrl shift U 00AC" but, the computer still won't accept my password.  What am I doing wrong?

Thanks,

Greg

---

### Post by CatKiller on 2020-01-19
Rather than getting into a muddle with locales and keyboard layouts, you could boot into recovery mode and temporarily change the password to something without symbols. Then you can log in normally and change the password to whatever you want, with symbols you can actually type.

---

### Post by ikerrin1 on 2020-01-19
Thanks for the reply, I just get a <grub> prompt when I do that.

---

### Post by ikerrin1 on 2020-01-19
Ok, I got to the BIOS by pressing F2 but didn't see anything to help me change the password.

---

### Post by Impavidus on 2020-01-20
Don't go into the bios/uefi. The grub menu come after that. Can you see it? Best to keep the grub menu enabled at all times, even if you rarely need it, but on single boot systems the installer automatically disables the grub menu, so it's a bit tricky to get into it. Hit shift or escape (I think one of those should work) right after that screen with your computer's brand's logo to open the menu. The menu should have a line with advanced options, then try recovery mode. If you get a grub prompt when you try to use the menu, there's something wrong.

Alternatively, you could try the on-screen keyboard. At the login screen, there's a button to open an on-screen keyboard. I never tried it, but you may be able to choose keyboard layout there.

---

### Post by ikerrin1 on 2020-01-20
Hi Catkiller and Impavidus. The challenge was that I was pressing and holding <esc> and going straight to the grub command line. I should have just pressed it once and quickly after the Dell sign came up. After doing that I got into the Ubuntu advanced boot menu. The following website guided me the rest of the way. It was the Dell support guy who was able to walk me through it to change my password as root. Yay for helpdesk support with the XPS and Dell. Totally worth the price. I appreciate both your efforts to help out.

[https://websiteforstudents.com/reset-forgotten-ubuntu-user-password-on-ubuntu-16-04-17-10-18-04/](https://websiteforstudents.com/reset-forgotten-ubuntu-user-password-on-ubuntu-16-04-17-10-18-04/)

---

### Post by Impavidus on 2020-01-21
Although I rarely need the grub menu, I keep it enabled anyway because it can be a real problem if you need it and can't get it. I have the grub menu show for only 3 seconds before booting the default entry. To enable the grub menu, edit /etc/default/grub, set GRUB_TIMEOUT to a small positive number (I use 3, for 3 seconds) and run sudo update-grub.

Can you mark this thread as solved? Thread tools &#8594; mark as solved.

---

