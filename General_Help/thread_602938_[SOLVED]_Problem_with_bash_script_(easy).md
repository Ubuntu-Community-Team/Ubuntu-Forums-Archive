---
title: "[SOLVED] Problem with bash script (easy)"
date: 2007-11-04
forum: General Help
---

### Post by Walter_Crankite on 2007-11-04
Following works: 

used1=`df -h | grep /mnt/Cinema | awk '{print $3}'`
size1=`df -h | grep /mnt/Cinema | awk '{print $2}'`
ava1=`df -h | grep /mnt/Cinema | awk '{print $4}'`
mount1=`df -h | grep /mnt/Cinema | awk '{print $6}' | cut -c6-20`
#
echo -e "$mount1 \t \t $used1 /$size1 \t $ava1"


Following doesn't work: 

used1=`df -h | grep /mnt/Cinema | awk '{print $3}'`
size1=`df -h | grep /mnt/Cinema | awk '{print $2}'`
ava1=`df -h | grep /mnt/Cinema | awk '{print $4}'`
mount1=`df -h | grep /mnt/Cinema | awk '{print $6}' | cut -c6-20`
#
X1=`$mount1 \t \t $used1 /$size1 \t $ava1`
echo "$X1"
echo $X1 



Why doesnt it print this?

Greetz,
Walter

---

### Post by bakeneko on 2007-11-04
In bash, when you enclose something in `backticks` bash will execute its contents are returned. So, in the line
X1=`$mount1 \t \t $used1 /$size1 \t $ava1`
bash is trying to execute whatever string is in your $mount1 variable. What you probably want to do is something more like this:
X1="$mount1 \t \t $used1 /$size1 \t $ava1"
echo -e "$X1"

---

### Post by Walter_Crankite on 2007-11-04
Cool
Thanks mate

Greetz,
Walter

---

