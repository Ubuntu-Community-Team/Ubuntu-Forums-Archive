---
title: "init-functions colors - hardy"
date: 2008-05-01
forum: General Help
---

### Post by allinurl on 2008-05-01
Hello, Does anybody knows how to edit init-functions in order to display colors on the startup console under hardy? I've tried on 7.10 and was working fine but Im not quite sure how to do it under 8.04. Thanks

---

### Post by nantax on 2008-06-06
*bump*

I'm also interested in adding colors to my boot up screen since I don't use the splash screen.

Any help on this would be appreciated.

After reading this [thread]("http://ubuntuforums.org/showthread.php?t=811005") I managed to locate the [OK] here: /etc/lsb-base-logging.sh

Now if somebody will help us figure out how to add colors... :)

---

### Post by nantax on 2008-06-06
```
log_end_msg () {
    if [ -z "$1" ]; then
        return 1
    fi

    if log_use_usplash; then
        if [ "$1" -eq 0 ]; then
            usplash_write "SUCCESS OK" || true
        else
            usplash_write "FAILURE failed" || true
        fi
    fi

    log_to_console log_end_msg "$@"

    if [ "$COL" ] && [ -x "$TPUT" ]; then
        printf "\r"
        $TPUT hpa $COL
        [B]if [ "$1" -eq 0 ]; then
            $TPUT setaf 4 # blue
            printf "["
            $TPUT setaf 3 # yellow
            printf " OK "
            $TPUT setaf 4 # blue
            echo "]"
            $TPUT op # normal[/B]
        else
            printf '['
            $TPUT setaf 1 # red
            printf fail
            $TPUT op # normal
            echo ']'
        fi
    else
        if [ "$1" -eq 0 ]; then
            echo "   ...done."
        else
            echo "   ...fail!"
        fi
    fi
    return $1
}
```

Okay I modified the code in bold and it's now showing colors. I wish I can colorize the [nnn]: part too. :)

---

