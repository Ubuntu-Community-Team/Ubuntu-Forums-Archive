---
title: "I made the mistake of install kubuntu-desktop"
date: 2006-07-09
forum: General Help
---

### Post by jimmygoon on 2006-07-09
And now I don't like it, I just wanted to try kde. So now I want my default usplash back and my interface is all screwed up... like my buttons and stuff cause I was playing around with the options in KDE and now I can't change it back :(

How do I fix that stuff :( :(

---

### Post by -deadcats on 2006-07-09
Ooooh, you did that too? So did I; boy, whadda mess!

I used Synaptic and Apt to uninstall kubuntu-desktop, kdm, and most of the oither related stuff. I did, but my system was somewhat flaky. I never was able to get rid of the Kubuntu bootsplash. I finally gave up and reinstalled Ubuntu. That's what they make Live DVD's for, I guess.

"Never get out of the boat. Never get out of the boat." Lesson learned.

regards,
-dc

---

### Post by jimmygoon on 2006-07-09
NO! I just got done installing "The Slab" and AIGLX/Compiz (again)

---

### Post by Jucato on 2006-07-09
No need to reinstall. Just type this in the Terminal
```
sudo update-alternatives --config uspalsh-artwork.so
```
the name of the Ubuntu (brown) usplash is usplash-default.so

Hope that helps.

---

### Post by AirRaven on 2006-07-09
Do you mean your buttons in GNOME or KDE?

---

### Post by jimmygoon on 2006-07-09
I'm just gonna reinstall!

---

### Post by aysiu on 2006-07-09
You don't need to reinstall.

Just do this:
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

and then this:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

and next time, use *aptitude* instead of *apt-get* or Synaptic:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by Jucato on 2006-07-09
If you don't want to remove kubuntu-desktop but still retain the Human theme (or any other GNOME theme) of GNOME, you can just do this. It's a little trick I realized while playing around with GNOME installed over Kubuntu. You might not want to do this (you might want to uninstall kubuntu-desktop) but I'm just sharing this for those interested.

1. Either from GNOME or KDE, press Alt+F2 to launch the Run Command box and type in this command:
```
kcmshell kcmgtk-xdg
```
A dialog box will appear.
2. Under the GTK Styles group, choose "Use another style" and 
look for Human (or your theme of choice) from the dropdown box beside it.
3. For the GTK Fonts, choose "Use another font" and click on Choose to change to the font of your choice. The default fonts for the Human theme is Serif size 10.
4. Click on Apply after you're done.

The long winded explanation: kcmshell kcmgtk-xdg is KDE's Control module for defining how GTK apps (meaning GNOME/Xfce apps) will appear in KDE. It seems that once you install KDE over GNOME or vice-versa, this part of KDE and GNOME's own theme manager conflict with each other. I don't know why, and I don't know which one the system obeys more. Choosing a GTK style in KDE that matches the theme in GNOME will make sure that your Ubuntu/GNOME desktop will have the consistent GNOME look.

... and KDE will still look like KDE.

---

### Post by jimmygoon on 2006-07-09
> **Fenyx said:**
> If you don't want to remove kubuntu-desktop but still retain the Human theme (or any other GNOME theme) of GNOME, you can just do this. It's a little trick I realized while playing around with GNOME installed over Kubuntu. You might not want to do this (you might want to uninstall kubuntu-desktop) but I'm just sharing this for those interested.

1. Either from GNOME or KDE, press Alt+F2 to launch the Run Command box and type in this command:
```
kcmshell kcmgtk-xdg
```
A dialog box will appear.
2. Under the GTK Styles group, choose "Use another style" and 
look for Human (or your theme of choice) from the dropdown box beside it.
3. For the GTK Fonts, choose "Use another font" and click on Choose to change to the font of your choice. The default fonts for the Human theme is Serif size 10.
4. Click on Apply after you're done.

The long winded explanation: kcmshell kcmgtk-xdg is KDE's Control module for defining how GTK apps (meaning GNOME/Xfce apps) will appear in KDE. It seems that once you install KDE over GNOME or vice-versa, this part of KDE and GNOME's own theme manager conflict with each other. I don't know why, and I don't know which one the system obeys more. Choosing a GTK style in KDE that matches the theme in GNOME will make sure that your Ubuntu/GNOME desktop will have the consistent GNOME look.

... and KDE will still look like KDE.

too late. thanks but I've already got it up and running with my aiglx+apps+slug but thanks a bunch anyways :)

---

### Post by hanzomon4 on 2006-07-10
> **jimmygoon said:**
> I'm just gonna reinstall!

You really don't have to reinstall, follow the links given by aysiu.

When I first started using ubuntu every time I would break something I would reinstall, but you don't learn anything that way.

Now if I break something I "fix it" and the things I learn make using ubuntu a lot easier and more enjoyable.

---

### Post by Jucato on 2006-07-10
> **hanzomon4 said:**
> You really don't have to reinstall, follow the links given by aysiu.

When I first started using ubuntu every time I would break something I would reinstall, but you don't learn anything that way.

Now if I break something I "fix it" and the things I learn make using ubuntu a lot easier and more enjoyable.

Too late. I think he already did reinstall. :D

---

