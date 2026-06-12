---
title: "Very basic AWK regex query."
date: 2018-04-03
forum: General Help
---

### Post by uncle-c on 2018-04-03
I often used awk way back in the Unix days of the late 80s but have been neglecting it over the past 20 years or so. Decided to refresh my AWK skills by reading some online tutorials. There is one very very basic question which needs answering and it's driving me potty !

```
 $ cat awkfile 

tcp        0      1 192.168.1.12:33364       185.29.132.92:443       FIN_WAIT1  
tcp        0    281 192.168.1.12:42964       216.58.206.130:443      FIN_WAIT1  
tcp        0      1 192.168.1.12:51353       66.135.209.36:443       FIN_WAIT1  
tcp        0      1 192.168.1.12:51333       23.56.185.233:443       FIN_WAIT1  
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN   

```


**Example 1 **
```
$ awk ' $1 ~ /[tcp]/ { print $0 } ' awkfile
tcp        0      1 192.168.1.12:33364       185.29.132.92:443       FIN_WAIT1  
tcp        0    281 192.168.1.12:42964       216.58.206.130:443      FIN_WAIT1  
tcp        0      1 192.168.1.12:51353       66.135.209.36:443       FIN_WAIT1  
tcp        0      1 192.168.1.12:51333       23.56.185.233:443       FIN_WAIT1  
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN   

```

**Example 2**
```
$  awk ' $1 ~ /[^tcp]/ { print $0 } ' awkfile

tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN   

```

The output in **Example 1 ** is as I expected ie if field 1 contains 'tcp' then print the entire line. However, in **Example 2 ** when there is a  '^' in front of 'tcp' the output shows lines with tcp6 in field 1. Why is this the case instead of no lines being printed  ?

---

### Post by Holger_Gehrke on 2018-04-04
I think you misunderstand the meaning of the brackets. They match **one character** which is a member of **the set inside the brackets**. The '^' at the beginning of the set inverts it. So '[tcp] matches any field that contains a 't', a 'c' or a 'p', while '[^tcp]' matches any character that is not a 't', a 'c' or a 'p'. The '6' is not a 't', a 'c' or a 'p', so 'tcp6' is a match.

Holger

---

