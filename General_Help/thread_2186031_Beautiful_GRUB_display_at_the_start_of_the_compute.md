---
title: "Beautiful GRUB display at the start of the computer"
date: 2013-11-05
forum: General Help
---

### Post by Gins on 2013-11-05
In my old Linux versions, I had a beautiful GRUB display on the screen. I could select other Linux flavours. I have Ubuntu 12.04 is the default version, nowadays.
I don't get that display when starting the computer. I see some lines in very small letters. I could select other versions, however.

How do I get the nice display of GRUB when starting the computer?
Your thoughts are welcome.

---

### Post by Buntu Bunny on 2013-11-05
You should still be able to select whatever Linux flavors you have installed, but I agree Grub is hardly aesthetic. You might try the suggestions in this article, [Make your Grub boot menu pretty.]("https://sites.google.com/site/easylinuxtipsproject/beautifygrub")

---

### Post by jamesisin on 2013-11-05
What was the old Linux version you were using?

---

### Post by Bashing-om on 2013-11-05
Gins; Hi !

I like Cavsfan's tutorial to have the boot menu set up as well as pretty pictures:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

[INDENT][INDENT]works great for me
[/INDENT][/INDENT]

---

### Post by oldos2er on 2013-11-05
> **Gins said:**
> How do I get the nice display of GRUB when starting the computer?

```
sudo apt-get update && sudo apt-get install kde-config-grub2
``` Now open System Settings, Startup and Shutdown, and you'll see a nice GUI way to configure grub2 to your heart's content.

---

### Post by SeijiSensei on 2013-11-05
> **oldos2er said:**
> ```
sudo apt-get update && sudo apt-get install kde-config-grub2
``` Now open System Settings, Startup and Shutdown, and you'll see a nice GUI way to configure grub2 to your heart's content.

Cool! Thanks.

---

### Post by Gins on 2013-11-07
Thanks everybody for the excellent replies.
Nowadays, I have little time to deal with these configuration related matters.

However, I had time to try the following suggestion:
sudo apt-get update && sudo apt-get install kde-config-grub2
**[ It worked fine. I mean it downloaded the stuff from the repositories. However, in System Settings, I could not find Startup and Shudown. Why is this? ]**
Maybe, my version of Ubuntu doesn't support these changes. I have a desktop computer and uses Ubuntu 12.04 LTS

---

### Post by oldos2er on 2013-11-07
So you're using Ubuntu, not Kubuntu? I'm a bit confused since you tagged the thread 'Kubuntu'.

---

### Post by Gins on 2013-11-08
Thanks oldos2er for the comments.
How do I find out whether I have Kubuntu?

---

### Post by SeijiSensei on 2013-11-08
Try this:

```

$ cd 
$ ls .kde

```

If you do not have a .kde directory, then you are not running Kubuntu.  

If the panel is at the bottom of the screen, and the menu button on the left of the panel has a big "K" on it, then you are running Kubuntu.

---

### Post by Gins on 2013-11-08
T

Thanks for the reply.
I didn't get any .kde directory.
On the left side, there is a panel. It is a vertical panel. I can see all my programs. However, there is not big 'K'.

---

### Post by oldos2er on 2013-11-08
That's Unity, the default version of Ubuntu, not Kubuntu. kde-config-grub2 won't work on non-KDE systems. Instead try [grub-customizer]("https://launchpad.net/grub-customizer").

Edit: Changed thread prefix to Ubuntu.

---

### Post by Gins on 2013-11-08
Thanks for the reply.
What is the difference between Ubuntu and Kubuntu?
I know Kubuntu uses KDE interface. It is my guess that Ubuntu uses GNOME interface.
I am not sure. Please tell me.

---

### Post by oldos2er on 2013-11-08
Ubuntu uses Unity, and I believe there's some Gnome and Compiz thrown in too. I don't use it so I don't really know much about it.

[https://en.wikipedia.org/wiki/Unity_%28user_interface%29](https://en.wikipedia.org/wiki/Unity_%28user_interface%29)

---

### Post by jamesisin on 2013-11-08
Unity is currently built on Gnome3.  Historically Ubuntu has been a Gnome distribution and Kubuntu a KDE distribution.

---

### Post by Gins on 2013-11-09
Thanks for the replies.
Do you think Kubuntu is a better product and Ubuntu is an inferior product?

---

### Post by SeijiSensei on 2013-11-09
I wouldn't go that far. GNOME derivatives tend to offer fewer configuration options to the user.  KDE lets you customize pretty much everything about your desktop.  

If you want to see KDE in action, boot from the [Kubuntu installation image]("http://cdimage.ubuntu.com/kubuntu/releases/13.10/release/") and choose "Try Ubuntu" when offered.  It will make no changes to your machine.

---

### Post by mcduck on 2013-11-10
Choise between Unity, KDE, and any other desktop or window manager is pretty much a question of personal preference, not one being better than others.

Anyway, Grub2 can do quite a bit more than just background pictures and colors, there are surprisingly few good themes available but this is the one I'm using: [http://gnome-look.org/content/show.php/Axiom+Grub+2+Theme?content=146396]("http://gnome-look.org/content/show.php/Axiom+Grub+2+Theme?content=146396"). Fairly simple one but most of the others I've found have branding for some other Linux distributions (and I quite like the clean & simple look anyway)...

---

