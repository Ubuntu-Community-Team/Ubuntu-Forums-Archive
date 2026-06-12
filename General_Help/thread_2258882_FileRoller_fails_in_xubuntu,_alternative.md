---
title: "FileRoller fails in xubuntu, alternative?"
date: 2014-12-31
forum: General Help
---

### Post by fkervin on 2014-12-31
Hi All,

I have some problems with file roller in xubuntu, sometimes it has an error and closed itself, so I'm thinking in removing it and install another file compression manager.

In kubuntu I used ark and worked ok, anyone can reccomend me this or another one?

And finally... how to install correctly and uninstall fileroller then integrate with thunar?

Many thanks in advance

---

### Post by schragge on 2014-12-31
Try [xarchiver]("http://manpages.ubuntu.com/manpages/trusty/man1/xarchiver.1.html"). To make thunar work with it as its archive manager you'll probably need to create *xarchive.tap* based on either *file-roller.tap* or *ark.tap* from package thunar-archive-plugin. It should contain something like:
```

action=$1; shift;
folder=$1; shift;

# check the action
case $action in
create)
        exec xarchiver --add "$@"
        ;;

extract-here)
        exec xarchiver --extract-to="$folder" "$@"
        ;;

extract-to)
        exec xarchiver --extract "$@"
        ;;

*)
        echo "Unsupported action '$action'" >&2
        exit 1
esac

```
It should be put in the same directory with file-roller.tap and ark.tap. Look it up with
```
dpkg -L thunar-archive-plugin|grep /file-roller.tap
```

---

### Post by oldos2er on 2014-12-31
> **fkervin said:**
> Hi All,

I have some problems with file roller in xubuntu, sometimes it has an error and closed itself, 

It would help to know what the error was; file-roller is just a GUI front-end to the CLI compression tools one has installed.

---

