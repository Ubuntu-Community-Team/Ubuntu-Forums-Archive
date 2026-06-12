---
title: "Cannot run sudo in Terminal?"
date: 2012-10-26
forum: General Help
---

### Post by modersbach on 2012-10-26
FIXED: IT IS WORKING. THANK YOU.

I am new to Ubuntu -and linux in general- so please try to keep things simple or I wont understand.

I need to run a permissions script to get a program to run on Ubuntu (Whatpulse) and to do that I need to be in sudo.

I type in sudo and this is what I get:

> usage: sudo [-D level] -h | -K | -k | -V
usage: sudo -v [-AknS] [-D level] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid]
usage: sudo -l[l] [-AknS] [-D level] [-g groupname|#gid] [-p prompt] [-U user
            name] [-u user name|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-D level] [-g groupname|#gid] [-p prompt] [-u
            user name|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-D level] [-g groupname|#gid] [-p prompt] [-u
            user name|#uid] file ...
I have no idea what that means, but I know that I am not in sudo as it still tells me I cannot run the script.

---

### Post by vandorjw on 2012-10-26
```

sudo su

```
give password

now you are root

You will notice the "~][COLOR="Red"]$[/COLOR]" change to "~][COLOR="Red"]#[/COLOR]"
GL/HF, try not to break your computer

---

### Post by dino99 on 2012-10-26
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[https://whatpulse.org/whatis/](https://whatpulse.org/whatis/)

be aware that whatpulse is no more maintained, and so can be unusable.
[http://jmrk.whatpulse.org/](http://jmrk.whatpulse.org/)

---

### Post by modersbach on 2012-10-26
> **vandorjw said:**
> ```

sudo su

```give password

now you are root

You will notice the "~][COLOR=Red]$[/COLOR]" change to "~][COLOR=Red]#[/COLOR]"
GL/HF, try not to break your computer
Now I run into the issue of not knowing my user name on Ubuntu. 

I thought it was the name in the upper right corner, but apparently I was wrong.

I tried all variations of my name, but I guess I must have typed in something else? I dunno, I usually just use my first name as my username on computers. 

How do I find my username in Ubuntu?

---

### Post by Penguin360 on 2012-10-26
> **modersbach said:**
> Now I run into the issue of not knowing my user name on Ubuntu. 

I thought it was the name in the upper right corner, but apparently I was wrong.

I tried all variations of my name, but I guess I must have typed in something else? I dunno, I usually just use my first name as my username on computers. 

How do I find my username in Ubuntu?
Do you know how to open a terminal window?

If you open a terminal window, then you will see something like this:

YourUsername@YourComputerName: ~$

Then you know what your username is.

---

### Post by modersbach on 2012-10-26
> **CodingBeaver said:**
> Do you know how to open a terminal window?

If you open a terminal window, then you will see something like this:

YourUsername@YourComputerName: ~$

Then you know what your username is.

Ugh, sorry. I probably shouldn't be asking for help when I am this tired. 

I am working in terminal this whole time. Apparently it tacked my computer name on the end of my username. Should have payed more attention.

---

### Post by Penguin360 on 2012-10-26
> **modersbach said:**
> Ugh, sorry. I probably shouldn't be asking for help when I am this tired. 

I am working in terminal this whole time. Apparently it tacked my computer name on the end of my username. Should have payed more attention.
It's all right.

---

### Post by grahammechanical on 2012-10-26
If you simply run the command sudo in a terminal then you will get a printout such as you got. It is a listing of the options for using the command sudo.

Let me give you an example of the correct way to use sudo. We can update Ubuntu through the Update Manager or through a terminal. In which case we use two commands:

```
apt-get update
```

and

```
apt-get upgrade
```

Now, if I simply run those commands as I have typed them, then all I will see is a lists of options to use with those commands.

To run the commands I need to have administrator access. To get that I put the command sudo in front. Then I will be asked to enter my password and then the commands will run. So,

```
sudo apt-get update
```

and

```
sudo apt-get upgrade
```

would be the actual commands to type. By the way, the password we type in is not echoed (printed) on to the screen as we type it. Security reasons.

By using sudo in front of a command we gain administrator access for a few minutes or until the task has been completed. Again, it is due to security reasons.

Regards.

---

