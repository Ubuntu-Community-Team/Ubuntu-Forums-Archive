---
title: "Which Command Script Help"
date: 2015-11-14
forum: General Help
---

### Post by Billy_Martinez on 2015-11-14
Hi everyone I'm new to Linux scripting and I'm playing around with the which command. Can any of you tell me why my script is not working. 

I have firefox installed, and when I enter firefox the script moves to the else statement even though it shouldn't.

> 
#!/bin/bash
# My First script

echo "Please enter the name of a program to check to see if it's installed."

read var

if which var
then 
echo $var " is insalled"

else
echo $var " is not insalled"
fi


---

### Post by Billy_Martinez on 2015-11-14
This is the result of the "which firefox"  command in terminal. 

> bill@bill-VirtualBox:~$ which firefox
/usr/bin/firefox


---

### Post by Billy_Martinez on 2015-11-14
I created the same script without the variable and it works.


> #!/bin/bash
# My First script

echo "Checking to see if firefox is installed"


if which firefox
then 
echo "firefox is insalled"

else
echo "firefox is not insalled"
fi


I'm lost [IMG]http://ubuntuforums.org/images/smilies/confused.gif[/IMG]

---

### Post by Lars Noodén on 2015-11-14
You seem to be missing a dollar sign for the variable:

```

 if which $var

```

If you want it to be silent, then redirect the output to the bit bucket

```

 if which $var > /dev/null

```

---

### Post by matt_symes on 2015-11-14
Hi

```
if which var
then
echo $var " is insalled"

else
echo $var " is not insalled"
fi 
```

Whenever you want to access the *contents* of a variable, you want to prepend it with a $ sign. You missed one that i have highlighted below.

Also you always want to quote your variables; also hightlighted below.

```
if which **"$var"**
then
echo **"$var is insalled"**

else
echo **"$var is not insalled"**
fi 
```

This is a good first attempt at a script so i won't critique it but i'll point you to some good websites for learning bash.

[http://mywiki.wooledge.org/BASH](http://mywiki.wooledge.org/BASH)
[http://wiki.bash-hackers.org/](http://wiki.bash-hackers.org/)

Consult these websites first :)

Kind regards

---

### Post by Billy_Martinez on 2015-11-14
Thank you all for your help.

---

### Post by matt_symes on 2015-11-14
Hi

If you're happy, I'll mark this thread as [solved] for you.

Kind regards

---

