---
title: "generate random number inset into text file"
date: 2021-02-27
forum: General Help
---

### Post by youmustnot on 2021-02-27
Hello all. 

I'm trying to generate a random number between 1/2147483647 and insert/replace an existing number within a text file
I just cant get it to work ?

```
newseed=$((1 + RANDOM*RANDOM % 2147483647))
sed -i -e '17c\seed="'"$newseed"'"' /home/test/lgsm/config-lgsm/rustserver/rustserver.cfg
```

The file is located at ~ /home/test/lgsm/config-lgsm/rustserver/rustserver.cfg
and within that file i have a filed called seed=""

```
ip="xx.xx.xx.xx"
port="28017"
rconport="28018"
appport=28083
rconpassword=""
rconweb="1" # Value is: 1 for the Facepunch web panel, Rustadmin desktop and Rustadmin Online; 0 for RCON tools like Rusty.
servername="test"
maxplayers="1"
salt="" # range: unknown, used to recover a known setting from an existing map.
worldsize="3000" # default: 3000, range: 1000-6000, map size in meters.
saveinterval="300" # Auto-save in seconds.
tickrate="30" # default: 30, range: 15-100.
seed="2042821"
```

I want to be able to run a cronjob that will change this value in the text file, currently i do this manually 

Thanks for any pointers!

---

### Post by dinkidonk on 2021-02-27
Arithmetic expression look wrong, try:

```
newseed=$((1 + (($RANDOM * $RANDOM) % 2147483647)))
```

---

### Post by youmustnot on 2021-02-27
thanks for your help. I have made the changes however It still fails to write to the file

```
newseed=$((1 + (($RANDOM * $RANDOM) % 2147483647)))
sed -i -e '17c\seed="'"$newseed"'"' /home/rust5/lgsm/config-lgsm/rustserver/rustserver.cfg
```

---

### Post by dinkidonk on 2021-02-27
Try this then:

```
sed -i 's/seed=.*/seed="'$newseed'"/' /path/to/file.txt
```

---

### Post by youmustnot on 2021-02-27
hey [COLOR=#000000]dinkidonk

Thanks for that it's working as expected now [/COLOR]

---

### Post by dinkidonk on 2021-02-27
Great! Please mark the thread as solved.. :)

---

