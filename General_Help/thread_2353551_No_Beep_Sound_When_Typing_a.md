---
title: "No Beep Sound When Typing \a"
date: 2017-02-22
forum: General Help
---

### Post by John_Patrick_Mason on 2017-02-22
Hey everyone,  I'm currently learning the Linux command line with the help of William E. Shotts' *The Linux Command Line* book, and I'm stuck at one section.  When I try the following commands, I don't get any beep sound:  ```
sleep 10; echo -e "Time's up\a"
``` ```
sleep 10; echo "Time's up" $'\a'
```

---

### Post by TheFu on 2017-02-23
Are you connected to a tty or a ptty?  
[https://unix.stackexchange.com/questions/1974/how-do-i-make-my-pc-speaker-beep](https://unix.stackexchange.com/questions/1974/how-do-i-make-my-pc-speaker-beep)

---

### Post by John_Patrick_Mason on 2017-02-23
tty, I think. I just opened a regular terminal session.

---

### Post by papibe on 2017-02-23
Hi John_Patrick_Mason.

You may need to load a module in order to beep, as it seems Ubuntu no longer loads that module by default:
```
sudo modprobe pcspkr 
```
Source [here]("http://askubuntu.com/questions/19906/beep-in-shell-script-not-working").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by John_Patrick_Mason on 2017-02-23
papibe,

I executed into the terminal the command your provided. Unfortunately, it didn't work.

---

### Post by TheFu on 2017-02-23
> **John_Patrick_Mason said:**
> tty, I think. I just opened a regular terminal session.

`who am i` which show which tty/pts you are connected with.  I have doubts. Did you look at that link?

---

### Post by John_Patrick_Mason on 2017-02-23
> `who am i` which show which tty/pts you are connected with.  I have doubts. Did you look at that link?

I executed the command your supplied, but I couldn't get it to work, so I decided to check out the link you provided.

First, I typed the following command:

```
sudo modprobe pcspkr
```

Then I created a backup of the blacklist file using:

```
sudo cp -v blacklist.conf blacklist.conf.bak
```

Then I commented out the blacklist pcspkr line using:

```
sudo vi blacklist.conf
```

and saved the file with :wq.

That's when I tried to get it to work again using:

```
sleep 10; echo -e "Time's up\a"
```

```
sleep 10; echo "Time's up" $'\a'
```

Still nothing. One of the comments in the link you provided suggested that I also type:

```
modprobe -r pcspkr && modprobe pcspkr
```

but I have no idea what this comment means. I don't usually like to execute commands that I don't understand in the first place. Should I still execute it?

I also typed whoami and it gave me my username.

---

### Post by TheFu on 2017-02-23
To learn the details about any command, use the manpages.  **man man** is an example. **man modprobe** is another.

who and whoami are different commands.  who am i will show the input line being used.

When you have issues, please post the EXACT COMMAND used and any relevant error messages, if you want help. Often, our interpretations of what happened is incorrect and someone else's eyes will see things we don't.  Plus googling any error message + ubuntu will lead to a solution many times.

---

### Post by John_Patrick_Mason on 2017-02-23
What command do you want me to type into the terminal:

```
who
```

or

```
who am i
```

---

### Post by TheFu on 2017-02-23
who<space>am<space>i<enter>

where the <spaces> are the space bar and <enter> is the enter key.

**who mom loves** is another method.

You reported typing "whoami", not "who am i" previously. Sorry for the confusion. who and whoami are different commands. "who" is the command with "am i" as options.
```
$ who am i
thefu       pts/0        2017-02-21 15:43 (:0)

```

---

### Post by John_Patrick_Mason on 2017-02-23
No problem. I typed:

```
who am i
```

but it came back with no output. That's why I was confused.

Same thing for:

```
who mom loves
```

---

### Post by TheFu on 2017-02-24
Well, I don't know what to say.  'who' is a command that has been around for decades, longer than I've been running Unix systems.  There probably are other ways to get the system to say which tty/pty is being used, but I don't know it.  The entire point I was trying to show was that you are probably NOT actually using a tty, so causing a beep probably isn't possible from any GUI-based terminal.  Check out that original stackexchange link.

---

### Post by John_Patrick_Mason on 2017-02-24
I did a little research on the "who am i" command and found this link: [https://stackoverflow.com/questions/3522341/identify-user-in-a-bash-script-called-by-sudo](https://stackoverflow.com/questions/3522341/identify-user-in-a-bash-script-called-by-sudo) The question dates from 2010, but if you scroll down to the first answer, there's a couple of replies just below it with somebody having the exact same problem with the "who am i" command yielding no output in Ubuntu 16.04. The user with the same problem suggests using the "who" command instead, which yields:  ```
mason    tty7         2017-02-24 12:02 (:0)
```

---

### Post by John_Patrick_Mason on 2017-02-24
I just figured out how to make it work.

Loading the module:

```
sudo modprobe pcspkr
```

is useless unless you already have the beep program installed using:

```
sudo apt-get install beep
```

and is not what I was looking for.

What I was looking for was how to use

```
echo -e '\a'
```
 
to make a beep sound.

What worked for me was when I read answer #3 in the link you provided:
[https://askubuntu.com/questions/19906/beep-in-shell-script-not-working](https://askubuntu.com/questions/19906/beep-in-shell-script-not-working)

All what it takes to get it to work is to edit the ~/.bashrc file located in your home directory using:

```
vi .bashrc
```

and add the following lines at the end:

```

xset b 100
pactl upload-sample /usr/share/sounds/ubuntu/stereo/bell.ogg bell.ogg

```

and save the file using:

```
:wq
```

and to run:

```
source .bashrc
```

in order to avoid having to restart.

---

### Post by cariboo on 2017-02-25
> **John_Patrick_Mason said:**
> papibe,

I executed into the terminal the command your provided. Unfortunately, it didn't work.

the command doesn't echo anything back. To check if the module loaded use this:

```
sudo lsmod | grep pcspkr
```

the output of the above command should look similar to this:

```
lsmod | grep pcspkr
pcspkr                 16384  0
```

---

