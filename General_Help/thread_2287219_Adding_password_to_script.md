---
title: "Adding password to script"
date: 2015-07-17
forum: General Help
---

### Post by tom171 on 2015-07-17
I have a script in Xubuntu that will launch an application that is only launchable via a script.  I wanted to create a desktop icon instead of launching through terminal.  I have the script working, the only issue is that it asks for my password because you have to open the application with rights.  So I have the sudo sh ./application in my script, but then it asks me for my password.  I don't want to enter my password to open this application.  Is there a way to enter my password into the script after the sudo sh command?

I realize that adding a password to a script is not best practice for security purposes.  But I am the only one using this PC and I'm not worried about this app.

I am new to Linux and very new to scripting so any help is greatly appreciated.

Thanks,

---

### Post by mystics on 2015-07-17
echo "password" | sudo -S command

The -S option tells sudo to get  the password from standard input rather than the terminal. Piping the  output (in this case the password) from echo satisfies this.

---

### Post by tom171 on 2015-07-17
Worked perfectly.  Thanks for your help!

---

