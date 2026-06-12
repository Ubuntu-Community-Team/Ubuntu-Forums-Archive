---
title: "bash script for checking network computers"
date: 2006-11-08
forum: General Help
---

### Post by pontifex3 on 2006-11-08
hi im currently writing a bash script to be able to find other users in my schools computer network so im doing a for loop so i can ping every computer but i havent found a way to make the computer know if the ping sent the packages or not so i have to look at all the packages and also if i want to know which user is connected to the computer i have to ssh it and type who, so i wanted to know if anybody knows a better way of remotely knowing who is logged on to the computer i wish to know and if theres a better way to know if the computer is logged in than using ping o the correct way of making ping work without verbose and just answer something like a 1 or 0 thanks

---

### Post by pontifex3 on 2006-11-08
ok i think im using the ssh lab$i who for checking who is on the computer i want to know so know im trying to find if theres any way to save my password somewhere (hashed, im not planning to put it on plaintext) so ssh wont ask for it everytime it connects to a computer, and still the issue of how to make ping return pretty values readable for the computer

---

### Post by yota on 2006-11-08
Hi, ssh supports RSA and DSA key authentication.

Have a look at [http://www.zettai.net/Support/Howto/sshKeyHowto](http://www.zettai.net/Support/Howto/sshKeyHowto) for an HowTo

or at 'man ssh-keygen' for command reference.

---

### Post by yota on 2006-11-08
Every command return a value in a special variable $? called "return code" that tells how the execution went, you can use it to guess if the host exists or not:
```

yota@linbook:~$ ping doesnotexist
ping: unknown host doesnotexist
yota@linbook:~$ echo $?
2
yota@linbook:~$ ping -c 1 localhost
PING localhost.localdomain (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=1 ttl=64 time=0.050 ms
--- localhost.localdomain ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.050/0.050/0.050/0.000 ms
yota@linbook:~$ echo $?
0
yota@linbook:~$

```

---

