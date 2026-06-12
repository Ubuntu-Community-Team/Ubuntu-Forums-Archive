---
title: "Question about Htop."
date: 2018-05-30
forum: General Help
---

### Post by mrazster on 2018-05-30
Not sure if it's the appropriate section of the forum to ask this...if not then feel free to move it.

I have a question about using Htop !

I have googled it and read thru the manpages and also looked in the configfiles...but have yet to find a clear answer.

In the Gnome DE, when I click on the icon I would like Htop as default to automaticlly open on "Desktop 2" and in fullscreen.
Is it possible and how would that startupcommand look like ?

I have something like an executable bashscript or something along thoose lines, in mind.
*(I know to make the bashscript e.t.c...it's just the htop "start command" I can't figure out.)*

Thanx in advance ! :-) <3

---

### Post by deadflowr on 2018-05-30
You can install gnome-tweaks and enable and set auto-move-windows, which will allow you to place apps to always open in certain desktop workspaces.
If auto move windows ins't already installed you can either grab it from the Ubuntu packaged version
```
sudo apt install gnome-shell-extensions
```
this will add a whole array of extensions, inlcuding auto-move-windows.
or grab it from the web site here:
[https://extensions.gnome.org/extension/16/auto-move-windows/]("https://extensions.gnome.org/extension/16/auto-move-windows/")

And you can try installing the extension linked here:
[https://ubuntuforums.org/showthread.php?t=2392116&p=13771662#post13771662]("https://ubuntuforums.org/showthread.php?t=2392116&p=13771662#post13771662")
Abotu trying to open apps in max screen.

*Unless you only want one app to open maxed.
Then there is probably a different method to do so.

---

