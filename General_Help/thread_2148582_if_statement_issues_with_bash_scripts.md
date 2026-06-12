---
title: "if statement issues with bash scripts"
date: 2013-05-25
forum: General Help
---

### Post by DoubleD33D on 2013-05-25
I've been fighting with bash for awhile now. I spent hours trying to get if statements that wouldn't trigger syntax errors, and when I finally did I found out that they are evaluating as true no matter what. Here is the goal of my script


 1. Check that output of `sh /var/scripts/running.sh` is true (will output "1\n" in which case
 2. If it is running, begin a for loop, for a max of 5 loops
 3. Check for an expected output from command and print it to a file if it is and break the loop
 4. If the loop ends and the expected output was not found, clear the output file


The expected output from the command is for it to contain two "[INFO]" no more or no less


Here is my script


    ```
#!/bin/bash
    
    #Is the server running?
    serverStat=$(sh /var/scripts/running.sh)
    echo "serverStat is $serverStat"
    if [ "$serverStat" == "1\n" ]
    then
        serverStat="true"
    else
        serverStat="false"
    fi
    
    #If the server is running
    if [ $serverStat="true" ]
    then
        for i in `seq 1 5`
        do
            playersLong=$(/etc/init.d/minecraft command list)
            temp=$(echo $playersLong | grep "[INFO]" | wc -l)
            echo "temp is $temp"
            if [ $temp="2\n" ]
            then
                echo "$playersLong"
                echo "$playersLong" > /var/www/list.txt
                playersProper="true"
                break
            else
                playersProper="false"
                sleep 10
            fi
        done
        if [ $playersProper="false" ]
        then
            > /var/www/list.txt
        fi
    fi



```Issues are
If statements are always evaluating true, even when they are CLEARLY not
-----
playersLong=$(/etc/init.d/minecraft command list)
temp=$(echo $playersLong | grep "[INFO]" | wc -l)
-----
gives temp and value of "1\n" when when I run $ /etc/init.d/minecraft command list | grep "[INFO]" | wc -l from command line I get "2\n"

---

### Post by steeldriver on 2013-05-25
You need some whitespace around the = operator in bash string comparisons - also good practice to quote any variables:

```
if [ "$temp" = "2\n" ]
```

See [http://tldp.org/LDP/abs/html/comparison-ops.html](http://tldp.org/LDP/abs/html/comparison-ops.html)

> 
**string comparison**=is equal to
**if [ "$a" = "$b" ]**
[TABLE="class: CAUTION, width: 90%"]
[TR]
[TD="width: 25"][IMG]http://tldp.org/LDP/abs/images/caution.gif[/IMG][/TD]
[TD]Note the [whitespace]("http://tldp.org/LDP/abs/html/special-chars.html#WHITESPACEREF")               framing the **=.**
**[B]if [ "$a"="$b" ]** is               *not* equivalent to the               above.[/B][/TD]
[/TR]
[/TABLE]

==is equal to
**if [ "$a" == "$b" ]**
This is a synonym for =.


---

### Post by HiImTye on 2013-05-25
remove the \n and give whitespace and it should work, i.e.
```
test=$(echo -e "2\n")
if [ "$test" = "2" ]; then echo 2
elif [ "$test" = "2\n"]; then echo 2\n
else echo neither
fi
```

---

### Post by Vaphell on 2013-05-25
on an unrelated note:  you don't have to embed *seq* command because bash can do this natively
```
for i in {1..5}
```

---

