---
title: "I can not login in my xubuntu 18-10 after trying to get a second &quot;x&quot; session"
date: 2018-10-28
forum: General Help
---

### Post by ruben-alfonsin on 2018-10-28
Hi
After trying to get a second "x" session working from a console (w/out succces)
now I can not login in my xubuntu 18-10

I get the login window (which should not be because it was configured to not ask password)
The user is ok, then I write my (old and well know) password
get by 2 seconds a black screen and then the login window again 

No error message appears (if I intentionally write a bad password, get a message saying that, with no black screen)
I can retry and the same happens again and again.

I have other partitions with windows and another xubuntu 18-04 installed. Both work fine.

I have changed session to xfce with same results
I have deleted displays.xml as sugested in an old post with no results.
I will wait for your help.

---

### Post by ruben-alfonsin on 2018-10-29
The solution is here:
[https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop)

I cause the problem issuing "***sudo* startx** " ; Never uso sudo with startx  (I know now)
Thanks anyway

---

