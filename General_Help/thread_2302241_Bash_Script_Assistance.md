---
title: "Bash Script Assistance"
date: 2015-11-08
forum: General Help
---

### Post by ulrichkenneth on 2015-11-08
Hello All, 

First off, If I am posting in the wrong area, kindly let me know and I will try to move it to the appropriate spot. 

I am trying to write a bash script that if the person logging in doesn't meet the security question, it will log them out. I know it seems simple but this is a test and if success it will get more complicated. 

I am not looking for answers but where to start looking. 

My script is below.  When I use the 'exit' command nothing happens. When I use the logout command it tells me to use the exit. 

Also,  excuse any typos. I'm using cell phone to type this. I don't have Internet at my place so I can't copy/paste the code but it is correct below. If not I will correct it. 

#! /bin/bash
echo "What is your name?" 
read $ISNAME 
If [ $ISNAME = "Ken" ] ;
then 
    echo "Hello Ken"
fi

if [ $ISNAME != "Ken" ]; 
then 
     echo "Get away from me" 
fi

if [ $ISNAME != "Ken" ];
then 
     exit
fi

---

### Post by TheFu on 2015-11-09
You  need  to  capture  all interrupts  so they cannot just cntl-c  to break  out.
There are many scripting-how-to guides. 
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)  for example.

I think you want to add the script to the approved shells, make it the login-shell for the user in the passwd file and exit only if there is a failure. Otherwise, start a bash shell.

Before doing this be certain you have another userid with any permissions setup. It is very likely to be locked out, a few times, at least.

I would  use an  'else'.  Only  need  1  'if' in this.

---

### Post by ulrichkenneth on 2015-11-09
Thank you, I will keep that in mind, but I would like the script to work before I incorporate it into shells and all that. Thank you for the information and guidance. :D

> **TheFu said:**
> You  need  to  capture  all interrupts  so they cannot just cntl-c  to break  out.
There are many scripting-how-to guides. 
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)  for example.

I think you want to add the script to the approved shells, make it the login-shell for the user in the passwd file and exit only if there is a failure. Otherwise, start a bash shell.

Before doing this be certain you have another userid with any permissions setup. It is very likely to be locked out, a few times, at least.

I would  use an  'else'.  Only  need  1  'if' in this.

---

### Post by Lars Noodén on 2015-11-09
Here is an example of trapping [signals](http://manpages.ubuntu.com/manpages/vivid/en/man7/signal.7.html) like TheFu mentioned is necessary:

```

#!/bin/sh

trap stopping 1 2 15

stopping() {
 echo Ow!
 exit 1;
}

read foo;
echo Foo=$foo
exit 0;

```

You can trap on the signal number or name.

The idea is that you can't ctrl-C your way out of the script.

---

### Post by TheFu on 2015-11-09
Actually, if you don't replace the shell, I don't think this will ever work.
That part is integral to the solution. When the shell finishes, the next action is the user will logout.

If users will only have remote access over ssh, [https://stackoverflow.com/questions/402615/how-to-restrict-ssh-users-to-a-predefined-set-of-commands-after-login](https://stackoverflow.com/questions/402615/how-to-restrict-ssh-users-to-a-predefined-set-of-commands-after-login) has some options.

---

### Post by SeijiSensei on 2015-11-09
I also think you need to make it the user's default shell in /etc/passwd.

For testing just create a new user with the script as its shell.

---

### Post by ulrichkenneth on 2015-11-19
**Ignore comment before this. It didn't post right as you can see**

Hello,Sorry for the delay, I got caught up with work. I actually had a chance to play with this today, and I accomplished a lot with your guidance. Below is a copy of the script I've been writing. Thank you for assisting me(a bash script newb) into getting this done.

My one and final question is that I want to incorporate this when a user logs in, before the terminal appears to get access to the server. Like, After Login, before terminal loads. I hope that makes sense. I want to be asked who is logging in, and what is the codename before the terminal loads for the user to start accessing the system.If I need to better clarify, I can. 

This is on GitHub as well with a warning that there are still bugs.

If anyone has any ideas how I can improve this little script, It is gladly welcome.

```
#!/bin/bash
trap -- '' SIGINT SIGQUIT SIGTERM SIGTSTP
echo "What is your name?"
read ISNAME
if [ $ISNAME = "root" ];
then
        echo "Nice to meet you, root."
        echo "Login as root" | mail -s "Login for root" root
        echo "Next for the Security Question!"  
fi

echo "What is the codename?"
read CODENAME
if [ "$CODENAME" = "Cole Server" ];
then
        echo "Hello, Welcome root!";
else
        echo "Away from me, Not Root";
        echo "Unauthorized Root Login" | mail -s "INTRUDER ALERT" root;
        pkill -KILL -u $ISNAME;
fi
```

Alright, So I hit another snag that I am investigating. 
If someone just types "r" instead 'root' for the What is your name, and either gets the Code Name right or wrong, it still logs into root. 

I am needing to find another way to kill the SSH or Terminal login attempt since the pkill is based off the name that is logging in.

---

### Post by Habitual on 2015-11-19
> **ulrichkenneth said:**
> ```
read CODENAMEif [ "$CODENAME" = "Cole Server" ];
```

should be like:
```
read CODENAME
if [ "$CODENAME" = "Cole Server" ];
```

---

### Post by ulrichkenneth on 2015-11-19
HA, 

I had it copied and pasted from the line that has it all smashed together, I completely overlooked that part. Thank you! I thought I had it all separated.

I fixed it.

I figured out how to get it to launch upon login. Now just got to find something similar to the pkill that if the user doesn't get the security code right, it will log out. As of now, If they type anything in as the What is the name, and anything for the Code Name, It auto log in as root still.

> **Habitual said:**
> should be like:
```
read CODENAME
if [ "$CODENAME" = "Cole Server" ];
```

---

### Post by Habitual on 2015-11-19
So, it all worked out?

---

### Post by ulrichkenneth on 2015-11-22
Yea it did. I just have to find a way to log the user out vs bash. I can use $isname but if roo is used instead of root then it will still login. I can also use kill -HUD 1 to cancel root login but the pid of the standard user changes ie Ken or Kenneth.

Trying to find a way around that.

If I use the logout it will say use exit. If I use exit it exits the script rather than logging said user out.

---

### Post by Lars Noodén on 2015-11-23
You might reverse the logic so that it defaults to logging out the user unless the correct answers are all provided.

---

### Post by TheFu on 2015-11-23
> **Lars Noodén said:**
> You might reverse the logic so that it defaults to logging out the user unless the correct answers are all provided.

Definitely!

BTW, have you looked at saving the PID from the last run program? Then it is easy to kill just the shell that gets spawned.  Killing root processes is dangerous to a running system.

---

### Post by ulrichkenneth on 2015-11-24
> **Lars Noodén said:**
> You might reverse the logic so that it defaults to logging out the user unless the correct answers are all provided.


Could you provide an example of what you mean please?

---

### Post by ulrichkenneth on 2015-11-24
> **TheFu said:**
> Definitely!

BTW, have you looked at saving the PID from the last run program? Then it is easy to kill just the shell that gets spawned.  Killing root processes is dangerous to a running system.


Unfortunately, I am not sure what you mean. If you can better clarify, That would be great! 

To All, 

Sorry for sounding like a newb, I am one lol.

---

### Post by TheFu on 2015-11-24
```
if [ $ISNAME != "root" ]; then
     exit;
fi
```

BTW, I'd code it differently to avoid common issues with no inputs.

```
if [ "X$ISNAME" != "Xroot" ]; then
     exit;
fi
```

This way only valid answers continue.

---

### Post by ulrichkenneth on 2015-11-24
So, I was doing some reading on Advance Bash Scripting over a couple PDFs I got from Tech Knowledge and some other sources via Facebook.

I've came across a couple of commands that could help. One is called "builtin commands" and the other is "enable/disable".

I've read that if you use "enable -n <command>" that it will treat it as an external(meaning exit the user, rather than the script) but when attempted, I got an error.

Can someone provide some referenecs, because I'm not having much luck finding these commands in Google.

---

### Post by TheFu on 2015-11-24
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) has pretty much anything that bash can do.  Bash has some settings that can be enabled or disable. noclobber is an example. That's all.

I don't use FB and never heard of "tech knowledge",  sorry.

---

### Post by ulrichkenneth on 2015-11-26
TheFu, 

It is fine. I might have misspelled what they really are. I mainly use Facebook to search articles, and free resources for any kind of Android/Linux Programming, Network/CyberSecurity resources download PDF books for learning material. 

I've actually learned a lot from the resources Facebook has to offer, and my collection grows by the second.

---

