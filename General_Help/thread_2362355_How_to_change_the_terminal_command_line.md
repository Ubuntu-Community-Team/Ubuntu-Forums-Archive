---
title: "How to change the terminal command line"
date: 2017-05-27
forum: General Help
---

### Post by ubu112 on 2017-05-27
Please,I'm not an expert.

I'd like to know how to change the terminal  command line on the right side of "@".

Thank you

---

### Post by &amp;KyT$0P# on 2017-05-27
Edit the [FONT=Courier New]PS1[/FONT] environment variable, which is set in [FONT=Courier New]~/.bashrc[/FONT]

---

### Post by vasa1 on 2017-05-27
What do you have and what do you want?

A lot of information is here: [https://help.ubuntu.com/community/CustomizingBashPrompt](https://help.ubuntu.com/community/CustomizingBashPrompt)

---

### Post by Habitual on 2017-05-27
```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[01;34m\] \w \$\[\033[00m\] '
```
Target is \h

---

### Post by ubu112 on 2017-05-27
Sorry,I wasn't so clear.

Now,my terminal command line is:

user@user-AOA150

I'd like to have:

user@AOA150

Please,can someone help me to understand how to delete "user-"

Thank you

---

### Post by &amp;KyT$0P# on 2017-05-27
So you want to change your computer's hostname from [FONT=Courier New]user-AOA150[/FONT] to [FONT=Courier New]AOA150[/FONT]? -

1) Run in Terminal
```
hostnamectl set-hostname AOA150
```

2) edit [FONT=Courier New]/etc/hosts[/FONT] (requires root privileges), replace [FONT=Courier New]user-AOA150[/FONT] with [FONT=Courier New]AOA150[/FONT]

3) reboot

---

### Post by ubu112 on 2017-05-27
Sorry,I'm not an expert and I don't want to make mistakes.

Edit /etc/hosts/ with "root privileges" mean:

sudo leafpad /etc/hosts/ ?and after changes save,close and reboot?Is this correct?

Thank you

---

### Post by vasa1 on 2017-05-27
What follows doesn't need elevated privileges and if you don't wish (or aren't allowed) to change your hostname, you can edit your .bashrc as described in the link I posted already. Making a backup of important files with a different name is helpful.

Close any running instances of your terminal(s).

Use a text editor such as gedit or leafpad or mousepad or kate (but not something like LibreOffice) to open your *.bashrc* file which is a hidden file in your home folder.

Go right to the end of the file and carefully paste in this line:
```
PS1="\u@AOA150 \w $ "
```
Save the file and close the text editor. Now open your terminal. You should see the new prompt looking like this:
```
user@AOA150 ~/Desktop $ cd Images
user@AOA150 ~/Desktop $ cd Images/
user@AOA150 ~/Desktop/Images $ 

```
(You could also use a terminal-based editor and then run *source .bashrc* but I'm assuming you're more at ease with a simple GUI-based text editor).

What we've done here is to make you a new prompt without changing any system information.
In *PS1="\u@AOA150 \w $ "*
[LIST]
[*]PS1= is what is needed to tell the system that what follows will be your prompt
[*]\u is your user name
[*]"@AOA150 " is a literal string (as per your needs). Note the space after "0" (optional).
[*]\w tells the system to include your present working directory.
[*]Another space (optional).
[*]$ is conventionally used to show that the current session is being run by a normal user.
[*]Another space (optional).
[/LIST]
Also note that there's no need to comment out or delete any lines relating to PS1 above the line you've added at the end of the file.

---

### Post by &amp;KyT$0P# on 2017-05-27
> **ubu112 said:**
> Edit /etc/hosts/ with "root privileges" mean:

sudo leafpad /etc/hosts/ ?and after changes save,close and reboot?Is this correct?
Almost.  Try -
```
sudo -H leafpad /etc/hosts
```

That [FONT=Courier New]-H[/FONT] flag sets [FONT=Courier New]$HOME[/FONT] to root's home directory.  This is important when using [FONT=Courier New]sudo[/FONT] with graphical applications, where without [FONT=Courier New]-H[/FONT] you could end up with root-owned files in your home directory.

---

### Post by ubu112 on 2017-05-27
Thank you Vasa1 for your kind reply

First:   .cp .bashrc .bashrc-backup

Second: I open in leafpad .bashrc and copy+paste - PS1="\u@AOA150 \w $ ",at the end.Save and close.

Third: Open the terminal and I'll see - user@AOA150 ~/Desktop $ cd Images

Why I see /Desktop,before $ and cd Images,after? or it's just an example?

Thank you

---

### Post by vasa1 on 2017-05-27
> **ubu112 said:**
> ...
Why I see /Desktop,before $ and cd Images,after? or it's just an example?
...
Just an example. Type *cd* and press enter to return home.

The prompt I've given will display the path to the current folder you're in.

---

### Post by ubu112 on 2017-05-28
I'd like to say Thank you, Vasa 1

Now I have:

> user@AOA150 ~ $

Am I wrong or after AOA150 I had : ?If I remove space after AOA150 and before $,can I have:

user@AOA150~$

Making:

> PS1="\u@AOA150:\w$ "

I'll have: 

> user@AOA150:~$

Is it correct?

Thank you

---

### Post by vasa1 on 2017-05-28
Just keep trying variations till you're happy! Keep records of what you do and what the effect is. Even if you break something, you have the original to fall back on :)

---

### Post by ubu112 on 2017-05-28
After many attempts I'm OK.Now I put SOLVED.

I have a little question:

I installed Lubuntu yesterday,I had Ubuntu but it was too slow,for example Firefox was slower than Chromium,now with Lubuntu

Firefox seems to be faster.Is it normal?is it better to try Midori?or an other lightweight?which one do you suggest to me?

Thank you,Vasa1,for your kindness

---

### Post by vasa1 on 2017-05-28
Please ask any new questions by starting a _new_ thread but I would suggest staying with Firefox and Chromium. Security updates are more frequent with these browsers.

---

