---
title: "Huge problems because of stupidity"
date: 2007-02-09
forum: General Help
---

### Post by Bjarkehl on 2007-02-09
I’m completely new in relation to Ubuntu (6.10), and have been trying to install Stardict and some dictionaries. During this process, and because of my lack of knowledge of the damage I could do, I changed the setup for my user account (I think it was under "System" - "Manage users & accounts" (or something like that), so it was based on the "root" instead of my "home" and desktop. So both the "root" user and my user were based on the "root" instead of mine being based on "home" (I'm unsure if this was really how it was setup. It was just the automatic setup). I did this, because I thought I then could paste the dictionaries into my usr/share/stardict/dic/. First, I failed in doing this. Second, after restarting my computer I suddenly found out that I couldn't log on the computer anymore, since my username doesn't connect to my "home". Ubuntu recommended trying to fix the problem in "save version", but I can only get "Terminal" to work, and since I'm a completely newbie, I don't know how to solve this problem in commando prompt. Because of this, I no longer can access my files on the computer, so I'm leaved with the only possibility of formatting and reinstalling, if you (men and women) can't help me solve this problem. So if anybody has any good advices please post them as soon as possible (I'm currently writing from my girlfriend's computer). I'm getting pretty desperate. Thanks for your help, I REALLY appreciate it.

Bjarke

---

### Post by Paerez on 2007-02-09
OK do the ubuntu Recovery mode, and when you get to a terminal, put in:

usermod -d /home/yourname yourname

so, my login is "nick" so I would type:

usermod -d /home/nick nick

then press CTRL+ALT+DEL to reboot and you should be ok!

---

### Post by lhtown on 2007-02-09
Hey, your stupidity wasn't that bad. At least you are using the right operating system. ;-)

Maybe you could login in using sudo from a terminal. I can't explain how to do it though since I don't really know what you would have to fix.

On a Unix/linux/bsd system, your password is pretty important.

You should still be able to copy any data off your hard drive by connecting it to another computer.

Also, you might be able to set up a new user (search the forums or hope someone helps you out here) and then copy over your data and delete your original user to fix it.

---

### Post by PurplePenguin on 2007-02-09
In the linux world, there are no huge problems, just huge learning experiences. :D

---

### Post by DagMan on 2007-02-09
And hardly ever a need to format and reinstall

---

### Post by Bjarkehl on 2007-02-10
I'm thankful for your support. Been trying the terminal mode and usermod-command (since my username is bjarke1405 I typed "usermod -d /home/bjarke1405 bjarke1405")
, but after doing this it says: "Usermod: unable to lock password file". What is there to be done to this? I really appreciate your help.

---

### Post by bigken on 2007-02-10
try sudo usermod -d /home/bjarke1405 bjarke1405

---

### Post by Bjarkehl on 2007-02-10
Hi,

Thank you for both your morale and technical support. Now it's fixed through the "sudo usermod -d /home/name name". Regards Bjarke

---

### Post by bigken on 2007-02-10
pleased your sorted :)

---

