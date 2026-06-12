---
title: "ubuntu 22.04 very slow"
date: 2022-06-12
forum: General Help
---

### Post by dwssapresnak on 2022-06-12
ubuntu runs extremely slow, even though the computer hardware is good, it runs many times faster when you install it in a very slow virtual environment, the terminal hangs once in a while

---

### Post by tea for one on 2022-06-12
Can you run the script from this site [https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)
Post the info or pastebin link in this thread and, hopefully, someone will be able to offer advice

---

### Post by mIk3_08 on 2022-06-12
> **dwssapresnak said:**
> ubuntu runs extremely slow, even though the computer hardware is good, it runs many times faster when you install it in a very slow virtual environment, the terminal hangs once in a while
I'm not an expert here nor pretend to be an expert of Linux Ubuntu Operating System  I always offer my help in this community voluntarily based on what I've experience using this Linux Ubuntu Operating System.
Please run this command below and show us the results here in thread. Paste it here wrap with code
```
hostnamectl status
```
This command below will allow you to show us your system machine hardware specifications. Please paste the results here in this thread wrap with code. 
```
lshw
```
Lastly, this command will show us your system logs. Please paste the results here in this thread wrap with code. 
```
cat /var/log/syslog
```
Good Luck Regards and Cheers.

---

### Post by mIk3_08 on 2022-06-13
> **tea for one said:**
> Can you run the script from this site [https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)
Post the info or pastebin link in this thread and, hopefully, someone will be able to offer advice
Thanks tea for one for this link. This will help a lot as it will give us all we need to the system information in just one execution of commands. 
One thing just to make it clear if you run the command directly to the terminal
```
username@username-machine:~$
```
This will directly create the system info text file to your "Home folder"
But if you run this command with the download folder address
```
username@username-machine:~/Downloads$
```
This will directly create the system info text file to your "Downloads folder"
Post the info or pastebin link in this thread. Regards and cheers.

---

### Post by HermanAB on 2022-06-13
This is Linux.  You need not sit and wonder why the performance is bad.  Run *top* or *htop* and see what is chewing up the CPU and *kill* the offending process.

---

