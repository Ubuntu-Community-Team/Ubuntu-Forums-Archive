---
title: "Way to remove packages by the date they were installed?"
date: 2008-05-18
forum: General Help
---

### Post by robog2 on 2008-05-18
So I installed xubuntu-desktop through apt-get (rather than aptitude, as I should have); now that I wish to undo this action, "apt-get remove" does not remove all packages installed as a result of the original (stupid) command.  The only way I can think of removing them all without having to remove each one individually (by looking at the apt log) is to do so by date, as they are the only ones I installed today.

Simply put: is there a way to remove packages by the date on which they were installed?


Thanks in advance.

---

### Post by Sef on 2008-05-18
> So I installed xubuntu-desktop through apt-get (rather than aptitude, as I should have); now that I wish to undo this action, "apt-get remove" does not remove all packages installed as a result of the original (stupid) command. The only way I can think of removing them all without having to remove each one individually (by looking at the apt log) is to do so by date, as they are the only ones I installed today.

The way to completely remove a file (including configuration files) is with a purge option:

```
sudo apt-get --purge remove package_name
```

---

### Post by robog2 on 2008-05-18
I just tried this, and still only "xubuntu-desktop" is removed (none of the packages installed along with it were removed).  I am running Ubuntu Hardy, by the way.

Any other suggestions?

Thanks

---

### Post by sdennie on 2008-05-19
This is a brute force method to remove xubuntu-desktop but, you could install a clean ubuntu machine in a VM, install xubuntu desktop, note the packages and then remove the listed packages form your host machine.  To save you the work, here is a list of packages that xubuntu-desktop installs after a clean install of ubuntu 8.04:

```

a2ps abiword abiword-common abiword-plugins gnumeric-common gnumeric-gtk gtk2-engines-xfce imagemagick libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libglib2.0-data libgoffice-0-6 libgoffice-0-6-common libgsf-gnome-1-114 libgtkmathview0c2a liblink-grammar4 libots0 libt1-5 libtagc0 libthunar-vfs-1-2 libwpd-stream8c2a libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 link-grammar-dictionaries-en mousepad mozilla-thunderbird orage psutils python-exo ristretto scim-modules-table scim-tables-additional tango-icon-theme tango-icon-theme-common thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird vim-runtime xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-governor-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mcs-plugins-extra xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs

```

I just did an install of xubuntu-desktop into a clean ubuntu VM then removed it using "sudo apt-get remove that_gigantic_list_of_files_I_posted" and it only removed exactly those packages (86 installed, 86 removed).  You'll probably want to review that list to make sure it doesn't include stuff that you've manually installed.

---

### Post by robog2 on 2008-05-19
Thank you!  I very much appreciate your help.

-Garrett

---

