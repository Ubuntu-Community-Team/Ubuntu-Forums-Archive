---
title: "Can't Change Selected_bg"
date: 2016-04-29
forum: General Help
---

### Post by dannymichel on 2016-04-29
I've done exactly what this guy said here,
> The color code is #d64937

find "/usr/share/themes/Numix Daily/gtk-3.0" -type f -name '*.css' -print0 | xargs -0 grep 'd64937'
therefore you have to change two files:

sudo nano "/usr/share/themes/Numix Daily/gtk-3.0/gtk-dark.css"
sudo nano "/usr/share/themes/Numix Daily/gtk-3.0/gtk.css"
Search for

@define-color selected_bg_color #d64937;
And replace with

@define-color selected_bg_color #4A90D9;
Restart GNOME via Alt-F2 any type r isn't enough, logout and re-login.
 and there is no trace of the selected_bg orage color anywhere [http://askubuntu.com/questions/682708/how-to-set-a-custom-text-highlighting-colour](http://askubuntu.com/questions/682708/how-to-set-a-custom-text-highlighting-colour) but im still getting the same orange color as that guy. My modified theme -> <snip> . Any ideas?

---

### Post by vasa1 on 2016-04-29
> **dannymichel said:**
> I've done exactly what this guy said here, and there is no trace of the selected_bg orage color anywhere [http://bit.ly/1VYja7X](http://bit.ly/1VYja7X) but im still getting the same orange color as that guy. My modified -> [http://bit.ly/1VYja7X](http://bit.ly/1VYja7X) . Any ideas?

_Please_ edit your post to make "what this guy said here" clear. Which guy, where?

Also, p_lease_ replace the two *bit.ly* links with the full links.

Edit: You also may want to specify the Ubuntu flavor and its version in your user profile. The reason I'm mentioning this is that gtk3 themes are evolving; what was true some months ago may not apply now. If you're interested, take a look at [The Numix gtk theme in 16.04]("http://ubuntuforums.org/showthread.php?t=2322710").

Further edit: I downloaded and looked at your theme. It is in the newer format. That askubuntu answer won't apply, AFAIK.

Just to to let you know how things have changed:> For developers

**If you want to hack on the theme**, make sure you have the inotifywait command available, which is used for watching and automatically building the files.

To start watching for changes, run the following,

make watch

If you change any assets, you'll need to regenerate the gtk.gresource.xml and gtk.gresource files. You can use grrr to do it easily.Source [https://github.com/numixproject/numix-gtk-theme](https://github.com/numixproject/numix-gtk-theme)

---

