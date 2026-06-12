---
title: "How to add date to logfile?"
date: 2014-10-28
forum: General Help
---

### Post by ELMIT on 2014-10-28
1. My current way:
program >> log
tail -f log | while read line; do echo `date` "$line" ; done >> log-date
tail -f log-date


How can I make that easier?


2 The log file includes a lots of data to display. I would like to add colors to certain text (only text or entire line)

So if tail -f log-date    finds  "success" then the line or just the word success should be green
if tail -f log-date    finds  "fail" then the line or just the word fail should be red

I want that only in the display, not in the log file itself.

---

### Post by btindie on 2014-10-30
Break it up into separate scripts. So for example

program:
```
#!/bin/bash

LINES=( "start" "performing check: success" "performing check: fail" "failure detected" "end" )

for LINE in "${LINES[@]}"; do
  echo "$LINE"
  sleep 2
done
```

prepend-date:
```
#!/bin/sh

while read LINE; do
  echo "$(date +%F\ %T): $LINE"
done
```

colour-output:
```
#!/bin/sh


sed -e 's/\bsuccess\b/\x1b[01;92m&\x1b[0m/' \
  -e 's/\bfail\b/\x1b[01;91m&\x1b[0m/' \
  -e 's/\b\(start\|end\)\b/\x1b[01;94m&\x1b[0m/'
```

You can then run it as
```
$ ./program | ./prepend-date | tee /tmp/log-date | ./colour-output
```
Which will display the colourised output on the terminal and prefix each log line with the date and write it to /tmp/log-date.

You could also run it as
```
$ ./program | ./prepend-date >> /tmp/log-date &
$ tailf /tmp/log-date | ./colour-output
```
which will separate it into two separate processes so you don't have to constantly have the log output to the terminal.

---

### Post by ELMIT on 2014-10-30
Thanks a lot!

Some more challenges:
What if I have found a trigger word, can I color the entire line instead only the trigger word?

Can you explain me where the color is and how I can change to other colors? Where are the color codes listed? Can I change the background instead of the font color or both?

---

### Post by Dennis N on 2014-10-30
I use log file viewer. You can create filters to find keywords in the log and also have it highlight the lines containing the keyword in color of your choosing.

---

