---
title: "Help writing a script that will notify me when a filesystem's size hits a threshold"
date: 2013-05-20
forum: General Help
---

### Post by porkroll on 2013-05-20
I am trying to write a script that will email me whenever a filesystem reaches a certain Use% (say 90% and above).  So far I have come up empty.  Thanks so much in advance.

---

### Post by prodigy_ on 2013-05-20
[http://ubuntuforums.org/showthread.php?t=2137419](http://ubuntuforums.org/showthread.php?t=2137419)

---

### Post by porkroll on 2013-05-21
You rock!  Thanks

***edit*** The script didn't work I am guessing it is because the way df displays the filesystems because of our labeling.

Filesystem           1K-blocks      Used Available Use% Mounted on/dev/mapper/VG00-LV00
                       2015568    748792   1165196  40% /
/dev/mapper/VG00-LV01
                       2015568    804840   1109148  43% /home
/dev/mapper/VG00-LV02
                       1007768     17756    939224   2% /tmp
/dev/mapper/VG00-LV04
                       1007768    172308    784672  19% /var
/dev/sda1               147801     28452    111717  21% /boot
tmpfs                   517344         0    517344   0% /dev/shm
/dev/mapper/VG00-LV03
                       6111816   3876156   1927644  67% /usr

Here is the script slightly modified:
```
#!/bin/bash


warn_types=([85]=WARNING [95]=CRITICAL)
subject="ALERT: Disk space utilization $(hostname)"
email="xxxxx"


# Add filesystem types below as needed
fs_types="ext|ntfs|cifs|fuseblk"


while read line; do
        perc_used=$(df $line | awk -F" " 'NR>1{print $5}')
        for i in 95 85; do
                if [ ${perc_used%\%} -gt $i ]; then
                        echo "${warn_types[$i]}: $line is $perc_used full" | \
                                # insert mail sending command here
                                # e.g. mailx -A accountname -s 'subject' address@example.com
                                mail -s "$subject" "$email"
                        break
                fi
        done
done < <(mount | grep -E "type $fs_types" | cut -d' ' -f 3)

```

When I run it I get the following output:
./diskcap.sh
./diskcap.sh: line 13: [: /: integer expression expected
./diskcap.sh: line 13: [: /: integer expression expected
./diskcap.sh: line 13: [: /home: integer expression expected
./diskcap.sh: line 13: [: /home: integer expression expected
./diskcap.sh: line 13: [: /tmp: integer expression expected
./diskcap.sh: line 13: [: /tmp: integer expression expected
./diskcap.sh: line 13: [: /var: integer expression expected
./diskcap.sh: line 13: [: /var: integer expression expected
./diskcap.sh: line 13: [: /usr: integer expression expected
./diskcap.sh: line 13: [: /usr: integer expression expected

Any thoughts?

---

### Post by porkroll on 2013-05-21
Bump

---

### Post by Vaphell on 2013-05-21
```
for i in 95 85; do
```
given the thresholds are defined already in the array ( *warn_types=([85]=WARNING [95]=CRITICAL)* ) i'd replace it with
```
for i in **${!warn_types[@]};** do
```
so the proper values for the loop are always extracted from the array (no risk of mismatch in case of sloppy code edits)
**edit:** i didn't consider order in which the array indices are produced, for the time being numbers should stay :-)


about the main problem:
protip: When in doubt, spam echo with everything that moves :-)
echo $perc_used to see if you get integer numbers from that. Apparently you don't so you print out the variables to be sure what you get.
Also check what you get from **df /** alone and see if the % is 5th in order.

This should avoid the hassle altogether
```
perc_used=$(df $line | **grep -Po '[0-9]+%' **)
```
it should look not for 5th 'word' whatever that might be, like awk did, but for 'digits%' explicitly

[B]
edit2:[/B]
```
#!/bin/bash

warn_types=( [85]="WARNING" [95]="CRITICAL" )
fs_types="ext|ntfs|cifs|fuseblk" # Add what you need
subject="ALERT: Disk space utilization $(hostname)"
email="xxxxx"

while read line
do
  perc_used=$( df $line | grep -Po '[0-9]+%' )
  x=''
  for i in ${!warn_types[@]}
  do
    [ ${perc_used%?} -ge $i ] && x=$i
  done
  [ -n "$x" ] && echo "${warn_types[$x]}: $line is $perc_used full" | \
                 mail -s "$subject" "$email"
done < <( mount | grep -E "type $fs_types" | cut -d' ' -f 3 )



```

---

