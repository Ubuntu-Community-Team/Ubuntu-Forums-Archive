---
title: "how to disable all password prompts"
date: 2013-10-03
forum: General Help
---

### Post by christon74 on 2013-10-03
Hello Unbunters :)

I have grown really tired of typing my password each and every time I log on to Ubuntu _ Yes, I am **that** lazy!!!
I do not care about privacy and I have nothing to fear since I am the only person at home to use the computer and this is why I am really not concerned about privacy. Now I have tried.
Now I have just tried this: 
[h=2]Instructions[/h] 						 							
[LIST]
[*] 									1 									 											Log into Ubuntu and click "Applications," "Accessories," then "Terminal."
 											 									

[*] 									2 									 											Type "sudo nano /etc/sshd_config" without quotation marks. Enter your administrative login password when prompted.
 											 									

[*] 									3 									 											Press "Ctrl+W" on the keyboard to open a "Search" window. Type "PasswordAuthentication" and press "Enter."
 											 									

[*] 									4 									 											Remove the "#" sign at the start of the  PasswordAuthentication label, then replace "Yes" with "No" so that the  line reads: PasswordAuthentication no

....But it does not work. I cannot find PasswordAuthentication.

Every other tip highly welcome.
Thanks in advance for all help and trouble.

Chris.

 											 									
[/LIST]

---

### Post by pholden on 2013-10-03
Are you walking about automatically logging into your desktop machine, or a server through SSH?

If desktop, then *System > Administration > Users and Groups* should let you set your account to automatically login. If server, then look at using your private key to login rather than a password.

---

### Post by slickymaster on 2013-10-03
If you want to disable administrative password prompts I think you should consider not doing it. The permission scheme set up on Linux systems has been very well thought out, and it goes deep into the system. You can really do a lot of damage to your system very easily, and the point of having you enter a password is to make sure you want change your system in some way.

---

### Post by stinkeye on 2013-10-03
This post might interest you.
I have a spare mouse button bound to a command to type out my password when needed.
The password can be retrieved from gnome-keyring which means it's not in a plain text file on your computer.
I just manually logon once at start of session then use the mouse button from then on when admin privileges are required.
The mouse button also works at the lock screen.
[http://ubuntuforums.org/showthread.php?t=2125918](http://ubuntuforums.org/showthread.php?t=2125918)

---

### Post by christon74 on 2013-10-12
Heavens! what on earth is a server through SSH? I am talking about a simple Personal Computer; it is an old HP DC 7700 SF and again I am the only person in the house who ever uses it, I have very few concerns about privacy and I cannot bring myself to imagine why so many people are that taken with passwords and encryption. I find it pretty baffling, really....

---

### Post by Kevin_Arnold on 2013-10-12
> **christon74 said:**
> Heavens! what on earth is a server through SSH? I am talking about a simple Personal Computer; it is an old HP DC 7700 SF and again I am the only person in the house who ever uses it, I have very few concerns about privacy and I cannot bring myself to imagine why so many people are that taken with passwords and encryption. I find it pretty baffling, really....

The settings you changed in your original post is for connecting to your computer remotely (from another computer)... I would change those settings back.

Then, like the person said a few posts up, just go to the Users area in settings and have it auto log you in. At that point, it will just ask you to type your password when you make a system change, but it looks like you can use the script posted above to just use a key to automatically type it.

---

### Post by coffeecat on 2013-10-12
> **christon74 said:**
> Heavens! what on earth is a server through SSH? 

If you don't know, then you really do not want to be following the instructions you posted in your first post. They appear to be for removing password authentication when ssh-ing into a server. Which sounds - ahem - unwise to me. Where did you find them?

---

### Post by Iowan on 2013-10-12
> **christon74 said:**
> Heavens! what on earth is a server through SSH?I'll assume you know what a server is. Since the instructions you posted are for logging into SSH (Secure Shell), the question was if you wanted to log into a server via SSH without a password. Those instructions generally continue with adding keys...

[edit]I seem to be closely be following** coffeecat** today! :)

---

### Post by Iowan on 2013-10-12
Under System Settings is User Accounts. There is an option for Automatic Login.
[https://help.ubuntu.com/community/AutoLogin](https://help.ubuntu.com/community/AutoLogin)
This doesn't eliminate ALL passwords, just the login.

---

### Post by coffeecat on 2013-10-12
Just to add to what Iowan mentions, one that irritates me on a machine that only I use securely at home.

System settings -> Brightness & Lock. Switch lock screen to off. Then the screen will only lock if you use the ctrl-alt-L shortcut.

If you eliminate password prompts for login and unlocking the screen after screen autolock, then the number of times you need to type in your password is dramatically decreased down to administrator tasks only: software installation, system updates, setting your wi-fi WPA passkey the first time only and using sudo in the terminal.

Which, if I remember correctly, is just about the same as when using a Mac.

---

### Post by christon74 on 2013-10-13
Aaaah ok. Now I see the 'ssh' in the instructions. I had not noticed this when I posted my first message. Again no no no, this is no server, it is just a plain desktop computer, it is a second hand reconditioned HP DC 7700 SF

---

### Post by christon74 on 2013-10-13
Hello again Ubunters:D I think I have at last found what I want:
[http://www.ubuntugeek.com/how-to-disable-password-prompts-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-password-prompts-in-ubuntu.html)
Open the terminal window from Applications --> accessories --> terminal, run the command:
 [INDENT]sudo visudo
[/INDENT] Find the line that says
 [INDENT]%admin ALL=(ALL) ALL
[/INDENT] and change it to
 [INDENT]%admin ALL=(ALL) NOPASSWD: ALL
[/INDENT] Save and exit the file

---

