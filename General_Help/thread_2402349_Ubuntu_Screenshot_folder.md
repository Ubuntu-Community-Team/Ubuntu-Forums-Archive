---
title: "Ubuntu Screenshot folder"
date: 2018-09-29
forum: General Help
---

### Post by bizhat on 2018-09-29
I am running Ubuntu 18.04, when i press  "Print Screen", screenshot  get saved to /home/user folder.

I want it save to  /home/boby/Pictures like it do by default. This happen after i did some HDD move, my picture was a symlink another drve, after i change my PC, this drive was not available for some time because it was zfs drive.

Now i created Pictures folder, but screenshot get saved to my home folder. 

I changed settings with gsettings, but it still get saved to home directory.

```

boby@ok-pc-01:~$ gsettings get org.gnome.gnome-screenshot auto-save-directory
'/home/boby/Pictures/'
boby@ok-pc-01:~$ 

```

Default value from  ''

I retarted PC after setting the value, still screenshots getting saved to /home/boby folder.

Any idea how to get screenshots saved to Pictures folder ?

---

### Post by monkeybrain20122 on 2018-09-29
> **bizhat said:**
> 

Now i created Pictures folder, but screenshot get saved to my home folder. 



So this is not the original Picture folder?

Open your file manager. show hidden files, go inside the hidden folder .config, open the file usr-dirs.dirs

make sure that the XDG_PICTURES_DIR is set  to your Pictures folder (or wherever you want)
```

XDG_PICTURES_DIR="$HOME/Pictures"
```

It probably becomes empty

---

### Post by bizhat on 2018-09-29
Thanks, that fixed it.

```

boby@ok-pc-01:~$ cat ~/.config/user-dirs.dirs | grep -i pict
XDG_PICTURES_DIR="$HOME/"
boby@ok-pc-01:~$

```

Edited it and rebooted PC. Now screenshots saved properly, with out reboot it keept saving to home dir.

What is the default value for 

```

gsettings get org.gnome.gnome-screenshot auto-save-directory

```

Should i revert back to empty sting '' ?

---

### Post by monkeybrain20122 on 2018-09-29
The default gsettings here is empty. You can revert back and in case it breaks again you can always change it.

---

### Post by bizhat on 2018-09-29
Thanks, i set it to default value

```

gsettings set org.gnome.gnome-screenshot auto-save-directory  ''

```

---

