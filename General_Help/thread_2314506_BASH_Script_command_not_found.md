---
title: "BASH Script command not found"
date: 2016-02-21
forum: General Help
---

### Post by nzdreamer55 on 2016-02-21
Hello everyone,

I am trying to write a BASH script and when I execute it I get "command not found".

[FONT=arial, sans-serif]When I run the following from the terminal window it works like a charm

[/FONT][FONT=arial]filebot -script fn:amc "/home/pi/usrmnt/Target/TV" --def "seriesFormat=\\\\TITANSERVER/[/FONT][FONT=arial]Series.Pool/{n}/{episode.[/FONT][FONT=arial]special ? 'Special' : 'Season '+s.pad(2)}/{n}.{s00e00}{'.'+[/FONT][FONT=arial]fn.match(/(?i:proper)/).[/FONT][FONT=arial]toLowerCase().upperInitial()}{[/FONT][FONT=arial]'.'+fn.match(/(?i:repack)/).[/FONT][FONT=arial]toLowerCase().upperInitial()}{[/FONT][FONT=arial]'.'+[vf]}{'.'+[vc]}{'.'+[ac]}{[/FONT][FONT=arial]'.'+[af]}{'.'+[source]}{'.'+[[/FONT][FONT=arial]group]}.{t}" -r --log-file "/home/pi/log/Filebot.log" --action move --conflict override -non-strict --def backdrops=y --def artwork=y[/FONT][FONT=arial] --def clean=y --def ut_label=tv --def excludeList="/home/pi/log/amc-[/FONT][FONT=arial]input.txt" > /home/pi/log/filebot.TV.log 2>&1

[/FONT]I can read the log and all is well but when I create a BASH script

```
#!/bin/bash
[FONT=arial]filebot -script fn:amc "/home/pi/usrmnt/Target/TV" --def "seriesFormat=\\\\TITANSERVER/[/FONT][FONT=arial]Series.Pool/{n}/{episode.[/FONT][FONT=arial]special ? 'Special' : 'Season '+s.pad(2)}/{n}.{s00e00}{'.'+[/FONT][FONT=arial]fn.match(/(?i:proper)/).[/FONT][FONT=arial]toLowerCase().upperInitial()}{[/FONT][FONT=arial]'.'+fn.match(/(?i:repack)/).[/FONT][FONT=arial]toLowerCase().upperInitial()}{[/FONT][FONT=arial]'.'+[vf]}{'.'+[vc]}{'.'+[ac]}{[/FONT][FONT=arial]'.'+[af]}{'.'+[source]}{'.'+[[/FONT][FONT=arial]group]}.{t}" -r --log-file "/home/pi/log/Filebot.log" --action move --conflict override -non-strict --def backdrops=y --def artwork=y[/FONT][FONT=arial] --def clean=y --def ut_label=tv --def excludeList="/home/pi/log/amc-[/FONT][FONT=arial]input.txt" > /home/pi/log/filebot.TV.log 2>&1[/FONT]
```

and try to execute it I get a command not found.  I am using ubuntu-mate on a raspberry pi.

Any idea what I am doing wrong?

---

### Post by steeldriver on 2016-02-21
How exactly are you trying to execute the script? Where is it located?

---

### Post by nzdreamer55 on 2016-02-21
It is located /home/pi/ and it is called tv.move.filebot.script.

I am opening a terminal window and typing tv.move.filebot.script

---

### Post by steeldriver on 2016-02-21
Unless you have added the directory /home/pi/ to your shell's PATH, you will need to give a full path to the script

```

/home/pi/tv.move.filebot.script

```

It will also need to be marked as executable, either from the file manager or from a terminal using

```

chmod +x /home/pi/tv.move.filebot.script

```

Path's don't have to be absolute e.g. if you are already in directory /home/pi then you can use relative path ./ to indicate the current directory

```

./tv.move.filebot.script

```

---

### Post by nzdreamer55 on 2016-02-21
Thanks.  I'll give that a try.  So my home directory isn't in my path by default?

I chmod 777 to the file.  Do I also need to chmod +x?

---

### Post by steeldriver on 2016-02-21
No the user's home directory is not on the PATH by default: check using

```

echo $PATH

```

777 makes it executable *and writeable* by everyone - not necessary. You could back that off to 755.

---

