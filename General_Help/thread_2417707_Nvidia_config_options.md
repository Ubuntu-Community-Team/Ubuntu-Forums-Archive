---
title: "Nvidia config options"
date: 2019-04-26
forum: General Help
---

### Post by morcar on 2019-04-26
Where would I save the changes I make once I have changed my graphics card options?

I can change them within the Nvidia configurator but when I go to save I don't know where I should be saving them.

Any help would be greatly appreciated.

---

### Post by Rubi1200 on 2019-04-27
When you make the changes do you not see an option to save like this?
[https://prnt.sc/nhm4dp](https://prnt.sc/nhm4dp)

---

### Post by kryten35 on 2019-04-27
The NVIDIA X driver does not preserve values set with nvidia-settings
between runs of the X server (or even between logging in and logging
out of X, with xdm, gdm, or kdm).  This is intentional, because
different users may have different preferences, thus these settings
are stored on a per user basis in a configuration file stored in
the user's home directory.

The configuration file is named "~/.nvidia-settings-rc".  You can
specify a different configuration file name with the "--config"
commandline option.

After you have run nvidia-settings once and have generated a
configuration file, you can then run:

    nvidia-settings --load-config-only

at any time in the future to upload these settings to the X
server again.  For example, you might place the above command in
your ~/.xinitrc file so that your settings are applied automatically
when you log in to X.

Your .xinitrc file, which controls what X applications should
be started when you log into X (or startx), might look something
like this:

    nvidia-settings --load-config-only &
    xterm &
    evilwm

or:

    nvidia-settings --load-config-only &
    gnome-session

If you do not already have an ~/.xinitrc file, then chances are that
xinit is using a system-wide xinitrc file.  This system wide file
is typically here:

    /etc/X11/xinit/xinitrc

To use it, but also have nvidia-settings upload your settings,
you could create an ~/.xinitrc with the contents:

    nvidia-settings --load-config-only &
    . /etc/X11/xinit/xinitrc

System administrators may choose to place the nvidia-settings load
command directly in the system xinitrc script.

Please see the xinit(1) manpage for further details of configuring
your ~/.xinitrc file.

---

