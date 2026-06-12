---
title: "How to filter users grep"
date: 2016-04-09
forum: General Help
---

### Post by luco2 on 2016-04-09
Hello, 

I need your help :-) I have following query: 

```
cat users | while read x; do echo "$x";  chage -l "$x" | grep 'Password expires' | grep '2017'; done > user2 
```

where 'users' is /etc/passwd (usernames) 

I want to filter only users where password will expire in 2017. Above query is working but also put in file 'user2' others users where password not expire in 2017. I want only expire users in file 'user2'.
for example: I want only 'vera' user in file 'user2' because her password expired in 2017 (also without word Password expires) I want only user name in this file 

```
postfix
ntp
haldaemon
gdm
pulse
sshd
tcpdump
luco
vera
Password expires                    : Apr 29, 2017
```


Like this 

```
vera

```

I don't know how to filter this :(

---

### Post by SeijiSensei on 2016-04-09
How often to you need to do this? How many users do you have?  Frankly I suspect it would be just as fast to do this manually if you only need to do it one time for a small group of users.

---

### Post by steeldriver on 2016-04-09
How about skipping the echo and using grep's --label?

```

while read x; do chage -l "$x" | grep -H --label="$x" 'Password expires' | grep '2017'; done

```

---

