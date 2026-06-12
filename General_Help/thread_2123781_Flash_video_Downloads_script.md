---
title: "Flash video Downloads script"
date: 2013-03-08
forum: General Help
---

### Post by Jacob-Gates on 2013-03-08
A very smart friend of mine wrote a script (at least I think HE wrote it, could be wrong) that when ran in terminal it copies any downloaded flash video to the directory the script is in. It worked on everything for the longest time but suddenly doesn't work anymore. I think it might be because when he gave it to me it was with Ubuntu 11.04 and now I have 12.10. Here is the code, if someone could look over this and check to see if something would keep it from working in 12.10 I would be very appreciative.

```
#!/bin/bash

args=("$@")


args=`echo $args | sed 's/[/]$//'`


pids=`eval pgrep -f flashplayer`
for pid in $pids
do
lsoutput=$(lsof -p $pid | grep '/tmp/Flash[^ ]*')


IFS=$'\n'
for line in $lsoutput; do
lsout1=`echo $line | awk '{print "/proc/" $2 "/fd/" $4}' | sed 's/[rwu]$//'`
lsout2=`echo $line | awk '{print $9}' | awk -F '/' '{print $3}'`


if [ -n "$args" ];then
if [ -d $args ]; then
echo "Copying $lsout2 to $args/"
eval "cp $lsout1 $args/$lsout2.flv"
else
echo "The directory \"$args\" doesn't exist"
break
fi
else
echo "Copying $lsout2"
eval "cp $lsout1 $lsout2.flv"
fi


done
done
```

when I run the bash it doesn't output anything in my terminal:
```
$ ./getFlash.bash 
$ 
```

that is literally all I get. Also, when it did work I had to do a couple of commands to be able to play the file which is fine. I just didn't want someone thinking that was my problem. Thank you for any help anyone can give me.

---

