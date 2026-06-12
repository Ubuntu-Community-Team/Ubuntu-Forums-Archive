---
title: "reading the results of a command into a bash script"
date: 2014-10-16
forum: General Help
---

### Post by jrs2 on 2014-10-16
I want to take the results of this command:

cat /sys/class/net/eth1/operstate

and use that as a variable in a bash script as a part of a if/then/else statement.

Is this possible? How would I accomplish this? The results will either be 'up' or 'down'

Basically,

-----------------------------------------------------------------------
read the results of cat /sys/class/net/eth1/operstate

if results = 'up', then do this....

else....then do this

---

### Post by whitesmith on 2014-10-16
```
cat /sys/class/net/eth1/operstate > retcode
```
will get the output into a file called retcode in pwd. Now use bash to read the file and place its contents into a variable. If you take a long view the solution is quite trivial. Regards.

---

### Post by Vaphell on 2014-10-16
```
operstate=$( cat /sys/class/net/eth1/operstate )
if [[ $operstate == 'up' ]]
then
    ...
else
    ...
fi
```

---

### Post by jrs2 on 2014-10-16
Thanks Vaphell! Just what I was looking for. Works great.

---

