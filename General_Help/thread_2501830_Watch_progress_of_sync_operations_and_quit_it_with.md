---
title: "Watch progress of sync operations and quit it with q"
date: 2024-10-22
forum: General Help
---

### Post by jagsdesai on 2024-10-22
[COLOR=#CCCCCC][FONT=&amp][COLOR=#dcdcaa]I[/COLOR] [COLOR=#ce9178]like[/COLOR] [COLOR=#ce9178]to[/COLOR] [COLOR=#ce9178]combine[/COLOR] [COLOR=#ce9178]these[/COLOR] [COLOR=#b5cea8]2[/COLOR] [COLOR=#ce9178]commands[/COLOR] [COLOR=#ce9178]in[/COLOR] [COLOR=#ce9178]order[/COLOR] [COLOR=#ce9178]to[/COLOR] [COLOR=#ce9178]watch[/COLOR] [COLOR=#ce9178]progress[/COLOR] [COLOR=#ce9178]of[/COLOR] [COLOR=#ce9178]sync[/COLOR] [COLOR=#ce9178]command[/COLOR] [COLOR=#ce9178]and[/COLOR] [COLOR=#ce9178]then[/COLOR] [COLOR=#ce9178]quit[/COLOR] [COLOR=#ce9178]it[/COLOR] [COLOR=#ce9178]with[/COLOR] [COLOR=#ce9178]'q'.[/COLOR]

```
[COLOR=#DCDCAA]watch[/COLOR][COLOR=#569CD6]-n1[/COLOR][COLOR=#CE9178] 'grep -E "(Dirty|Write)" /proc/meminfo; echo; ls /sys/block/ | while read device; do awk "{ print \"$device: \"  \$9 }" "/sys/block/$device/stat"; done';[/COLOR]
```
[COLOR=#dcdcaa]
Source:[/COLOR] [COLOR=#ce9178]https://unix.stackexchange.com/a/713647/366010[/COLOR]

[COLOR=#dcdcaa]and[/COLOR] [COLOR=#ce9178]quit[/COLOR] [COLOR=#ce9178]it[/COLOR] [COLOR=#ce9178]qith[/COLOR] [COLOR=#ce9178]q[/COLOR] [COLOR=#ce9178]by[/COLOR] [COLOR=#ce9178]either:[/COLOR]

```
[COLOR=#D4D4D4]2>&1[/COLOR][COLOR=#D4D4D4]|[/COLOR][COLOR=#DCDCAA]less[/COLOR]
```
or
[/FONT][/COLOR]```
[COLOR=#CCCCCC][FONT=&amp][COLOR=#D4D4D4]|[/COLOR][COLOR=#CE9178]& [/COLOR][COLOR=#DCDCAA]less[/COLOR][/FONT][/COLOR]
```[COLOR=#CCCCCC][FONT=&amp]

[COLOR=#dcdcaa]Source:[/COLOR] [COLOR=#ce9178]https://askubuntu.com/a/1415867/928088[/COLOR]

[COLOR=#dcdcaa]So[/COLOR] [COLOR=#ce9178]I've created a fucntion:[/COLOR]

```
[COLOR=#CE9178]nano ~/.bashrc[/COLOR]
```
[COLOR=#ce9178]
and added:[/COLOR]

```
[COLOR=#CE9178]function ws() {
[/COLOR][COLOR=#ce9178]    ( watch -n1 'grep[/COLOR] [COLOR=#569cd6]-E[/COLOR] [COLOR=#ce9178]"(Dirty|Write)"[/COLOR] [COLOR=#ce9178]/proc/meminfo[/COLOR]; [COLOR=#dcdcaa]echo[/COLOR]; [COLOR=#dcdcaa]ls[/COLOR] [COLOR=#ce9178]/sys/block/[/COLOR] [COLOR=#d4d4d4]|[/COLOR] [COLOR=#c586c0]while[/COLOR] [COLOR=#dcdcaa]read[/COLOR] [COLOR=#ce9178]device[/COLOR]; [COLOR=#c586c0]do[/COLOR] [COLOR=#dcdcaa]awk[/COLOR] [COLOR=#ce9178]"{ print [/COLOR][COLOR=#d7ba7d]\"[/COLOR][COLOR=#9cdcfe]$device[/COLOR][COLOR=#ce9178]: [/COLOR][COLOR=#d7ba7d]\"[/COLOR][COLOR=#d7ba7d]\$[/COLOR][COLOR=#ce9178]9 }"[/COLOR] [COLOR=#ce9178]"/sys/block/[/COLOR][COLOR=#9cdcfe]$device[/COLOR][COLOR=#ce9178]/stat"[/COLOR]; done[COLOR=#ce9178]'; )[/COLOR]
[COLOR=#ce9178]}[/COLOR]
```

```
[COLOR=#CE9178]export -f ws[/COLOR]
```

[COLOR=#ce9178]So, with '[/COLOR]ws[COLOR=#ce9178]' I get:[/COLOR]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294401&stc=1[/IMG]

[COLOR=#ce9178]Now if I add:[/COLOR]

```
[COLOR=#CE9178]2>&1 | less;[/COLOR]
```
[COLOR=#ce9178]
to combine both and make it:[/COLOR]

```
[COLOR=#CE9178]function ws() {
[/COLOR][COLOR=#ce9178]    ( watch -n1 '[/COLOR]grep -E [COLOR=#ce9178]"(Dirty|Write)"[/COLOR] /proc/meminfo; [COLOR=#dcdcaa]echo[/COLOR]; [COLOR=#dcdcaa]ls[/COLOR] [COLOR=#ce9178]/sys/block/[/COLOR] [COLOR=#d4d4d4]|[/COLOR] [COLOR=#c586c0]while[/COLOR] [COLOR=#dcdcaa]read[/COLOR] [COLOR=#ce9178]device[/COLOR]; [COLOR=#c586c0]do[/COLOR] [COLOR=#dcdcaa]awk[/COLOR] [COLOR=#ce9178]"{ print [/COLOR][COLOR=#d7ba7d]\"[/COLOR][COLOR=#9cdcfe]$device[/COLOR][COLOR=#ce9178]: [/COLOR][COLOR=#d7ba7d]\"[/COLOR][COLOR=#d7ba7d]\$[/COLOR][COLOR=#ce9178]9 }"[/COLOR] [COLOR=#ce9178]"/sys/block/[/COLOR][COLOR=#9cdcfe]$device[/COLOR][COLOR=#ce9178]/stat"[/COLOR]; done[COLOR=#ce9178]'; ) 2>&1 | less;[/COLOR]
[COLOR=#ce9178]}[/COLOR]
```

[COLOR=#ce9178]I get this jumbled output:[/COLOR]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294402&stc=1[/IMG]

[COLOR=#ce9178]So how to combine these 2 commands? Many thanks in advance.[/COLOR]
[/FONT][/COLOR]

---

### Post by sudodus on 2024-10-22
I suggest that you make a bash shellscript and use the bash version of **[FONT=Courier New]read[/FONT]** that is activated by a 'q' in order to kill **[FONT=Courier New]watch[/FONT]**.

```

#!/bin/bash

watch -n1 'grep -E "(Dirty|Write)" /proc/meminfo;
echo;
ls /sys/block/ | while read device;
do
 awk "{ print \"$device: \"  \$9 }" "/sys/block/$device/stat"
done' & pid=$!

while true
do
 read -sn1 -t2 ans
 if [ "$ans"  == "q" ]
 then
  kill -9 "$pid"
  echo "
quit"
  exit 0
 fi
done

```

---

### Post by 1fallen on 2024-10-22
+1 to sudodus's script

---

### Post by jagsdesai on 2024-10-22
> **sudodus said:**
> I suggest that you make a bash shellscript and use the bash version of **[FONT=Courier New]read[/FONT]** that is activated by a 'q' in order to kill **[FONT=Courier New]watch[/FONT]**.

It's working perfectly. Many thanks.

---

