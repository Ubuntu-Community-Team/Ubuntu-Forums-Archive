---
title: "Conky calendar layout problem"
date: 2008-05-31
forum: General Help
---

### Post by MeKino on 2008-05-31
Hi,

Suddenly, my conky calendar has started to screw up the last two rows - see attached image.

Is there anybody who can tell me how to fix it?

My conky script is:

${color #0077ff}Calendar ${hr 1}${color}
${color blue}${execi 1 ~/.conky/get_calendar.sh first_part}${color red}${execi 1 ~/.conky/get_calendar.sh today}${color blue}${execi 1 ~/.conky/get_calendar.sh second_part}

and the calendar script:

#! /bin/sh
#str=`echo '\033[01;32m29'`

DATE=`date | awk -F" " '{print $3}'`

case "$1" in
first_part)
cal | grep '[a-zA-Z]';
cal | grep -v '[a-zA-Z]' | grep '[0-9]' | awk -F$DATE ' BEGIN {i=0}
($1 == $0 && i==0) {print $1}($1 != $0 && i==0){i=i+1;print $1}';
;;
today)
echo $DATE;
;;
second_part)
cal | grep -v '[a-zA-Z]' | grep '[0-9]' | awk -F$DATE ' BEGIN {i=1}
(i==0) {print $0}($1 != $0 && i==1){i=i-1;print $2}';
;;
esac

Thanks in advance...

---

### Post by jjgomera on 2008-05-31
add this line at begin of conkyrc:

text_buffer_size 256

---

### Post by MeKino on 2008-05-31
Solved! Thank you!

---

