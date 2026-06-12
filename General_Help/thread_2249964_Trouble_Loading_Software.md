---
title: "Trouble Loading Software"
date: 2014-10-25
forum: General Help
---

### Post by Curbside Jimmy on 2014-10-25
I used to be able to load software with Ubuntu. Now, sometimes it won't recognize my password. Other times I get a message that I don't have the authority to load software. 

Can anyone tell me in laymans terms how to get around this ussue?

Is there a way to disable these kinds of security features?

I don't need them and they are a constant headache.

---

### Post by JazzPotato on 2014-10-25
Hi there,
Are you attempting to install software through the "ubuntu software center" or from a .deb package you downloaded from the internet? Which package in particular are you trying to install? 
Also, there is no way to get around having to input your password when install a package, it's an integral part of how the operating system is designed. And even if there were ways to get around this security feature, you wouldn't want to because you'd open up security vulnerabilities giving anyone the ability to install software (*ahem* windows)

---

### Post by Curbside Jimmy on 2014-10-25
GIMP from the ubuntu software page. I don't mind typing a password. I just need to find a way to get things done one my own computer. 
I do have a password. I just reset it. The password doesn't seem to work for loading software. Somehow I need to give myself the authority to install software, I guess. I am guessing it is something like runing windows as administrator. 

I am trying hard to get away from windows.

---

### Post by JazzPotato on 2014-10-27
Hi there curbside Jimmy,
Just a bit of background information, software installation and updates are managed in ubuntu through a program called **apt**. "apt" is a **package manager **which acts like a search engine for software. The ubuntu software center uses apt behind the scenes to hit up a list of software hosted by the ubuntu team, called a **repository**, looking for the software that you're looking for. apt will then download the software from the **repository** an install it for you, along with any **dependencies** (additional software that may be needed for your programs to run).
It is possible for you to run apt manually, without going through the ubuntu software center first, by opening up a **terminal emulator** with 
```

ctrl + alt + t

```
Or by searching for "terminal" in the ubuntu dash.
In the prompt that appears, enter the command,
```

sudo apt-get install gimp

```
A breakdown of what this command tells the computer to do follows:
[LIST]
[*]**sudo **tells the computer that you want to work as an administrator, and will ask for your password.
[*]**apt-get **commands apt that you are getting software
[*]**install **tells apt that you want to install software
[*]**gimp** is the name of the program that you want to install
[/LIST]

This command is what the ubuntu software center is running behind the scenes, but by running it directly you will be told exactly what is going wrong.

There is a learning curve associated with using another operating system, but if you persist you will reach a new level of computing bliss.

Thank you, and good luck!

---

