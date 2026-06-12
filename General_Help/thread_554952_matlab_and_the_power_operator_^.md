---
title: "matlab and the power operator ^"
date: 2007-09-19
forum: General Help
---

### Post by lessthanjake on 2007-09-19
I am not able to type in the power operator ( ^ ) in Matlab. It works great in all other applications. Anyone else experiencing this, and maybe even got an solution?

---

### Post by olejorgen on 2007-09-19
Easiest solution is to set the keyboard layout to "eliminate dead keys"
[http://ubuntuforums.org/showthread.php?t=347092&highlight=maple](http://ubuntuforums.org/showthread.php?t=347092&highlight=maple)

---

### Post by kaamos on 2007-09-19
Here is a simple script used at my uni:

```

case `uname` in
    Linux)
    if [ "$1" = "-restore" ]; then
        echo keycode 35 = dead_diaeresis dead_circumflex dead_tilde dead_caron dead_tilde \
        | xmodmap -
        echo "Restored keymap with dead key."
    else
        echo keycode 35 = asciicircum asciicircum asciitilde asciitilde | \
        xmodmap -
        echo "Activated xmodmap work-around for Matlab dead key lockup bug."
        echo
        echo "Keymap with dead key can be restored with command 'matlab-keyfix -restore'."
    fi
        echo
        echo "If Matlab is already running, please restart it."
    ;;

    *)
        echo "This work-around is only needed on Linux platform."
    ;;
esac

```

---

### Post by lessthanjake on 2007-09-19
Thanks, both tips worked great!

---

### Post by kakila on 2008-05-20
I updated this post
[http://ubuntuforums.org/showthread.p...ighlight=maple](http://ubuntuforums.org/showthread.p...ighlight=maple)

nice solution...

---

