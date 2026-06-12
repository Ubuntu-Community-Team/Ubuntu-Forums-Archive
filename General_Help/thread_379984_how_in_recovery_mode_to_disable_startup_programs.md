---
title: "how in recovery mode to disable startup programs"
date: 2007-03-09
forum: General Help
---

### Post by bomoeller on 2007-03-09
Hi

I am linux NOOB - sorry so bear over with me. I have installed beryl and xgl but it did not work (i followed a guide...). Now I want to uninstall it all - so done... I thought... 
Apparantly my beryl-manager and beryl-xgl entry is still in my startup programs - I added to these in under gnome session under system/preferences/sessions. Know this means that I have a white cube that can rotate ... and I can not get to do anything - I understand that this is beryl... but can not get to any commands or anything. I want to remove those entries (beryl-manager and beryl-xgl). Can someone please tell me how to do that in recovery mode? I need a step by step guide please. What commands to use like LS nano and all that. Your help is greatly appreciated.

Cheers

---

### Post by Famicommie on 2007-03-09
Don't worry, no terminal work should be necessary, because there's an easier way :D

From the login screen, select the "Sessions" icon, and select "GNOME". From there, you should be able to log in to Ubuntu no problem and revert any changes that you've made to your sessions manager.

IF that doesn't work, then you need to do some commandline work. Boot in as normal, and look frustratedly at the screen. Then, type press alt+F2 and type 'gnome-terminal' That should give you a terminal ;)

Then simply type

rm ~/.config/autostart/beryl-manager.desktop

---

### Post by ~LoKe on 2007-03-09
Get rid of beryl-manager first so that it doesn't bug you (sometimes Beryl won't allow me to login, so I remove it completely before manually removing it from the session applications).
```
sudo dpkg -r beryl-manager
```
Then follow the post above.

---

### Post by bomoeller on 2007-03-09
Thanks for the reply guys but when i get the white-out cube from beryl I cant do anything... alt-f2 does not bring up the terminal. I guess I have to go through the recovery mode? Can you help me on what commands to use and how----- please :)

---

### Post by ~LoKe on 2007-03-09
Press **ctrl+alt+F1**.  Log in, then type this:
```
sudo dpkg -r beryl beryl-manager
```

---

### Post by bomoeller on 2007-03-09
thanks tried that. it said "ignoring request to remove beryl-manager which isn't installed".... no I am utterly confused. The white cube IS beryl. When rotating it I see the diamond. .... is the only option really reinstall?

---

### Post by ~LoKe on 2007-03-09
Try just this, then:
```
sudo dpkg -r beryl
```

---

### Post by Famicommie on 2007-03-09
go back to the console (ctrl+alt+F1), and type

```
cd .config/autostart/
```

What files are in that directory, if any?

What guide did you follow?

---

### Post by ~LoKe on 2007-03-09
Basically just give us the output of this:
```
ls ~/.config/autostart
```

---

### Post by Crooksey on 2007-03-09
Ctrl+Alt+F2

login

```

sudo aptitude remove beryl
```

---

### Post by bomoeller on 2007-03-09
again thx for your quick replies guys

done the aptitude and now in my autostart folder I have beryl-manager.desktop and beryl-xgl.desktop. What do I do with them?

---

### Post by Famicommie on 2007-03-09
rm ~/.config/autostart/beryl-manager.desktop

;)

---

### Post by bomoeller on 2007-03-09
Thx all for your help. I am up and running again. Learned a lot. 

Cheers

---

