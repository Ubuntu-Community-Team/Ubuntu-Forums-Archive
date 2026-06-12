---
title: "How do i use a &quot;&amp;&quot; in notify-send ?"
date: 2012-11-01
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-11-01
i made a little script for gmusicbrowser to use with notify-send so i always get a icon in it
```
~$ cat /usr/local/bin/notify-music 
#!/bin/sh
icon="$1"
if [ ! -f "$icon" ];then
    icon=gmusicbrowser
fi
while [ `pidof hwengine`0`pidof supertuxkart` -gt 0 ];do
    sleep 5
done
notify-send --icon="$icon" "$2" "$3"

```if there is a & in the Album name it only shows the icon and the title in the notification
```
notify-send --icon=gmusicbrowser "Title" "<i>by</i> Artist\n<i>from</i> Album"
```how do i make a & print in it?

edit:
seems you have to escape the & like you would in html &amp;
is there a better way to to that than this:
```
body=$(echo "$3" | sed 's/&/&amp;/')
```

---

### Post by Vaphell on 2012-11-02
```
notify-send --icon="$icon" "$2" "${3//&/&amp;}"
```

```
$ x='some&thing&some&thing'
$ echo "${x//&/&amp;}"
some&amp;thing&amp;some&amp;thing
```

---

### Post by pqwoerituytrueiwoq on 2012-11-02
thanks, though i think to do that i have to make it a bash script instead of a sh script, does that impact performance?

---

### Post by Doug S on 2012-11-02
> **pqwoerituytrueiwoq said:**
> thanks, though i think to do that i have to make it a bash script instead of a sh script, does that impact performance?Interesting question. I had heard bash was maybe 6 times slower than dash (dash is where /bin/sh points now (the change caused me some grief with a cgi script)). I decided to try to compare for myself, avoiding calls to other programs within the scripts.
 
Summary: bash was 4 times slower than dash
 
Details:```
doug@doug-64:~/scripts$ cat test_1.sh
#!/bin/bash
clear
echo 'Using bash: '
loops=2000000
iterations=$loops
echo 'Started at ' $(date)
Start=$(date +%s)
while [ $iterations -gt 0 ]; do
        let modvalue=$loops/10
        let c=iterations%$modvalue
        if [ $c -eq 0 ]
        then
                echo $iterations '      - ' $(date +"%T")
        fi
        let iterations=iterations-1
done
echo 'Finished at ' $(date)
Finished=$(date +%s)
let diff=$Finished-$Start
echo 'Completed in' $diff 'seconds'
doug@doug-64:~/scripts$

``````
Using bash:
Started at  Fri Nov 2 13:31:12 PDT 2012
2000000       -  13:31:12
1800000       -  13:31:27
1600000       -  13:31:43
1400000       -  13:31:58
1200000       -  13:32:14
1000000       -  13:32:29
800000       -  13:32:45
600000       -  13:33:00
400000       -  13:33:15
200000       -  13:33:31
Finished at  Fri Nov 2 13:33:46 PDT 2012
Completed in 154 seconds
doug@doug-64:~/scripts$
``````
doug@doug-64:~/scripts$ cat test_2.sh
#!/bin/dash
clear
echo 'Using dash: '
loops=2000000
iterations=$((loops))
echo 'Started at ' $(date)
Start=$(date +%s)
while [ $iterations -gt 0 ]; do
        modvalue=$(($loops/10))
        c=$(($iterations%$modvalue))
        if [ $c -eq 0 ]
        then
                echo $iterations '      - ' $(date +"%T")
        fi
        iterations=$((iterations-1))
done
echo 'Finished at ' $(date)
Finished=$(date +%s)
diff=$(($Finished-$Start))
echo 'Completed in' $diff 'seconds'
doug@doug-64:~/scripts$
``````
Using dash:
Started at  Fri Nov 2 13:30:03 PDT 2012
2000000       -  13:30:03
1800000       -  13:30:07
1600000       -  13:30:11
1400000       -  13:30:14
1200000       -  13:30:18
1000000       -  13:30:22
800000       -  13:30:26
600000       -  13:30:29
400000       -  13:30:33
200000       -  13:30:37
Finished at  Fri Nov 2 13:30:41 PDT 2012
Completed in 38 seconds
doug@doug-64:~/scripts$
```Readers: Please don't write about what a terrible programmer I am because I have the modvalue calculation inside the loop, whereas it should be outside. I did that on purpose, just to add another calculation to the loop to take more time.
 
References:
[http://www.pixelbeat.org/programming/shell_script_mistakes.html](http://www.pixelbeat.org/programming/shell_script_mistakes.html)
[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)
 
Edit: the real difference will, of course, be application dependent. For example, if I just add this line to each script:```
        calc=$(awk -v i=$iterations 'BEGIN{print sqrt(i)}') ;
```The execution times go to 3253 seconds for bash and 2379 seconds for dash, for a ratio of 1.4.

---

