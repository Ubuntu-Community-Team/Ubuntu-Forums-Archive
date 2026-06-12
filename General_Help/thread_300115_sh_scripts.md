---
title: "sh scripts"
date: 2006-11-15
forum: General Help
---

### Post by dmbeer on 2006-11-15
Hi All

I have just installed Ubuntu (Edgy) all seems to be good except I can't execute a script (sh file). I need this to launch netbeans and other scripts I have written. All I get as an error message is permission denied. 

I have tried this both as a normal user and using sudo.

Any suggestions would be great.

David

---

### Post by dannyboy79 on 2006-11-15
have you made them executable? i think it's sudo chmod 755 filename. i think, you might want to google how to make a file executable.

edited: if putting sudo in front doesn't work, have you tried to temp log in as root by doing sudo -i, enter your password, then you're actually logged in as root, this has worked when i can't use sudo in front of the command, then make sure when you;'re done that you type exit at the cl, then you'll be back to you as the logged in user. good luck

---

### Post by dmbeer on 2006-11-15
The script has executable permissions.

I tried logging in as root using sudo -i and still get the following error message.

-bash: /home/david/Programs/netbeans-5.5/bin/netbeans: Permission denied


I have Xubuntu (Daper) installed on a laptop and that works fine.

However if I put sh in front of the command the script runs fine and launches netbeans IDE.

I shouldn't really have to put sh in front of it.

---

### Post by dannyboy79 on 2006-11-15
not sure about that, does this have something to do with how sh is configured? i have made a script before and for me to run it, i had to type in ./mountsmb. it was a script i created to mount a network share. anyway, this website contain info you already know but check it out, [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_02_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_02_01.html). you might just find out why you have to put sh before your script.

---

### Post by dmbeer on 2006-11-15
I might have to, but I never have before on any of the Linux systems I have used. Maybe it has something to do with the way it is configured on Ubuntu and no others.

---

### Post by dmbeer on 2006-11-15
After having looked at the guide at [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_02_01.html]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_02_01.html")

It basicly says that you should be able to run the script by using the following command mainly:

```
./script.sh
```

When I run the above command I get the following error.

```
bash: ./netbeans: Permission denied
```

Although you can use sh and bash to run your script.

Any suggestions why I can't use ```
./script.sh
``` to run my scripts

---

### Post by taurus on 2006-11-15
What are the first few lines of netbeans anyway?

```
more netbeans
```

---

### Post by dannyboy79 on 2006-11-15
i was just about to ask the same thing, if you are using bash to run it, you're first line will have to be 

#!/bin/bash

and maybe yours says something different???? although if it works in xubuntu why wouldn't it work in ubuntu or kubuntu whichever you;re using? hum?

---

### Post by dmbeer on 2006-11-15
The first line of the netbeans file is #!/bin/sh then there license and some code.

I can run the netbeans file I put sh first. I looked at /bin directory and it says that sh is pointing to dash. Where as my laptop points to bash.

Other links like rbash point to bash. Should I try changing the link.

---

### Post by taurus on 2006-11-15
That's your problem there.  Replace the #!/bin/sh with #!/bin/bash...

---

### Post by dmbeer on 2006-11-15
Changed it to !#/bin/bash and still get the error:

```
 ./netbeans 
bash: ./netbeans: /bin/bash: bad interpreter: Permission denied

```

Try with sh in front of it and it works.

---

### Post by taurus on 2006-11-15
```
ls -la netbeans
```

---

### Post by dmbeer on 2006-11-15
-rwxr-xr-x  1 david david 3826 2006-11-15 15:02 netbeans

As I understand it I have permission.

---

### Post by dmbeer on 2006-11-15
Hi All

Just to let you know I have fixed the problem.

It appeared to be a permissions issue on the drive where netbeans was stored.

It now runs successfully.

---

### Post by dannyboy79 on 2006-11-15
i noticed you stated that you changed it to !#/bin/bash, it's suppose to be #!/bin/bash, that's why it stated bad interpreter I am guessing because the line wasn't commented out since you didn't have the  symbol first, did you fix that also and just not mention that?

---

### Post by dmbeer on 2006-11-15
The netbeans file was restored to its original state, so the first line is #!/bin/sh

I also made sure that the link in /bin for sh pointed to bash and not **dash**.

Main problem I think was that I had mounted the drive wrongly not sure exactly what but I had.

---

