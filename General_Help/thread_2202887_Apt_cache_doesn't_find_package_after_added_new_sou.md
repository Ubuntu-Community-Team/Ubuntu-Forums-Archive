---
title: "Apt cache doesn't find package after added new source."
date: 2014-01-31
forum: General Help
---

### Post by mario-s-s-areias on 2014-01-31
Hello guys, 


I have a question, but I'm not sure what is the problem. 

I am adding a new apt repo for my app. The app is called "**bla**". 

If I look at **/etc/apt/sources.list.d** I see a file called **bla.list **with the right content.

Then I run **apt-get update **and then I run [B]apt-get install bla. 
[/B]
Now where the problems begin. If I get a new installation of the Ubuntu 12.04 server, that works perfectly. However, I got a VM that already have some configuration and it doesn't install. If I run **apt-cache show bla **it throws an error telling it cannot locate the package. Which makes think, there is some configuration missing, but I don't know where to start. If I run **apt-cache dump **it shows the right repo, but it shows size as 0. 


I would like to know if there is any commands to try to understand this problem and why it is failing in this specific VM. 



Thanks!


Mário

---

### Post by varunendra on 2014-02-01
Welcome to the forums Mário !

Is the version of Ubuntu in the VM also 12.04? Compare the outputs of -
```
lsb_release -d
uname -mr
```
If these are different, maybe the repository doesn't support the version in the VM.

---

