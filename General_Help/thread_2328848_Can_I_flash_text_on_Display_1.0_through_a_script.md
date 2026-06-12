---
title: "Can I flash text on Display 1.0 through a script"
date: 2016-06-25
forum: General Help
---

### Post by Superdude_123 on 2016-06-25
I was wondering, is is possible for a BASH command to display a string of text over what's on Display 1 (Unity)?

I have a shell script that monitors my external IP and I would like it to over lay a string of text with the idea that it would show "New IP = $IP" on top of my X11 session.

---

### Post by sudodus on 2016-06-25
Maybe ruby-notify can do it for you:

- Install
```
sudo apt install ruby-notify
```

- Examples:
```
notify "summary" "This is is the text body with LANG=$LANG"
notify --expire-time=2000 "summary" "This is is the text body with LANG=$LANG"  # shown 2 s (2000 ms)
notify --expire-time=0 "summary" "This is is the text body with LANG=$LANG"     # does not expire until 'you click on it'

```

You find more details via the help option.
```
$ [COLOR="#0000FF"]notify --help[/COLOR]
Usage:
  notify-send [OPTION...] <SUMMARY> [BODY] - create a notification

Help Options:
  -?, --help                        Show help options

Application Options:
  -u, --urgency=LEVEL               Specifies the urgency level (low, normal, critical).
  -t, --expire-time=TIME            Specifies the timeout in milliseconds at which to expire the notification.
  -a, --app-name=APP_NAME           Specifies the app name for the icon
  -i, --icon=ICON[,ICON...]         Specifies an icon filename or stock icon to display.
  -c, --category=TYPE[,TYPE...]     Specifies the notification category.
  -h, --hint=TYPE:NAME:VALUE        Specifies basic extra data to pass. Valid types are int, double, string and byte.
  -v, --version                     Version of the package.

```

---

