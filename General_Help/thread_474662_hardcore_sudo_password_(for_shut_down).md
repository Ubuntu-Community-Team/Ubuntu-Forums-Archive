---
title: "hardcore sudo password (for shut down)"
date: 2007-06-15
forum: General Help
---

### Post by utopial on 2007-06-15
hey i was wondering if there is a way of hardcoding passwords to bypass the sudo password check? i want to shut down my comp using the xmms 'goodnight' plugin and it requires u to put in a line of code to shut it down.  i dont want to have to change the requirements for shutdown so that it doesnt need sudo as ive read in some places

this shuts down ur comp:
```
sudo shutdown -h -t time now
```

but it prompts a password. just say your password is abc123. how do u incorporate it into your code? i tried:
```
sudo shutdown -h -t time now password: abc123
```

and that didnt work.

btw xmms only give u one line of code to input. so i can either use one line or call a bash script with multiple lines. either way i need to hardcode the password

---

### Post by thelinuxguy on 2007-06-15
Well, you can make sudo not prompt a password for shutdown. Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=468626](http://ubuntuforums.org/showthread.php?t=468626)

---

### Post by utopial on 2007-06-18
thanks, but i said that i know about that option but i want to be able to hardcode it

for the shutdown i ended up just changing the sudo permissions
HOWEVER, im now finding that this password issue relates to lots of stuff. basically i need to incorporate it in some of the bash scripts im making

ive got a few scripts that i need to write and but they end up prompting questions like:
```
password:
```
```
yes(y) or no(n)?:
```

how do i incorporate this into my code so that i can just double click on the script and it does everything for me (taking care of all the passwords/yesno stuff itself)??

surely some of u nerds have encountered this b4

btw, is there a realplayer plugin i can get so that my firefox/swiftfox plays the videos? if i install realplayer in wine will it work in my browser? i thought vlc/mplayer/totem would support real player...

---

### Post by yota on 2007-06-18
From 'man sudo'
> 
 -S  The -S (stdin) option causes sudo to read the password from the standard input instead of the terminal device.

For instance you can:
```

echo '*password*' | sudo -S command

```
but also:
```

cat passwordfile.txt | sudo -S command

```
Hope this helps!

---

### Post by utopial on 2007-06-19
thanks
i tried it but it wont work
e.g. if my password = ABC
i tried:

```
echo 'ABC' | sudo -s nautilus
```
(sudo nautilus lets u open up your root directory and browse as root user)

then i tried the same thing with a password.txt file i made and just put ABC in the top line.

both of them asked me for my password

also, how do i get rid of the yes(y)/no(n) prompts from terminal that come up sometimes when u (un)install stuff?

---

### Post by linzta on 2007-06-19
[http://ubuntuforums.org/showthread.php?t=61481](http://ubuntuforums.org/showthread.php?t=61481)

just change to make it fit :D

---

### Post by thelinuxguy on 2007-06-19
> **utopial said:**
> 
also, how do i get rid of the yes(y)/no(n) prompts from terminal that come up sometimes when u (un)install stuff?

If you want to reply yes to everything then
```

yes | program_name_here

```

---

### Post by yota on 2007-06-19
> **utopial said:**
> thanks
i tried it but it wont work
e.g. if my password = ABC
i tried:

```
echo 'ABC' | sudo -s nautilus
```
(sudo nautilus lets u open up your root directory and browse as root user)

then i tried the same thing with a password.txt file i made and just put ABC in the top line.

both of them asked me for my password

also, how do i get rid of the yes(y)/no(n) prompts from terminal that come up sometimes when u (un)install stuff?

its 'sudo -S' and not 'sudo -s' (my fault! I mistyped in my original post)

---

### Post by utopial on 2007-06-20
awesome work guys. thanks a heap!

but how do i do both things in one operation? i tried the following code but it failed

```
echo '*password*' | yes | sudo -S command
```

---

### Post by utopial on 2007-06-21
*bump*

---

### Post by yota on 2007-06-21
> **utopial said:**
> awesome work guys. thanks a heap!

but how do i do both things in one operation? i tried the following code but it failed

```
echo '*password*' | yes | sudo -S command
```

this way you are redirecting the output of "echo password" to the yes command and a list of "y" to sudo:

*password* -> yes
yyyyyyy... -> sudo

try this instead:
```

echo *password* | sudo -S su -c 'yes | *command*'

```

---

### Post by mtn on 2007-06-21
How can I force the need for a password to shutdown? With GUI when the panel shutdown button is used?!

Any ideas?

---

### Post by utopial on 2007-06-22
hey yota, thanks for that. it appears to have worked

---

