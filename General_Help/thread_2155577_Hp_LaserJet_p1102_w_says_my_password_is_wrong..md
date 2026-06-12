---
title: "Hp LaserJet p1102 w says my password is wrong."
date: 2013-06-18
forum: General Help
---

### Post by bobayoga on 2013-06-18
Hello! Thank you for taking the time to help me.

Here is my problem:

I just got a new HP printer LaserJet p1102w.

I went on the website to get the right plugin. And I ran it with the terminal. But then when I run the command "hp-setup" to finalize the whole thing, it asks for my root password and when I enter it it says my password is wrong. And yes I have double checked and triple checked my password. So I don't know what to do. Any help would be much appreciated.

---

### Post by mbeach on 2013-06-18
have you tried:

```
sudo hp-setup
```

then when prompted enter your password? You have likely tried this already, but mention it just in case you have not.

---

### Post by bobayoga on 2013-06-19
Yes thank you for asking. I have tried sudo hp-setup. And of course it prompts for my root password in the terminal. And in the terminal it accepts it there's no problem there. It's once the window pops up and detects the printer that the problem arises. The window prompts for my root password and then it fails no matter how many times I try.

Again thank you for taking the time to try and help me.

---

### Post by bobayoga on 2013-06-21
Nevermind I found a solution. I don't know what made it work but here is what I did

I typed this into the terminal:

```
sudo hp-plugin -i
```

Then in the settings page for HP printers I printed a test page and after that I could print no problem.

---

