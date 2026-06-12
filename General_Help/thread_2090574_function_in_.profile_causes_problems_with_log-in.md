---
title: "function in .profile causes problems with log-in"
date: 2012-12-02
forum: General Help
---

### Post by sgy on 2012-12-02
When I add the following function definition to .profile, it becomes impossible for me to log-in through the display manager after restart.  The log-in screen sends me back to the log-in screen, indefinitely.  I can ctr-alt-F1 to tty1.

What am I doing wrong?  Why would that happen?  I am running Quantal, although my signature may indicate otherwise.  Thanks.

```

sgy-project() {
if [ -d "$HOME/jhsph" ] ; then
    if [ "$1" = "seq" ] ; then
    if [ -d "/home/sgy/jhsph/targeted-sequencing/" ] ; then
        export WORKDIR="/home/sgy/jhsph/targeted-sequencing/"
    else
        echo "project directory does not exist"
        export WORKDIR="/home/sgy/"
    fi
    fi
else
    echo "jhsph is not mounted"
    export WORKDIR="/home/sgy/"
fi
}

```

---

