---
title: "Login looping, guest account works, .Xauthority file missing"
date: 2014-08-16
forum: General Help
---

### Post by sam69 on 2014-08-16
Hello,

I recently had to reset my user password through root in recovery mode. Since I did so, I have been unable to log into my account as the login screen simply returns back to itself with only a brief pause and a blank screen. I changed nothing else and edited no files since it last worked. After searching through various forum posts and questions on the topic, I have tried the following in order to resolve the problem:

```
sudo chown [username]:[username] .Xauthority
```

```
sudo mu .Xauthority .XauthorityBak
```

```
sudo apt-get install --reinstall xorg
```

```
sudo rm /home/[username]/.Xauthority
```

```
sudo chmod a+wt /temp
```

```
dpkg -reconfigure lightdm
```

```
sudo mv ~/.Xauthority ~/.Xauthority.backup
```

```
sudo service lightdm restart
```

None of these have resolved the issue and I am still stuck. When I try to locate the .Xauthority file I am informed that no such file exists, or is missing. It is rather important that I regain access to a file which is saved in my home/[username] folder. If I could access that folder somehow while on the guest account by giving myself the authorisation I would not mind having to reinstall but would prefer not to.

Thanks in advance for your help and advice.
Sam

---

### Post by deadflowr on 2014-08-16
You would not need to sudo in recovery mode as you would already be running as root.
However, if in the recovery mode, you would need to run the full path to the file, or else it will only be changing, or adding, it to the root home directory, and not your home directory. If that makes sense.

That said, what does 
```
ls -la
```
say?
is there an entry for the Xauthority file?

Also, if you creating the system with encrypted filesystem look at this answer for possible help.
[http://ubuntuforums.org/showthread.php?t=2239811](http://ubuntuforums.org/showthread.php?t=2239811)

Of course, though, I am just spittballing here, seeing what might stick as to a solution...

---

