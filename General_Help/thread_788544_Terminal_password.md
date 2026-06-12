---
title: "Terminal password"
date: 2008-05-09
forum: General Help
---

### Post by cloroxmartini on 2008-05-09
So I'm trying to get the Kiba Dock to install but before I can even do that, I go into the terminal and type in the command "su."  Then it asks for my password.  I give my password but it doesn't accept it and says authentication failed.  Why would it do that?

---

### Post by Exsecrabilus on 2008-05-09
Instead of running:
```
su
```Just do:
```
sudo {your command}
```

I read somewhere you shouldn't use *su* (for some reason.)

---

### Post by Separ on 2008-05-09
You have to type the password for the "root" account when running things as the super user. You have to set this manually once ubuntu is installed. You will need to do this if you have not done so yet by typing ```
sudo passwd
```

As for Exsecrabilus's thing about not using "su", you should only really use it when having to run multiple commands as root such as compiling a program from several different makefiles. Kiba-Dock is a classic example of when "su" comes in handy :D

---

