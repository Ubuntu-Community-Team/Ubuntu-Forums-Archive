---
title: "Problems with my files"
date: 2008-01-20
forum: General Help
---

### Post by MarySaints on 2008-01-20
Hello there, I am new in the forum... :D I'm Mary Saints, very pleased to meet y'all!
So, I use Ubuntu-Gnome in my computer (and I love it <3), but these few days I've noticed a "problem" that surely annoys me... I'd like to put new things into some programs that I regularly use (GIMP, Amsn), but I cannot install anything because it is blocked, somehow. What should I do to be able to paste new folders or files inside the programs?
Thank you for the attention and bye!

---

### Post by MarySaints on 2008-01-20
I really need help, maybe this thing could possibly give me more troubles in the future. :(

---

### Post by mdpalow on 2008-01-20
I'm sure this message makes perfect sense to you, but I'm having a bit of a problem understanding. :confused:    :)

Try and be more specific too as it does help us help you.

You are using Ubuntu 7.10 / 32-bit?

What is it you want to install to Gimp aMSN?

What does 'blocked' mean exactly to you? Is there an example of some message you could copy and paste for us to see? Did you mean you got a message that says you don't have permissions? Usually, when you want to install something you have to place the ' sudo ' command beforehand and then enter your password when asked for it.

You shouldn't have any problems 'pasting' folders in your /home directory, but if you're trying to create or paste a folder in / you wouldn't be able to do that unless you again used the 'sudo' command or brought up your nautilus in sudo mode. example:

```
gksudo nautilus
```

type the above into a terminal window if you're trying to create folders outside of /home. Might seem like a hassle, but this is why Linux Ubuntu is more secure for you.

I'll leave it at this for now... I'm sure if you edit your message, you will get a much better answer in no time at all. 

Good luck to you and welcome to Ubuntu...

---

