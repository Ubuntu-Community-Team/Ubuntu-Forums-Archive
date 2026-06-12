---
title: "MATE Calculator is too small, how do I enlarge it?"
date: 2021-09-08
forum: General Help
---

### Post by ardouronerous on 2021-09-08
Running Xubuntu 20.04 and this is how MATE Calculator looks like, it's too small for my eyes and to use for calculating my financials.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289146&stc=1[/IMG]
Is there a way to enlarge this? If not, can one recommend a calculator with a bigger UI? Thanks.

---

### Post by monkeybrain20122 on 2021-09-08
I don't use Mate and don't have mate calculator, it may have a config file where you can set the size. Look among the hidden files (those that start with a dot "." ) in  your home directory and look inside .config.

---

### Post by ardouronerous on 2021-09-08
> **monkeybrain20122 said:**
> I don't use Mate and don't have mate calculator, it may have a config file where you can set the size. Look among the hidden files (those that start with a dot "." ) in  your home directory and look inside .config.

No config files for MATE Calculator. There's a [FONT=courier new]/.config/mate/[/FONT] but the only config file there is for mate-dictionary, I even searched for calculator with Catfish, no config files for MATE Calculator found.

---

### Post by mikewhatever on 2021-09-08
This is the Basic mode. If you click Mode->Advinced, the calculator window becomes bigger with more keys and functions.

---

### Post by ardouronerous on 2021-09-08
> **mikewhatever said:**
> This is the Basic mode. If you click Mode->Advinced, the calculator window becomes bigger with more keys and functions.

I've tried that already, the UI is still too small for me and the extra keys and functions just confuses me. Is there another calculator application with a bigger UI in basic mode?

---

### Post by Dennis N on 2021-09-08
> **ardouronerous said:**
> I've tried that already, the UI is still too small for me and the extra keys and functions just confuses me. Is there another calculator application with a bigger UI in basic mode?
There are large-size online calculator at:
[https://www.online-calculator.com/full-screen-calculator/](https://www.online-calculator.com/full-screen-calculator/)

---

### Post by ardouronerous on 2021-09-08
> **Dennis N said:**
> There are large-size online calculator at:
[https://www.online-calculator.com/full-screen-calculator/](https://www.online-calculator.com/full-screen-calculator/)

Thanks, this would do nicely for now, but still, I still wished there was a offline calculator with a bigger basic UI.

---

### Post by mikewhatever on 2021-09-08
> **ardouronerous said:**
> I've tried that already, the UI is still too small for me and the extra keys and functions just confuses me. Is there another calculator application with a bigger UI in basic mode?

I don't know if there is a basic calculator with huge oversized buttons. You might need to do a bit of homework on that.
There are many calculators in the repositories, but from what I've seen, people hate oversized design on their desktops with passion, and tend to trough major temper tantrums over it.

---

### Post by sudodus on 2021-09-08
Try **galculator**. I have version 2.1.4 from the repo universe, and I can change size of buttons and fonts (and the total size of the window will fit.

Edit: See the attached screenshot.

---

### Post by dragonfly41 on 2021-09-08
If you install Albert and just enable Calculator extension it is a very simple interface.
I have set the hot key to be NumEnter (the key at bottom right of my keyboard, next to num keypad).

Of course Albert has many other uses.

---

### Post by ardouronerous on 2021-09-08
> **sudodus said:**
> Try **galculator**. I have version 2.1.4 from the repo universe, and I can change size of buttons and fonts (and the total size of the window will fit.

Edit: See the attached screenshot.

Thank you so much. galculator is very customizable and you can edit the window size and the font size, so it's perfect for my eyes.

The default maximum window size is 100x100, but I was able to get past that by editing the **galculator.conf** file.

> **mikewhatever said:**
> what I've seen, people hate oversized design on their desktops with passion, and tend to trough major temper tantrums over it.

In my case, my eyes aren't what they used to be and so I need a calculator with a bigger window and font size, and galculator does the trick.

---

### Post by ardouronerous on 2021-09-08
> **sudodus said:**
> Try **galculator**. I have version  2.1.4 from the repo universe, and I can change size of buttons and fonts  (and the total size of the window will fit.

Edit: See the attached screenshot.

Thank you so much. galculator is very customizable and you can edit the  window size and the font size, so it's perfect for my eyes.

The default maximum window size is 100x100, but I was able to get past that by editing the **galculator.conf** file.

> **mikewhatever said:**
> what  I've seen, people hate oversized design on their desktops with passion,  and tend to trough major temper tantrums over it.

In my  case, my eyes aren't what they used to be and so I need a calculator  with a bigger window and font size, and galculator does the trick.

---

### Post by monkeybrain20122 on 2021-09-08
How about [qalculate]("http://qalculate.github.io/")?

Looks pretty cool, both qalculate and qalculate-gtk are in the repo, since you are on xubuntu you should get the gtk version.

---

### Post by Paulgirardin on 2021-09-19
I second qalculate - you can change the font size and make the window any size you want - the buttons expand with the window.
It also has a full range of financial functions as well as every other function you might need.

I use it in history mode ,where buttons are not displayed and the keyboard is used to input data and previous calculations are listed below the current calculation

---

