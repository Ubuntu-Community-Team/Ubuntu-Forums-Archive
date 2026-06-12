---
title: "Running programs after logging off"
date: 2013-04-02
forum: General Help
---

### Post by chuckie86 on 2013-04-02
I need some help with a thing, think it should work but don't know how. 

I'm running a vps with sabnzb on it, and when i log out my vps, it's keep downloading and unrarring. Now i want to try and do it the other way.
I'm using newspost to upload some files, which i have rarred and parred in one command. I logon to my vps with putty, then type the command for uploading,
it starts, but when i disconnect putty, it stops uploading. Is there a way that my vps will keep uploading even when i'm not logged in with putty?

---

### Post by Impavidus on 2013-04-02
Maybe **nohup** is what you need. Have a look at the manual.

---

### Post by chuckie86 on 2013-04-04
Thx man, that did the job!

---

### Post by faucets xp on 2013-04-05
Thanks. Can Nohup  work? I will try.

---

### Post by chuckie86 on 2013-04-08
I'm trying to rar and par a file with the nohup command. 
Rar command && par command, like that. If i place nohup rar command && nohup par command, it only does the rarring part. Can i make it do both?

---

### Post by Impavidus on 2013-04-08
What happens is this:
- Give command **nohup rar command && nohup par command**
- Shell starts the **nohup rar command**
- **rar command** is started
- You log off
- SIGHUP is send to the remaining processes. rar has been started with nohup, and therefore ignores the SIGHUP. The shel, however, terminates on recieving the signal.
- rar terminates. The shell had been waiting for that moment to start the par command, but won't do that, as the shell is no longer running.

The solution is to run the shell with nohup. The way to do so is```
nohup bash -c 'rar command && par command'
```(I think. Never tried things like that myself.)

---

### Post by markbl on 2013-04-08
Consider using tmux or screen instead.

---

### Post by chuckie86 on 2013-04-09
> **Impavidus said:**
> What happens is this:
- Give command **nohup rar command && nohup par command**
- Shell starts the **nohup rar command**
- **rar command** is started
- You log off
- SIGHUP is send to the remaining processes. rar has been started with nohup, and therefore ignores the SIGHUP. The shel, however, terminates on recieving the signal.
- rar terminates. The shell had been waiting for that moment to start the par command, but won't do that, as the shell is no longer running.

The solution is to run the shell with nohup. The way to do so is```
nohup bash -c 'rar command && par command'
```(I think. Never tried things like that myself.)

Will try that, thx for that!

---

### Post by chuckie86 on 2013-04-09
> **markbl said:**
> Consider using tmux or screen instead.

Can you just download it in file manager?

---

