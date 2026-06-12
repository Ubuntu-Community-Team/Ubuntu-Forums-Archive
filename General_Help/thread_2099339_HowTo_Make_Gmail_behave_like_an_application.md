---
title: "HowTo: Make Gmail behave like an application"
date: 2012-12-29
forum: General Help
---

### Post by DrTebi on 2012-12-29
This little how-to should be of interest to you if you use Gmail, but prefer to run it in a separate window without browser toolbars etc. The Gmail web app created through these steps can become a separate launcher with it's own icon.

This guide is based on Ubuntu 12.04 and Google Chrome 23.0.1271.97, but it will most likely work with Chromium as well.


The most important thing to understand is, that the gmail application needs to run in it's own profile. If not, you will not be able to separate chrome and gmail icons in your launcher, or get a gmail icon at all.

Start by opening a terminal and creating an empty directory for the google-gmail profile:
```
mkdir ~/.config/google-gmail
```

Next you should have an icon for the app. Try something like this:
[https://www.google.com/imghp?um=1&q=gmail+icon+filetype:png]("https://www.google.com/imghp?um=1&q=gmail+icon+filetype:png")
Choose any image you like, preferable a square one. Make sure it's a PNG file and you probably don't want an image bigger than e.g. 256x256. Save this icon as gmail_icon.png in your local directory, e.g. ~/Pictures.

Now you are ready to create the custom launcher, which is a .desktop file. Browse to the directory where your local launchers are located:
```
cd ~/.local/share/applications
```

Now use your preferred text editor, e.g. nano, and create a file named gmail.desktop:
```
nano gmail.desktop
```

Put the following content into the file:
```

[Desktop Entry]
Type=Application
Version=1.0
Name=Gmail
GenericName=Web-based e-mail application    
Comment=Gmail
Icon=/home/<username>/Pictures/gmail_icon.png
OnlyShowIn=GNOME;Unity;
Exec=/opt/google/chrome/chrome --user-data-dir="~/.config/google-gmail" --app="https://mail.google.com/"
Terminal=false
Categories=Network;
Keywords=mail;email;e-mail;webmail;gmail;google mail;

```

Make sure you replace <username> with your username. Note that using the tilde (~) sign as a shortcut does not work in a .desktop file, you need to provide the full path.

Also make sure that the path after the "--user-data-dir" is correct; this is the path to the new profile directory you created earlier.

Save the file (in nano it's ctrl+o), exit your editor (ctrl+x in nano) and hit your "super" key or click the Ubuntu button. When you now search for gmail, your chosen icon should show up; when clicking on the icon, you should get a chrome window with no toolbars etc, only gmail.

In your launcher bar you should see your icon now, and you can lock it there if you like (right-click on it, choose "Lock to Launcher").


One last note: If the gmail window should ask anything about using this account for your profile (can't remember the exact wording), you probably should say no. You would not want to confuse your web-browsing profile with the gmail profile.


Any comments are welcome. I have successfully installed this launcher on two computers now, but if you are having trouble or this how-to needs some corrections, please let me know and I will edit it.

DrTebi

---

### Post by Elfy on 2012-12-29
Closed.

This forum is for support.

If you want to create a how to - then the wiki is the place for it, you can create a thread in Community Wiki Discussions once there's a wiki for it.

---

