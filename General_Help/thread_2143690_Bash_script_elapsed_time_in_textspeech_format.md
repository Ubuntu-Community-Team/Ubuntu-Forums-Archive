---
title: "Bash script: elapsed time in text/speech format"
date: 2013-05-09
forum: General Help
---

### Post by CaptainMark on 2013-05-09
I've got a whole bunch of scripts that I wanted to display elapsed time in a text format, for checking how long since a backup script was last run or how long its been since I last logged in somewhere or current uptime etc. etc.
Anyway I got fed up with duplicating effort so went online to see if someone has written some code that does this already but couldn't find anything so I wrote my own function and here it is for all to share if you want it.
```
function time_text() {    
    function plural() {
        if [ $1 -eq 1 ]; then
            echo "$1 $2"
        elif [ $1 -gt 1 ]; then
            echo "$1 $2s"
        fi
    }
    
    and=0
    
    (( year=$1/31536000 ))
    (( s=$1-$year*31536000 ))
    ((
    week=$s/604800,
    day=$s/86400%7,
    hour=$s/3600%24,
    minute=$s/60%60,
    second=$s%60
    ))
    
    if [ $2 ]; then
        [ $2 = "minutes" ] && let second=0
        [ $2 = "hours" ] && let {second,minute}=0
        [ $2 = "days" ] && let {second,minute,hour}=0
        [ $2 = "weeks" ] && let {second,minute,hour,day}=0
        [ $2 = "years" ] && let {second,minute,hour,day,week}=0
    fi
    
    for period in second minute hour day week year; do
        [ ${!period} -gt 0 ] && [ $and -eq 1 ] && result="and $result"
        [ ${!period} -gt 0 ] && result="$(plural ${!period} $period) $result" && (( and=$and+1 ))
    done

    [ -z "$result" ] && result="0 $2"
    echo $result
}
```If you post this into your bash script you can simply call the function with time_text and pass it a number of seconds to get that amount of time back in human readable words correct with plurals and the 'and' in the correct place.
Additionally you can pass it a second argument of days to round down to the nearest single day, or weeks for weeks, hours or minutes etc, months have been deliberately excluded because of their varying lengths but maybe I'll come back to that someday
 I find it most useful embedded into a notify-send or notify-osd command to alert users when they last did something like backup

Example:```
$ time_text 7654321
12 weeks 4 days 14 hours 12 minutes and 1 second
$ time_text 7654321 days
12 weeks and 4 days

```

Any feedback, thoughts or criticisms (please not too harsh, I still consider myself a beginner) feel free to comment them here.

Regards
Mark

---

### Post by CaptainMark on 2013-05-09
By the way before anyone posts about a built in bash command that does this exact thing already, I think my ignorance is my bliss, don't tell me I wasted an evening

---

### Post by Vaphell on 2013-05-09
eval in most cases is a dirty hack.
You can use ${!var} instead also you can replace lets with bash specific (()) switching to integer math mode

```
$ t=3333333
$ (( second=t%60, minute=t/60%60, hour=t/3600%24, day=t/86400%7, week=604800%52, year=t/31536000 ))
$ for period in second minute hour day week year; do echo $period **${!period}**; done
second 33
minute 55
hour 13
day 3
week 40
year 0
```

---

### Post by Impavidus on 2013-05-10
The script will fail when the time is between 364.0 and 365.0 days, because this is more than 52 full weeks, but still less than one year. It will report the same time as if time were between 0.0 and 1.0 days.

I think the best way to solve this would be to first calculate the number of years, subtract the number of years * 31536000 sec/year and convert the result into days and weeks. For the weeks no modulo is required, so 364.5 days = 31492800 seconds will be displayed as 0 years, 52 weeks, 0 days, 12 hours.

Alternatively, you can use fake years of only 364 days.

---

### Post by CaptainMark on 2013-05-11
@Vaphell Thanks for the advice, I have substituted your tips into the original post

@Impavidus Well spotted I hadn't considered that,

Ive amended the code in the original post, so what do you guys think now?

---

### Post by Impavidus on 2013-05-11
Looks OK now.

---

