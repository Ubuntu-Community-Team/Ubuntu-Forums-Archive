---
title: "Switch user"
date: 2017-05-22
forum: General Help
---

### Post by most122 on 2017-05-22
Hi I have installed Ubuntu 17.04 and joined it to domain controller realmd successfully my question is I could not able to switch user from GUI to enter the domain user name
from terminal its easy to switch via su username is there any one help me?
Thank You

---

### Post by QIII on 2017-05-22
Hello!

Which release of Ubuntu are you using?

What do you mean by "I could not able to switch user from GUI to enter the domain user name"?  Are you unable to find the GUI?  Do you enter your credentials in the login form and something that you don't expect happens?  If so, what exactly happens?

---

### Post by most122 on 2017-05-23
Ubuntu 17.04 Yes I could established  GUI I mean from Login GUI screen no option appeared to me to switch standard user for example if I want to switch from user1 to user2 i hope i am clear.Thank you for your response

---

### Post by shridhar-kapshikar on 2017-05-23
[COLOR=#111111][FONT=Ubuntu][FONT=inherit]Go to the top right-hand corner of the screen and click on your username to trigger the drop-down menu of options, then click on Switch User.

If that option is not available, then install debian package.
[/FONT]
In a terminal:
```
sudo apt-get install xfswitch-plugin

```

Or via Software Center:
[IMG]https://hostmar.co/software-banner[/IMG]
[FONT=inherit]
[/FONT]
[/FONT][/COLOR]

---

### Post by most122 on 2017-05-23
Thank you for your support solved

---

