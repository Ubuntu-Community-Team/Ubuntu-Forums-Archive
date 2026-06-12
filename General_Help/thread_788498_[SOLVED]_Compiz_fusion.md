---
title: "[SOLVED] Compiz fusion????"
date: 2008-05-09
forum: General Help
---

### Post by hnlntm on 2008-05-09
Ok I'm new to Linux and thought ubuntu would be a good place to start it's installed and works a treat :) however I want use compiz fusion to spice up my desktop any help would be great. 

I've tried to configure the X11 file but I just started drowning in code:(:confused::(

---

### Post by evozniak on 2008-05-09
hi hnlntm, if you are using Hardy (8.04) do this.

Right click on desktop > preferences > visual efects > Advanced

this may help you, if not work install restricted driver of your graphic card, search on forum and see many guides to do this.

---

### Post by Exsecrabilus on 2008-05-09
Do you have your graphics driver enabled?

Go **System** >> **Administration** >> **Hardware Drivers**.

If it detected your graphics card, just click on the checkbox and you will get a choice whether or not to enable the graphics card.

Proceed and let it finish downloading the proper package to enable the driver.

If you're running Ubuntu 8.04 (Hardy Heron) effects should be enabled automatically after the above step.

Now go to Terminal and type:

```
sudo apt-get install compizconfig-settings-manager simple-ccsm
```

To change desktop effects settings, now go **System** >> **Preferences** >> **Advanced Desktop Effects Settings** or **System** >> **Preferences** >> **CompizConfig Settings Manager** or Alt+F2 and type in *ccsm*. For a simpler way, go **System** >> **Preferences** >> **Simple CompizConfig Settings Manager** or Alt+F2 and type in *simple-ccsm*.

---

### Post by hnlntm on 2008-05-09
Thanks both for you responce I have got the proprietary driver for my graphics card enabled.

and I've gone into system>preferences>appearance>visual effects is set to extra.

---

### Post by macaholic on 2008-05-09
> **hnlntm said:**
> Thanks both for you responce I have got the proprietary driver for my graphics card enabled.

and I've gone into system>preferences>appearance>visual effects is set to extra.
So is it working at the moment or not?

---

### Post by hnlntm on 2008-05-10
> **macaholic said:**
> So is it working at the moment or not?
this works fine (system>preferences>appearance>visual effects is set to extra)

but i want to add my own theames ....

what I'm not sure of is compiz built in or an addional piece of software (I'm guessing addional software),  how to install it if it is and how to add theames

---

### Post by Royke on 2008-05-10
Hello hnlntm, If i understand you correctly, you can just setup your desktop as desired and then use the theme-manager(gnome-appearance-properties that is build in) to save your themes. I hope this answers your question. (But i wander how you succeeded installing NVIDIA-drivers in Hardy Heron, i tryed many things with no success.)

---

### Post by hnlntm on 2008-05-10
> **Royke said:**
> Hello hnlntm, If i understand you correctly, you can just setup your desktop as desired and then use the theme-manager(gnome-appearance-properties that is build in) to save your themes. I hope this answers your question. (But i wander how you succeeded installing NVIDIA-drivers in Hardy Heron, i tryed many things with no success.)
when I enabled this ubuntu asked me if i wanted to install the driver...so i did?? system>preferences>appearance>visual effects is set to extra

where are the appearance properties the only properties I can find only offer basic fuctions... once i've downloaded a theame what do i do with it??

I can use the GUI but I am compleatly lost when using terminal.

Thanks again for any help you can offer

---

### Post by TobiDN on 2008-05-10
If you wan't to customize the way compiz-fusion acts, you should use add-remove, and install "cssm". With that tool you can customize it as you
want. If you want to change the look of the desktop menus, window decorations and so forth, you can use system>preferences>appearance,
and install new themes from there.

---

### Post by Zorael on 2008-05-10
> **TobiDN said:**
> If you wan't to customize the way compiz-fusion acts, you should use add-remove, and install "cssm".
As he said, but the package name is [FONT="Courier New"]compizconfig-settings-manager[/FONT] and the app itself is named [FONT="Courier New"]ccsm[/FONT]. :>

---

### Post by Exsecrabilus on 2008-05-10
If you guys read the above posts, he already installed *ccsm*.

He's asking how to use themes to change window borders, etc.

To **Hnlntm**, run this command:

```
sudo apt-get install emerald
```

Then to change window borders with compiz enabled, go **System** >> **Preferences** >> **Emerald Theme Manager** or Alt+F2 and type in *emerald-theme-manager*.

To change cursors, icons, or the style inside window borders, go **System** >> **Preferences** >> **Appearance** or Alt+F2 and type in *gnome-appearance-properties*.

Click **Install** and go to the .tar.gz file you have downloaded.

(If it's not a .tar.gz file, then try right clicking and do **Extract here**. Now click on the file created, right click and press **Create Archive...**. Change the extracted file type to .tar.gz and press **Create[**.)

After installation of the .tar.gz file, press **Customize** on whatever theme and find the theme you installed under whatever tab. Press it and the theme will change.


You should also try this if you already didn't:

```
sudo apt-get install fusion-icon
```

Now go to **Applications** >> **System Tools** >> **Fusion Icon** or Alt+F2 and type in *fusion-icon*.

Now an applet will appear on your panel.

Right click on it and you'll have a choice of choosing between Compiz and Metacity, GTK Window Decorator and Emerald.

That thing is useful for a lot of things so do this: (So it'll appear everytime you log in)

Go **System** >> **Preferences** >> **Sessions** or Alt+F2 and type in *gnome-session-properties*.

Click **Add** under the **Startup Programs** tab and enter a name for the applet.

For the **Command**, enter *fusion-icon*. Then click **OK**. There, you're set.

---

### Post by free2useemail on 2008-05-12
Well, you should be able to install it through the add remove programs screen. If not, then you will have to get it online. 

MAKE SURE YOUR GRAPHIC DRIVER IS CAPABLE OF THIS!

---

### Post by hnlntm on 2008-05-13
Thanks all This is now sorted

---

