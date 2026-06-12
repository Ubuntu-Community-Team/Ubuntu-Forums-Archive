---
title: "How to change boot text color"
date: 2013-05-29
forum: General Help
---

### Post by JKUSHALYA on 2013-05-29
I like to change my boot text colours. I tried to change colour in [ OK ] to green by change following in > lsb-base-logging.sh
```

        log_end_msg () {
        if [ -z "$1" ]; then
            return 1
        fi
    
        if [ "$COL" ] && [ -x "$TPUT" ]; then
            # If plymouth is running, print previously stored output
            # to avoid buffering problems (LP: #752393)
            if log_use_plymouth; then
                if [ -n "$LOG_DAEMON_MSG" ]; then
                    log_daemon_msg $LOG_DAEMON_MSG
                    LOG_DAEMON_MSG=""
                fi
            fi
    
            printf "\r"
            $TPUT hpa $COL
            if [ "$1" -eq 0 ]; then
                $TPUT setaf  4 # blue
                printf '[ '
                $TPUT setaf  2 # green
                printf OK
                $TPUT setaf  4 # blue
                echo ' ]'
                $TPUT op  # normal                      
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

This works when machine going to halt and shows all [ok]'s in green. But when booting only one is in green. Bellow is my boot log. As you can see only the apparmour  [ok] is in green.

[IMG]http://i.stack.imgur.com/2zOi6.png[/IMG]

What is the wrong with this? How can resolve this? Is this a Bug? Thanks in advance!

---

### Post by JKUSHALYA on 2013-05-30
Is this the right forum to ask this? If not please move this to correct category.

---

### Post by JKUSHALYA on 2013-05-30
At least can any one point me some related things to this. Am I the only one who tried this?

---

