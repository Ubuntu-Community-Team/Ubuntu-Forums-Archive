---
title: "Ubuntu shows high CPU usage while using flash"
date: 2015-04-27
forum: General Help
---

### Post by anwar4 on 2015-04-27
Hello, 

I have laptop Dell n4010  with Ubuntu 14.04. It pretty good for the most of my job. But it acts weird (high CPU usage) under the following condition. can you help find the reason behind the issues?

1. while playing youtube videos
2. while using google video hangout
3. while using facebook (this is good thing for me :p I won't spend much time on FB due to this)

I can use YT/FB/hangout for ~5-10 minutes, But it will shows high CPU usage, heating and screen will get stuck after that. 

Can you help me to find the reason?

Here is little info about my system

```
lspci -nn | grep VGA 
```

response

```
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 18)



```

thanks in advance

---

### Post by dragonfly41 on 2015-04-27
My guess is that this is due to flash plugin (used by sites you refer to)

Read here [http://ubuntuforums.org/showthread.php?t=2236146](http://ubuntuforums.org/showthread.php?t=2236146)

---

