---
title: "[SOLVED] Mobile Connect Card"
date: 2007-11-21
forum: General Help
---

### Post by Nunu on 2007-11-21
I have one other thing that is just out of general interest and i am sure the answer will be pretty much simpler then what i expect it to be. 

I have the software and the drivers installed for my E220 mobile connect card and everything is working perfectly, it also seems to work faster under Gutsy then under XP. The only bugging thing is that before you can open the mobile connect application you need to open a terminal window run sudo -s, enter the sudo password and then leave the window open until the application has started. after the application is open you can close the terminal window and use the software as per normal. My question is can i create a custom launcher that will run sudo -s enter the password and then launch the application or even create a launcher that will run sudo -s request the user for a password and once the password is entered open the application? 

Can anyone give me an idea of what i need to do to create the launcher. I have tried adding sudo -s before the execution string on the launcher properties but as you can imagine... nada nothing. Or even better will be if someone can point me into a direction of what i need to do so that the software does not require me to be in supper user mode to function.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-21
Hi, Nunu

I assumed you need root access to launch (GUI) application, yes?

To run (GUI) application with "administrator" privilege, you can try gksu or gksudo.
You will get prompted for password just like when you launch "Synaptic".

[LIST]
[*]You can create launcher by right-clicking your desktop, and select "Create Launcher..."
[*]And enter this code for the "command":
```

gksudo *application_name*

```
Substitute *application_name* with the program you want to run.
[/LIST]

---

### Post by Nunu on 2007-11-21
Milk & Toast & Honey

I knew it wasn't going to be as difficult is i figured it would be... You are a scholar and a Gentleman and i do thank you ever so much. The installation of the Software package creates a launcher under the internet program group from the task bar, i created a shortcut to the desktop from there, so i just need to add gksudo or gksu command before the launch string in the launcher shortcut.

Thank you very much for the reply.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-21
Nunu,

thanks for your compliment.
I'm glad I can help you.

Just a reminder, please mark this thread as solved, by selecting:
```

Thread Tools -> Mark as Solved

```

Thank you.

---

### Post by Nunu on 2007-11-21
will do 

many thanks

---

### Post by Nunu on 2007-11-22
Just for interest sakes. gksudo worked like a charm :D

---

