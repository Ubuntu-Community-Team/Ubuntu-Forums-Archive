---
title: "Gnome tweaks Shell has exclamation point"
date: 2021-07-24
forum: General Help
---

### Post by dora5 on 2021-07-24
I just upgraded to 20.04, and in Gnome Tweaks, Shell has no options but shows a black triangle with an exclamation point.  See screenshot.   What is the reason and how do I fix it?

Thanks!

Dora Smith

---

### Post by dora5 on 2021-07-24
Never mind.  I found the answer.  Something about enable themes.

---

### Post by walts48 on 2021-07-25
> **dora5 said:**
> Never mind.  I found the answer.  Something about enable themes.

I have the same issue.

How is that done?

---

### Post by TheFu on 2021-07-25
My first thought was that gnome tweaks isn't part of the core repositories, so with the upgrade, the old version would be removed, but the .desktop file would be left.  That would leave a menu item, but no program.  Since the old PPAs are disabled during the upgrade process, re-adding the PPA where gnome-tweaks is released, doing an 
```
sudo apt update
sudo apt install gnome-tweaks
```
Would be needed to get the newer version for the current release.

Anyway, that was my initial thought. Guess I was wrong.

I've never used gnome-tweaks.

---

### Post by tea for one on 2021-07-25
> **walts48 said:**
> I have the same issue.

How is that done?

Have you downloaded a GTK theme, which includes the necessary software for gnome-shell theming.
Some themes are only gnome-shell, some are system wide including gnome-shell.
For example, here is one that is system-wide [https://www.gnome-look.org/p/1299514](https://www.gnome-look.org/p/1299514)

---

### Post by deadflowr on 2021-07-25
Enable user themes.
Install the user themes extension if not already installed, which is included in the package gnome-shell-extensions.

---

### Post by walts48 on 2021-07-26
> **tea for one said:**
> Have you downloaded a GTK theme, which includes the necessary software for gnome-shell theming.
Some themes are only gnome-shell, some are system wide including gnome-shell.
For example, here is one that is system-wide [https://www.gnome-look.org/p/1299514](https://www.gnome-look.org/p/1299514)

I guess I don't understand what a gnome-shell is.

I thought it was installed as the shell Gnome is built on.

Might try checking out themes someday.

I am using Adwaita-dark here.

---

### Post by tea for one on 2021-07-26
> **walts48 said:**
> I guess I don't understand what a gnome-shell is.

I thought it was installed as the shell Gnome is built on.

Might try checking out themes someday.

I am using Adwaita-dark here.

Gnome-shell is installed together with the Adwaita theme.

Gnome-shell themes (as well as system-wide GTK themes) simply change the appearance.

E.g. Adwaita has a blue highlight but you may want red, therefore you explore themes and install a theme which you find pleasing to the eye.

---

### Post by walts48 on 2021-07-27
Then why am I seeing an exclamation point?

---

### Post by deadflowr on 2021-07-27
> **walts48 said:**
> Then why am I seeing an exclamation point?

I posted the answer.
But you may need to close and reopen Tweaks.

Note that the shell theme in Ubuntu is Yaru by default and has no relation to whatever the gtk or application theme may be.
Generally it's semi-hard-coded. I say semi as the shell theme is a compiled binary gresource file.
So to change it you need to recompile a new one.
Or...
You use the User Themes extension which allows you to set your own theme without the recompiling hassle.
The User Themes extension is a Gnome developers created extension, so safe to use.

---

### Post by tea for one on 2021-07-27
> **walts48 said:**
> Then why am I seeing an exclamation point?

As deadflowr previously mentioned:-

Open gnome-tweaks > Extensions > User Themes > Activate

You still have to have themes which include gnome-shell configuration folder in ~/.themes or /usr/share/themes

---

### Post by Dennis N on 2021-07-27
If you are interested in exploring different gnome-shell themes, the place most people get them is gnome-look.org where they currenty have 467 gnome-shell themes. The version of the theme you choose should be made for the version of gnome shell you have. For example, Ubuntu 20.04 needs a theme made for gnome-shell 3.36, which not the latest gnome-shell version.

[FONT=Courier New]dmn@Sydney-vm:~$ gnome-shell --version
GNOME Shell 3.36.9[/FONT]

---

### Post by dora5 on 2021-07-28
Ha, ha, I actually thought that was enough information.  I thought it would get an appropriate snort at my silly question.   

First to do any of it you have to install gnome-tweaks, it doesn't come on your system. 

I THINK that's sudo apt-get install gnome-tweaks

So to be able to add a shell you have to add the ability to do that.   Click on Extensions, and turn on "User themes" - "Load shell themes from user directory".  

Then you can change the shell. 

It's needlessly complicated and not something one would intuitively think of.  I feel better now that I'm not the only one who didn't think of it.

---

### Post by walts48 on 2021-07-31
> **dora5 said:**
> Ha, ha, I actually thought that was enough information.  I thought it would get an appropriate snort at my silly question.   

First to do any of it you have to install gnome-tweaks, it doesn't come on your system. 

I THINK that's sudo apt-get install gnome-tweaks

So to be able to add a shell you have to add the ability to do that.   Click on Extensions, and turn on "User themes" - "Load shell themes from user directory".  

Then you can change the shell. 

It's needlessly complicated and not something one would intuitively think of.  I feel better now that I'm not the only one who didn't think of it.

Agreed, indeed.

Nice to know our systems aren't broken, and we don't need a shell.

---

