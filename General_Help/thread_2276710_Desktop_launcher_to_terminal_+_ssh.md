---
title: "Desktop launcher to terminal + ssh"
date: 2015-05-04
forum: General Help
---

### Post by majest2 on 2015-05-04
I would like an icon on the desktop (Xubuntu 14) that opens a terminal emulator and enters the command ssh -X majest@123.345.567.678 leaving me at the password prompt.

I've tried messing around with creating launchers but can't get it to work. Thanks for any pointers!

---

### Post by Lars Noodén on 2015-05-04
Have you tried these instructions for creating a desktop file?

[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

As for the details of the *Exec* line, that would be gnome-terminal.  :

```

Exec=/usr/bin/gnome-terminal --window-with-profile=Default --execute  /usr/bin/ssh -X majest@123.345.567.678
Icon=/usr/share/app-install/icons/openterm.svg

```

If you don't have a custom profile in mind, you can leave that option off.

---

### Post by majest2 on 2015-05-12
Hey Lars - thanks! I'm on Xubuntu so the Exec command was

Exec=/usr/bin/xfce4-terminal --execute /usr/bin/ssh -X [email]mb1234@sdf.org[/email]

Another little problem... I am trying to make a launcher for Thunar (file manager) to open a remote folder. I can't make it work. Do you know how? Using the same ssh or sftp mechanism, ideally. I made it work once by entering the IP address, connecting and then dragging+dropping the URL onto the desktop but it breaks as soon as I log off.

---

### Post by Lars Noodén on 2015-05-13
I don't have XFCE4 so I can only guess that it would probably be something like this:

```

Exec=/usr/bin/thunar sftp://mg1234****@sdf.org/home/mg1234/

```

As far as I know, it won't work with keys, even if you've loaded them into the agent.  So that may be a problem.

---

