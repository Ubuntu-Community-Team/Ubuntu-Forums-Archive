---
title: "Password manager for non browser based applications"
date: 2021-08-04
forum: General Help
---

### Post by wilqo21 on 2021-08-04
Hello,


I'm a new Ubuntu (LTS) Budgie user and i have a question about logging in in an application that does not run in a webbrowser.
I downloaded the FlatPack application for Element ([https://app.element.io](https://app.element.io)).

When i run the program I am required to login with my Element User-ID and password.
I would like to do that automatically.

Is there an application that will do this ?
I would prefer an open source application that will store the passwords locally and not in the cloud.

I tried KeePassXC but that application only stores login information about websites

I there a program who can do this ?

Thanks.  :-)


Wilqo21

---

### Post by TheFu on 2021-08-04
KeePassXC sorts all my passwords, passphrases, software licenses, banking information, emergency contacts, current passport, current immunization, and insurance information just fine.

"Autotype" is a very dangerous way to use any password manager - browser or not.  There are all sorts of ways to accomplish automated logins, but none should be automatic without any user steps.  Even to login to a cat video website, I am required to select the record for that location in PeeKassXC, then press the auto-entry accel key-chord to fill in my credentials.  Seems a minor thing to me for 100x more security.

If you don't care about security, you could use something like xdotool to enter keystrokes for you and hook that up to the window manager of your GUI session to make running it something like "<ctl>-<alt>-F8" as the input.  Of course, the userid/password would be in your xdotool script, which would be a security failure.  You could have the script use keepasscli to get the password as part of your xdotool script and enter it into the Element program. That poor security choice would be all yours.  But it is possible.

---

### Post by wilqo21 on 2021-08-05
Hello,    Reading your answer i realized that this will indeed cause security problems.   I agree with you on that.      So i will add "user steps", probably the best way for now is to store the login   details in KeePassXC, and use the "Copy User-ID" and "Copy password" buttons.    Thanks for your help.      Wilqo21

---

### Post by TheFu on 2021-08-05
> **wilqo21 said:**
> Hello,    Reading your answer i realized that this will indeed cause security problems.   I agree with you on that.      So i will add "user steps", probably the best way for now is to store the login   details in KeePassXC, and use the "Copy User-ID" and "Copy password" buttons.    Thanks for your help.      Wilqo21

Sorry, I wasn't clear.  I use the autotype that does enter the username and password when that's possible, but I have to hit <c>-<s>-v to start it AND have to have selected the active record in the list.  Additionally, in the window layers, KeepassXC is at the top and the program to receive the entry are at Z-1 layer with the cursor in the username field.  Wow, that's harder to say than actually do.

---

### Post by wilqo21 on 2021-08-07
Hello,

I tried the "autotype", and it works perfectly.
I will use KeePassXC and "autotype" from now on.
Thanks for your help.  :-)

Wilqo21

---

