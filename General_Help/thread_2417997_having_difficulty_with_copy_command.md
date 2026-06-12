---
title: "having difficulty with copy command"
date: 2019-04-30
forum: General Help
---

### Post by sammy11 on 2019-04-30
yes I am fairly new to this anyway I want to install a av, I have downloaded the installer and I need to copy it to /opt/f-prot (I guess) anyway I don't know what I am doing and need help with this so
someone help me out please and thanks for help

---

### Post by TheFu on 2019-04-30
Sorry. I don't understand the question.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a beginning book on Linux.

I can only guess that you are having permissions and command issues.  All Unix systems are multi-user.  Every process and every file/directory has an owner and a group.  Only the owner can modify the permissions to allow other users access. 
> I want to install a av
Isn't clear. Know idea what that means.  Usually, programs in Ubuntu shouldn't be downloaded directly.  Use the package manager to install 99.9999% of the programs you need. Very few programs would be installed into /opt/ - usually that is for commercial software that costs $1000 or more.

If you are really new to Unix systems and Linux, then an overview might be helpful: [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) explains the major differences between Windows and Linux from a new-user perspective. It explains the GUIs, package management, etc.

---

### Post by Rubi1200 on 2019-04-30
F-Prot has an antivirus solution for Linux. But, there is no need to use antivirus on Linux unless you are sharing files with Windows or using Wine, for example.

Please read this link carefully [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

I have been using Linux for more than 13 years and have never used an AV or anything like that so please consider whether you really need it.

---

### Post by sammy11 on 2019-05-01
thanks for all the help, I am a go-getter and a hands on type of person and have figured it out but the linux comands book is a good thing this one is solved!

---

### Post by TheFu on 2019-05-01
> **sammy11 said:**
> thanks for all the help, I am a go-getter and a hands on type of person and have figured it out but the linux comands book is a good thing this one is solved!

"av" means anti-virus?  See how far out I am from Windows?  There are 2 reasons to run AV on Linux.  
a) You work on a LAN and share files with Windows people all-the-time.
b) Your professional E&O insurance mandates that all computers have current, up-to-date AV software and signatures.

If you are on the same LAN, but don't share documents with Windows computers, I wouldn't bother with AV.
I did have to install AV on all our servers to maintain our E&O insurance.  I attempted to explain why that was dumb for non-Windows companies, but they insurance people weren't going to change their policy and honestly weren't qualified to make the determination, at least not the 5 people I spoke with trying to explain.  They kept saying "it is industry best practices" - which I agreed with ON WINDOWS.  How many AV installs do you think Google has to protect their servers?  I bet it maps to the number of Windows servers they have 1-for-1.  On Linux, I bet they wrote their own and don't call it AV, since it scans for any security issue, not just virus.

---

