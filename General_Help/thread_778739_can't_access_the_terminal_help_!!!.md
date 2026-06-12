---
title: "can't access the terminal help !!!"
date: 2008-05-02
forum: General Help
---

### Post by AgentZ86 on 2008-05-02
Hi all

I installed Ubuntu 7.10 and it worked perfectly, 
I setup the login page to login automatically, and then did an upgrade, now the screen is funny looking like the resolution or frequency is wrong, I can't see the screen to fix anything and I can't select any options on the login windows because it logs me in automatically, 

How do I get to the terminal at this point, and what commmand do I use to change the screen resolution from there ????

Please help thanks

---

### Post by TeoBigusGeekus on 2008-05-02
Boot up into recovery mode with grub and type
```
sudo [COLOR="Red"]dpkg[/COLOR]-reconfigure -phigh xserver-xorg
```
to reconfigure your display settings.

---

### Post by AgentZ86 on 2008-05-02
> **TeoBigusGeekus said:**
> Boot up into recovery mode with grub and type
```
sudo [COLOR="Red"]dpkg[/COLOR]-reconfigure -phigh xserver-xorg
```
to reconfigure your display settings.

this is excellent, but this is the problem,
How do I get to recovery mode, if I don't get the login screen it just boots up to the gui automatically ?

There is no options button that you would normally get on the login screen because it just bye passes all that and boots to the gui ? 
Is there some shortcut key I can hit to go into reconfigure etc  ? 

I'm sure that the system fully boots to ubuntu gui, and is on at the desktop automatically but I just can't see it because of the settings foul up.

Thanks

---

### Post by TeoBigusGeekus on 2008-05-02
Don't you have grub?

---

### Post by AgentZ86 on 2008-05-02
I see in grub, sorry about that

Thanks

---

