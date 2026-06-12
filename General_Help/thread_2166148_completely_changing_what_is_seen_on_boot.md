---
title: "completely changing what is seen on boot"
date: 2013-08-07
forum: General Help
---

### Post by physman2 on 2013-08-07
So I have lubuntu and xfce and when I start up my laptop (I'm not dual booting) it loads and then asks me to sign in and has a nice looking login screen. The thing is, I don't really want the nice login screen, I want the start up to be as quick and "lightweight" as possible. I want it to just start up in say the command prompt, prompting me for a password and that's it, something very simple. How would I go about doing so? I'm guessing I would have to change grub settings? Is there a textbook which I can read or a tutorial which teaches me how to edit the "backeend" of Linux and like the start up process and what not?

---

### Post by Cheesemill on 2013-08-08
To stop the display manager from loading so that you get a CLI login run the following command...
```
echo "manual" | sudo tee -a /etc/init/lightdm.override
```

Once you are logged in you can start the GUI by running...
```
startx
```

---

