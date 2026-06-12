---
title: "do-release-upgrade - prompt at shell/ssh login"
date: 2012-11-02
forum: General Help
---

### Post by heWhoWearsAshes on 2012-11-02
I've done this before, I've just forgot how to do it. There was a file that filled up the /etc/motd with all the release-y sorta info and I want to know how to set/unset it.

---

### Post by Lars Noodén on 2012-11-02
What kind of release info?  The program or script you use to get that release info could go in .bashrc  One option is "/usr/bin/lsb_release -rd"

---

### Post by pbrane on 2012-11-02
I think this is what you're talking about,
[http://www.howtogeek.com/104708/how-to-customize-ubuntus-message-of-the-day/]("http://www.howtogeek.com/104708/how-to-customize-ubuntus-message-of-the-day/")

or

```

man update-motd

```

---

### Post by heWhoWearsAshes on 2012-11-02
> **pbrane said:**
> I think this is what you're talking about,
[http://www.howtogeek.com/104708/how-to-customize-ubuntus-message-of-the-day/]("http://www.howtogeek.com/104708/how-to-customize-ubuntus-message-of-the-day/")

or

```

man update-motd

```

I checked it out, there's a script in /etc/update-motd called 91-release-upgrade and it fires another script /usr/lib/update-manager/release-upgrade-motd. It checks to see if /var/lib/update-notifier/release-upgrade-available has contents, then prints them on the /etc/motd.

So, turns out my /var/lib/update-notifier/release-upgrade-available is vacant. I guess there's some other script that populates it with the message saying to run do-release-upgrade.

/etc/update-motd.d/91-release-upgrade-motd:
```
#!/bin/sh

exec /usr/lib/update-manager/release-upgrade-motd

```

/usr/lib/update-manager/release-upgrade-motd:
```
stamp=/var/lib/update-notifier/release-upgrade-available
if [ -s "$stamp" ]; then
        # Stamp exists and is populated, so display
        cat "$stamp"
        echo
elif [ -f "$stamp" ]; then
        # Stamp exists, but is empty, see if it's expired
        now=$(date +%s)
        lastrun=$(stat -c %Y "$stamp") 2>/dev/null || lastrun=0
        expiration=$(expr $lastrun + 86400)
        if [ $now -ge $expiration ]; then
                # But is older than 1 day old, so update in the background
                /usr/lib/update-manager/check-new-release -q > "$stamp" &
        fi

```

/var/lib/update-notifier/release-upgrade-motd:
```
""
```

---

