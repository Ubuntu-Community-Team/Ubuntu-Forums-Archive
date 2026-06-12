---
title: "self-purging guest account"
date: 2008-03-24
forum: General Help
---

### Post by lemonlaw95 on 2008-03-24
does anyone know how to make an account purge itself when you log out?  purge meaning delete the home folder and settings.  i've got a guest account working, but i just need to make it do this, like with windows xp and osx.  any help will be greatly appreciated.

---

### Post by monraaf on 2008-03-24
Try adding this just before **exit 0** in * /etc/gdm/PostSession/Default*

```

if [ "$HOME" = "/home/guest" -a  -d "/home/guest" ]; then
    pkill -9 -u guest
    rm -rf /home/guest
    mkdir /home/guest
    chown guest:guest /home/guest
fi

```

---

### Post by dcstar on 2008-03-24
This may be worth considering:

[http://ubuntuforums.org/showpost.php?p=2297167&postcount=9](http://ubuntuforums.org/showpost.php?p=2297167&postcount=9)

---

### Post by lemonlaw95 on 2008-03-24
.

---

