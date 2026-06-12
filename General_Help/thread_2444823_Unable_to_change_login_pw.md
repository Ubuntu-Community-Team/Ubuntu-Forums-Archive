---
title: "Unable to change login pw"
date: 2020-06-04
forum: General Help
---

### Post by ubuntini2 on 2020-06-04
Ubuntu MATE 18.04 LTS. Have forgotten my login PW so have attempted to change it following these directions [https://itsfoss.com/how-to-hack-ubuntu-password/](https://itsfoss.com/how-to-hack-ubuntu-password/)

Boot into recovery mode
Get into shell prompt
$ mount -rw -o remount /
$ passwd jim
$ new password
$ new password
$ exit
Then booted normally. However it didn't work. My new pw that is.

Am I at least correct in assuming my username is correct?



What should I try next? Any feedback welcome!

[ATTACH=CONFIG]286095[/ATTACH]

---

### Post by ubuntini2 on 2020-06-04
So I assume my issue is disk space. I logged into text terminal and freed up some space in /home but still showing 100% usage in / (root)


What is the safest way to free up space in root from the text terminal?

---

### Post by guiverc on 2020-06-05
Also asked at [https://askubuntu.com/questions/1247049/cant-change-login-pw](https://askubuntu.com/questions/1247049/cant-change-login-pw)

---

### Post by ActionParsnip on 2020-06-05
Make a new user and become that user using su from root. Can you then su to jim using the password you set?

---

