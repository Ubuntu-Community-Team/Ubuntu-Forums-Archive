---
title: "Is it possible to run a .sh file as root?"
date: 2006-12-23
forum: General Help
---

### Post by rctxtreme on 2006-12-23
Is it possible to run a .sh file as root? If so, how?

---

### Post by ~LoKe on 2006-12-23
```
sudo sh file.sh
```

---

### Post by iamhugeinjapan on 2006-12-23
Sure

```
 sudo ./scriptname.sh
```

---

### Post by 23meg on 2006-12-23
Assuming the script is in your current directory,```
sudo ./script.sh
```

---

### Post by dbott67 on 2006-12-23
Or
```
sudo su
```
followed by the desired command.

-Dave

---

### Post by kidders on 2006-12-23
Hi there,

Although your question has been answered :-) it's worth mentioning that running a shell script as root is extremely dangerous, so be sure you trust it! I wonder what would happen if the first line in it was **rm -Rf /home**.

---

### Post by digital_me on 2006-12-23
> **kidders said:**
> Hi there,

Although your question has been answered :-) it's worth mentioning that running a shell script as root is extremely dangerous, so be sure you trust it! I wonder what would happen if the first line in it was **rm -Rf /home**.

Or even worse, **rm -rf /**...

---

### Post by rctxtreme on 2006-12-24
Let's see... the shell script is from CodeWeavers... is that unsafe?

edit:
> The '/home/richard' directory does not belong to you.
Point $HOME to your home directory and try again.

Oh, great. Wow, linux IS hard to use, even though I am good with computers...

---

### Post by kidders on 2006-12-24
Ohhh, you mean the script isn't something you wrote yourself? Since shell scripts are so open to malicious interference, running one as the superuser is a very odd thing for a software company to ask of you. A rough equivalent from the Windoze world might be maybe letting a web page run an ActiveX script. It can be quite an act of trust!

The problem you're having is that by typing **sudo ./script.sh**, parts of your own working environment persist, even though the script is running with root privileges. You can check by typing something like **sudo echo $HOME**, to see if you get "/home/richard" or "/root", which you might be expecting.

dbott67 suggested using **sudo su** which is subtly different.

> Wow, linux IS hard to useHehe, it can take a little time to get to grips with its security model, but rest assured, it tends to do things the way it does for very good reasons!

---

### Post by rctxtreme on 2006-12-24
I wasnt asked to do so by codeweavers its just that (wtf happened to my keyboard its treating everything like im pressing shift with it) for some reason if i install a program the menu for codeweaver apps doesnt appear so i thought maybe its because it doesnt have root stuff because it worked with dapper!

---

