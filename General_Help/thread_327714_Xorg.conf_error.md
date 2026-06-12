---
title: "Xorg.conf error"
date: 2006-12-29
forum: General Help
---

### Post by mk04 on 2006-12-29
I screwed up by xorg.conf file! ](*,)  How do I edit (fix) it, I can't boot into Ubuntu (I'm in WinXP).

---

### Post by ndube on 2006-12-29
> **mk04 said:**
> I screwed up by xorg.conf file! ](*,)  How do I edit (fix) it, I can't boot into Ubuntu (I'm in WinXP).

Does ubuntu at least let you log in via terminal?

---

### Post by mk04 on 2006-12-29
yes

---

### Post by ~LoKe on 2006-12-29
The xserver should fail and knock you into a virtual terminal.  Log in, type **sudo dpkg-reconfigure xserver-xorg**.  Once you follow the on setup, it'll bring you back to the terminal.  Now, type **sudo /etc/init.d/gdm restart**.

---

### Post by NeoLithium on 2006-12-29
It's wise to always make a backup file as well, before you modify configuration files, if you did do that, just copy the file over to what it was.
Generally, I do this before modifying it:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then if a problem comes up with the new configuration, you just have to reverse the command with
```
 sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

### Post by jimbob on 2006-12-29
If you aren't sure how to answer all the selections, entering sudo dpkg-reconfigure -phigh xserver-xorg will generate a new xorg.conf file for you to try without any of the questions.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

