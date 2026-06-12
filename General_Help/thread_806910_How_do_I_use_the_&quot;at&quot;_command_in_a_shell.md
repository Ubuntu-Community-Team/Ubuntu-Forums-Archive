---
title: "How do I use the &quot;at&quot; command in a shell script?"
date: 2008-05-25
forum: General Help
---

### Post by Macintosh SE on 2008-05-25
I am writing a Bash shell script to record TV from a TV tuner. The tuner works fine. However, I want to set recording for a later time. How do I execute a command with at through a shell script, without using at -f (which is the only function of this command that I'm familiar with)?

---

### Post by chewearn on 2008-05-25
You can use echo to output the command, which is piped into the at command.

E.g. this will show a notify balloon in the next minute:

```
echo "notify-send -u normal -t 5000 \"Test\" \"This is a test.\"" | at now + 1 minutes
```

Note:
libnotify-bin required for the example.

.

---

