---
title: "Need help with how to be root"
date: 2007-03-26
forum: General Help
---

### Post by Masterj15 on 2007-03-26
I was trying to make an xgl session for beryl ( I'll never get beryl to work ) and when I try to go to the properties of the startxgl and go to the permissions it says that I am not the root user so I can't change the properties of this content. I am the only person on my computer. I am the only one that has a login and yet their telling me that I am not the root user. 

I know this is a noob question but this has been bothering me alot. How am I supose to ask more questions on beryl if I have not done what was required of me in the first place.:confused:

---

### Post by zvacet on 2007-03-26
It is just computer not arteficial inteligence.Tell him you are root.

```
sudo command_of_your_choice
```

if that is not enough
```
sudo -i
```

---

### Post by floke on 2007-03-26
When using the terminal you need the 'sudo' command to become the superuser - even if you are the only user on your system. Its a security feature to stop you doing stupid things, and to stop rogue software from wrecking your system, since any system changes require you to enter the password first.

When opening graphical programs as root user you need to use the 'gksu' command. so, in your case, open nautilus as root (open a terminal and enter 'gksu nautilus'). enter your password, and navigate to the file you want to change. Then alter the permissions there.

Hope this helps.

---

### Post by Masterj15 on 2007-03-28
both off you helped me thanks a lot! I keeped using chown when I herd about that command but this is better. And the first guy showed be that I have to get a computer that has artifical intelligence. (even though his brain would tak more space than my 250 gb hd.) (LOL):)

---

### Post by zvacet on 2007-03-28
Maybe something similar to Hall 9000?

---

### Post by Masterj15 on 2007-03-28
May I ask what is that? 

Noobquestion of course

---

### Post by tschneiter on 2007-03-28
[Courtesy of WikiPedia]("http://en.wikipedia.org/wiki/HAL_9000")

;)

---

### Post by darkos on 2007-03-28
As far as i know chown is used for setting the owner of directories. For example if you want the owner of this folder /home/user/blabla to be YOU, you type ```
sudo chown your_username_goes_here /home/user/blabla
``` Probably it will ask for your password :)

---

### Post by Masterj15 on 2007-03-28
Hall 9000 is cool. And the chown thing was the only thing I had until now.

---

