---
title: "sources.list"
date: 2007-01-19
forum: General Help
---

### Post by mikeymouse on 2007-01-19
Can anyone tell me how to replace sources.list with sources.list.save?
 I don't understand sudo, so if you could give me the coding necessary i would greatly appreciate it.
Thanks mikeymouse

---

### Post by jimbob on 2007-01-19
sudo cp sources.list.save sources.list

---

### Post by taurus on 2007-01-19
> **jimbob said:**
> sudo cp sources.list.save sources.list

And make sure you are in /etc/apt directory first.

```
cd /etc/apt
```

---

### Post by mikeymouse on 2007-01-19
when i try that coding here is what comes up:
cp: cannot stat 'sources.list.save' no such file or directory

I know there is because i am looking at it. 
any further ideas?
 thanks mikeymouse

---

### Post by taurus on 2007-01-19
```
sudo cp /etc/apt/sources.list.save /etc/apt/sources.list
```
And if you still get the same error message, then paste the output of this command here.

```
ls -la /etc/apt
```

---

### Post by jimbob on 2007-01-19
May I suggest that it is not in the directory you think it is in.

do this:

  sudo cd /
  sudo find . -name sources.lis\*

---

### Post by mikeymouse on 2007-01-19
Thankyou that worked just fine. I appreciate all.
 The problem started when i tried to download and install automatix.
 I did type in what the Automatix page said but looks like it messed up my sources list.
 I am all back and running fine again and thankyou..
mikeymouse

---

### Post by mikeymouse on 2007-01-19
One day i may understand 'sudo'
 But i sure miss 'root'

---

### Post by taurus on 2007-01-19
If you still want to use automatix, let me see your /etc/apt/sources.list after you've modified it.  Shouldn't be too hard to figure out what goes wrong.

```
cat /etc/apt/sources.list
```

p.s.  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

