---
title: "Theme install on IceWM"
date: 2008-01-24
forum: General Help
---

### Post by Waelwulf on 2008-01-24
I'm having trouble using a theme I downloaded. I downloaded my IceWM theme from freshmeat: SpreadBuntu, and unpacked it. Then, in console I entered ```
sudo mv /home/user/Desktop/SpreadBuntu /home/user/.icewm/themes
```
But when I look in IceWM's Theme Manager, it doesn't show up, even after a restart. Can anyone provide some help?

---

### Post by aysiu on 2008-01-25
Any reason you used *sudo*?

You shouldn't need root permissions to move a theme into your own directory.

Maybe instead of using the console, you could just cut the unpacked theme with your mouse's right-click, and then paste it into ~/.icewm/themes

---

### Post by Waelwulf on 2008-01-25
Did exactly as you said. Still no luck. The Theme Manager is empty of the SpreadBuntu theme.

---

### Post by aysiu on 2008-01-25
Is it possible that SpreadBuntu is not an IceWM theme after all? Or that it is a poorly constructed theme? Do you have a link to it?

---

### Post by Waelwulf on 2008-01-25
Here you are: [http://themes.freshmeat.net/projects/spreadbuntu/](http://themes.freshmeat.net/projects/spreadbuntu/)

---

### Post by aysiu on 2008-01-25
> **Waelwulf said:**
> Here you are: [http://themes.freshmeat.net/projects/spreadbuntu/](http://themes.freshmeat.net/projects/spreadbuntu/)
That's weird. I tried it out on my Ubuntu's IceWM, and it worked fine.

Can you try copying and pasting these commands in the terminal? ```
cd ~/Desktop
wget -c http://themes.freshmeat.net/redir/spreadbuntu/70160/url_tgz/spreadbuntu-default-1.0.1.tar.gz
tar -xvzf spreadbuntu-default-1.0.1.tar.gz
mkdir ~/.icewm
mkdir ~/.icewm/themes
mv SpreadBuntu ~/.icewm/themes/
``` If the *mkdir* commands give you an error saying the folders already exist, that's okay. Just keep going.

---

### Post by Waelwulf on 2008-01-25
No luck. But I want to thank you for being so thoroughly helpful. It's an awesome community like this that makes me feel warm and fuzzy inside.

---

### Post by aysiu on 2008-01-25
Well, since you had used *sudo* earlier, it's possible that a change ownership might be preventing you from using the theme.

```
sudo chown -R *username:username* /home/*username*
``` where *username* is your actual username, should make sure that you have ownership of everything in your home directory.

After that, verify that Spreadbuntu exists as a folder inside /home/*username*/.icewm/themes and try again.

---

### Post by Waelwulf on 2008-01-26
Done, and yet more bad luck.

---

### Post by aysiu on 2008-01-26
Hm.

Can you try creating a test user, logging in as that test user, installing the theme, and picking the theme?

If it works for the test user, then we know it's a user-specific and not system-wide problem.

Also,  have you been able to successfully install other IceWM themes?

---

### Post by Waelwulf on 2008-01-26
I couldn't figure out how to create a new user but I did try and install the IceBuntu theme, which also didn't show up in the Theme Manager. By the way, I'm running Xandros: but I can't see that effecting a theme that only modifies IceWM right?

---

### Post by aysiu on 2008-01-27
> **Waelwulf said:**
> I couldn't figure out how to create a new user but I did try and install the IceBuntu theme, which also didn't show up in the Theme Manager. By the way, I'm running Xandros: but I can't see that effecting a theme that only modifies IceWM right?
As long as you're actually using *IceWM* on Xandros, it shouldn't matter. But I believe Xandros' default environment is KDE, so if you're using KDE, the IceWM themes won't show up.

You are definitely using IceWM, right?

---

### Post by conspirador on 2008-07-16
Hi everyone, I am new to the Linux Forums. I also have this problem and have been looking for a solution. Has anyone found a solution yet?
Id appreciate any help, thank you.

---

