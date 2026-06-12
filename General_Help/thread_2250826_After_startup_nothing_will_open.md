---
title: "After startup nothing will open"
date: 2014-10-31
forum: General Help
---

### Post by TheBaileyAce on 2014-10-31
I'm fairly new to Ubuntu but have been using it for about 2 months now and it has worked fine. For the past few days after starting Ubuntu, I try to open average programs (Chrome etc.) yet it does not open and then eventually the desktop icons disappear as well as the little taskbar icon things in the top right corner but the rest of the bar remains. It is really weird and nothing opens at all. Nothing even shows up in the search bar thing. Any ideas?

---

### Post by JazzPotato on 2014-10-31
Anything strange looking in /var/log/Xorg.0.log, /var/log/Xorg.1.log, /var/log/apport.log, /var/log/syslog? Usually when something goes wrong checking the logs is a good idea.
A good way to view logs is to run the following command in a terminal
```

cat /var/log/Xorg.0.log | less

```
This command shows you the contents of a file in a terminal. Here is a breakdown of that command:
**- cat** prints the contents of a file
**- /var/log/Xorg.0.log **is the location of the file you want to read
**- The "|" character **is called the "pipe" character. It "pipes" the output of a command through another program. On my UK keyboard I can find it next to the "z" key. We want to pipe the output of *cat*into a program called *less*
**- less **is a program that makes reading files in a terminal easier because you can search files and navigate up and down easily.

While using less you can navigate up and down with the **j **key (down) and the **k** key (up). You can also search for for a keyword by pressing **/** and the typing the word you'd like to search for.

To find out more about less run the command
```

man less

```

And that applies for any terminal command, the command *man* pulls up the online help for commands.

Good luck!

---

### Post by TheBaileyAce on 2014-10-31
I can't even get the Terminal open. Nothing can be opened at all.

---

### Post by Bucky Ball on 2014-10-31
Which release are you using?

---

### Post by TheBaileyAce on 2014-10-31
14.04, I believe.

---

### Post by matt_symes on 2014-10-31
Hi

> A good way to view logs is to run the following command in a terminal
Code:

cat /var/log/Xorg.0.log | less

No need for the cat and pipe.

```
less /var/log/Xorg.0.log
```

Well worth looking through that log file though.

Can you get to a Virtual terminal by pressing CTRL + ALT + F1 ?

If so then enter your user name and password to login in.

Then type

```
DISPLAY=:0 $(which gedit)
```

What diagnostic information, if any, is displayed on the virtual terminal ?

You can also look through the above log file from the virtual terminal as well.

Kind regards

---

### Post by TheBaileyAce on 2014-11-01
Thanks for the help, but even though pressing Ctrl+Alt+F1 DOES work, it just does a constant stream of messages with random numbers, I can't even enter my login info. I could take a photo of it with my phone but I'm not sure what kind of quality it would be.

---

### Post by TheBaileyAce on 2014-11-03
Here's 2 photos of what happens.
[http://imgur.com/He9bRgs,wxm0gdq](http://imgur.com/He9bRgs,wxm0gdq)

---

### Post by Bucky Ball on 2014-11-03
Looks like you have a bad sector on your hard drive. It's probably fixable but I'm not knowledgable about how.

How old is that drive? Might pay to back it up if you haven't.

---

### Post by jhay2 on 2014-11-03
try to install lxterminal from the tty screen "ctrl+alt+f1"  

then go back to your main screen "ctrl+alt+f7"

then open the lxterminal ,  and try to run your chrome in root user "sudo google-chrome" something like that .. if the chrome opens .. you have a permission problem on the sudo user

---

