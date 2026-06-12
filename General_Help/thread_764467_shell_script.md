---
title: "shell script"
date: 2008-04-23
forum: General Help
---

### Post by alixthedark on 2008-04-23
I am trying to make a shell script but it wont work. can someone tell me what I did wrong please?
```

#!/bin/sh
set input=
set /p input=input:
if %input%==google goto A
if %input%==newgrounds goto B
if %input%==runescape goto C
if %input%==youtube goto D
if %input%==iaiym goto E
if %input%==wispering drive goto F
exit
A:
start http://google.com/
exit
B:
start http://newgrounds.com/
exit
C:
start http://www.runescape.com/
exit
D:
start http://www.youtube.com/
exit
E:
start http://itsallinyermind.proboards101.com/index.cgi?
exit
F:
start http://www.whisperingdrive.proboards88.com/index.cgi?
exit

```

---

### Post by alixthedark on 2008-04-23
I really need help.

---

### Post by Monicker on 2008-04-23
> **alixthedark said:**
> I am trying to make a shell script but it wont work. can someone tell me what I did wrong please?
```

#!/bin/sh
set input=
set /p input=input:
if %input%==google goto A
if %input%==newgrounds goto B
if %input%==runescape goto C
if %input%==youtube goto D
if %input%==iaiym goto E
if %input%==wispering drive goto F
exit
A:
start http://google.com/
exit
B:
start http://newgrounds.com/
exit
C:
start http://www.runescape.com/
exit
D:
start http://www.youtube.com/
exit
E:
start http://itsallinyermind.proboards101.com/index.cgi?
exit
F:
start http://www.whisperingdrive.proboards88.com/index.cgi?
exit

```


That looks like a windows batch file, and not a linux shell script.

You may want to peruse this:  [http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/")

---

### Post by ibuclaw on 2008-04-24
> **alixthedark said:**
> I am trying to make a shell script but it wont work. can someone tell me what I did wrong please?
Try this:
```

#!/bin/bash

if [ $# != "1" ]
then
    echo "Usage: $0 |google|newgrounds|runescape|youtube|iaiym|whispering|"
    exit 1
else
    case $1 in
        google)
            firefox http://www.google.com/
            ;;
        newgrounds)
            firefox http://www.newgrounds.com/
            ;;
        runescape)
            firefox http://www.runescape.com/
            ;;
        youtube)
            firefox http://www.youtube.com/
            ;;
        iaiym)
            firefox http://itsallinyermind.proboards101.com/index.cgi?
            ;;
        whispering)
            firefox http://www.whisperingdrive.proboards88.com/index.cgi?
            ;;
        *)
             echo "Usage: $0 |google|newgrounds|runescape|youtube|iaiym|whispering|"
             exit 1
             ;;
    esac
fi
exit 0

```
That should be a good translation of what you need.

After you save, you need to mark the file executable:
```
chmod +x **filename**
```

Regards
Iain

---

