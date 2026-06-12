---
title: "File sharing between Ubuntu and Windows over internet"
date: 2008-04-02
forum: General Help
---

### Post by snkngshps on 2008-04-02
Are there any programs that will allow me to share files between Ubuntu and a Windows machine over the internet? This is not a local connection. Basically I want to be able to access files from my home computer (running Ubuntu Hardy) while at my work computer (running XP). I remember a while back when I was using windows on both machines I found a few programs where you could set up a shared folder and as long as both computers had this program running and logged in you could swap files back and forth. Is there anything like this for Ubuntu?

---

### Post by justleen on 2008-04-02
i would suggest installing openssh-server on the ubuntu side, and use WinSCP on the windows side.

---

### Post by zeronothing on 2008-04-02
One way I have done it is by using Hamachi. Its a simple vpn type program that you can run and it allows you machines to look like their on the same local network. This allows you to copy back and forth between both machines like you were on your home network. you can install hamachi on windows, mac os, and linux.

---

### Post by xelapond on 2008-04-02
You could also try sFTP which is a little harder to set up, but easier to use.  This would also allow you to go both(push and pull both) ways, wheras SSH will only allow you to push and pull from one side, not both.

Alex

---

### Post by xelapond on 2008-04-02
I would also recommend using Hamachi as zeronothing said, because otherwise you have to open ports in routers, stuff you probably can't do at work.

---

### Post by justleen on 2008-04-02
> **xelapond said:**
> You could also try sFTP which is a little harder to set up, but easier to use.  This would also allow you to go both(push and pull both) ways, wheras SSH will only allow you to push and pull from one side, not both.

Alex


We use WInSCP to manage our whole server park, and it works both ways.

Yes, there is an issue with speed permance when pushing large file, but other then that, there no reason to use sFTP over SSH/SCP.

If you want sFTP from home to work, you will need a serve ron the work side, just you will need an SSH serve ron the work side if you want SSH from home to work.

For just accessing your system@home  from work, ssh works fine.

---

### Post by xelapond on 2008-04-02
> We use WInSCP to manage our whole server park, and it works both ways.

How do you SSH into a windows machine?  As far as I know there is no SSH server for windows, but I havn't used it for a few years now.

If you only wanted to do SFTP push and pull from one side then you only need one server,  If you are going to do that though, just use SSH.  All SFTP is is FTP over SSH, so SCP would be much easier to set up, it would just have some minor speed compromises.  Either way you will still have to forward ports, and Hamachi will work with any of the above mentioned methods.  If you use Hamachi in conjunction with any of these methods you will not need to forward ports.

Good Luck!

Alex

---

### Post by snkngshps on 2008-04-02
Thanks guys! I think Hamachi was what I was looking for. I actually think that was the program I was using a while back anyways. Thanks again!

---

### Post by snkngshps on 2008-04-02
Ok I have another quick question. I'm at work now, using remote desktop to set up hamachi on my computer at home. I'm following a guide and I have to log out and log back in for part of it, but that would obviously disconnect me from remote desktop and I wouldn't be able to log back in. Is there a way reset the session without fully logging out? Or a way to remote connect back in after logging out?

---

### Post by zeronothing on 2008-04-02
if you are using remote desktop and you connect to the computer on the other end. you cnd log out of the machine on the other end and still remote back into it. The remote desktop connection services is running in the background. you can even restart the machine on the end and remote back into it after it boots back up. if you disconnect from the remote desktop and not log off, it will keep the session up so when you reconnect again you are back to where you left off.

---

### Post by justleen on 2008-04-02
> **xelapond said:**
> How do you SSH into a windows machine?  As far as I know there is no SSH server for windows, but I havn't used it for a few years now.





i'd use cygwin with openssh.. :)

---

