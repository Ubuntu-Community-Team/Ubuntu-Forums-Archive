---
title: "Password request in &quot;terminal&quot;??"
date: 2007-08-13
forum: General Help
---

### Post by gimpster123 on 2007-08-13
trying to enter some code in the terminal, it prompts me for a password

I assume this is the same as my account log in password.

How do i type it in?

thanks,
gimp

---

### Post by merlinus on 2007-08-13
Yes, it is the user password.  Nothing will appear when typing,  Press Enter when finished to run the command.

-merlin

---

### Post by steveneddy on 2007-08-13
> **gimpster123 said:**
> 

How do i type it in?



Use the keyboard. It's the board looking thingy with all the letters and numbers on it.

:popcorn:

(couldn't resist)

---

### Post by bwtranch on 2007-08-13
Yep

---

### Post by bwtranch on 2007-08-13
After you get logged in it's time to play around a little. I said a little. Let's not get too crazy. Don't play around in the root folder unless you know what you are doing.  Now, for some basic commands:

bash that means that you did something wrong and after you get that for a while, you just want to bash someone's head in

/ means the root folder and everything is under that

/home/username is where you will usually start out and that is confusing and is not the same as

/home/username/Desktop

cd to change to a new dir like cd /home/username/shouldigobacktowindoze?

mkdir creates a new dir like mkdir /home/username/newdir

ls the most important command for a new user, shows the contents of the current dir

file shows what type of file it is

cp copies a file to a new dir without deleting it from the old one

mv does the smae as cp, but deletes the file from the old dir, also used to delete a file if no dir is specified

That's enough to get you started. Play around a little. As said before don't be root unless you know what's up

sudo su IS ROOT

exit to get outta there

clear to just clear the sceen

The up arrow will give you your last command.

---

### Post by merlinus on 2007-08-13
And whatever you do, this one is the biggest no-no:

sudo rm -R /

:guitar:

-merlin

---

### Post by lisati on 2007-08-13
> **steveneddy said:**
> Use the keyboard. It's the board looking thingy with all the letters and numbers on it.

:popcorn:

(couldn't resist)

Smartypants!

Now what can I usefully add to the contributions others have made to this discussion? 

For starters, here's a thought:
Many commands come with a "help" facility. Try:
```

cd --help

```
The two "-" are important....

---

### Post by bwtranch on 2007-08-14
Hi Merlin what does that do? Maybe I don't what to know :)

sudo su always works good for me when I want to be root for a while and then I exit.

I thought of 3 more that are good for a new user

lsmod
ifconfig
dmesg | less for finding mods that loaded at boot. Use the less option for easier paging

Anything else anybody can think of? I wish somebody had given me this when I first started out :)

You know, one thing I still don't know? How do ya get the box with the "code" at the top. Somebody said you just hit the pointy thing at the top of the reply screen. Did they mean a carat? Do I need HTML enabled? "cause I guess, well I know that I don't.  Hey, laugh if you wants, no, I don't know this! Geez:confused: Sorry, I'll get better :)

---

### Post by aldenhg on 2007-08-14
There's no reason to get snarky. Everyone was a noob at one point - some people just get to the game a little late. The purpose of these forums is to help and inform, not censure for inexperience. I'd expect more from some of the more senior forum members here.

---

### Post by bwtranch on 2007-08-14
No, lol, I was really asking :) I mean really, I don't know how to do that!:confused:

---

### Post by bwtranch on 2007-08-14
Re: #9 Maybe you were not speaking to me. But, I think I posted some good commands to get someone started. I am not new to Linux, but I am new to the forums and I was just asking how you get that little box that posts the code from a terminal. Looks more pro, ya know?

sudo apt-get install build-essential

---

### Post by merlinus on 2007-08-14
> 
 I was just asking how you get that little box that posts the code from a terminal.


Place the word code in brackets before the output, and /code in brackets after it.

-merlin

---

### Post by aldenhg on 2007-08-14
bwtranch  - That wasn't directed at you. I might have used the quick reply button and in some display modes that would make it look like I was bitching at you specifically, but I wasn't. In fact, I wasn't bitching at you at all. I'm just tired of people getting on the new people's cases about little things. We're here to help people and make Ubuntu easier, not to condescend. It doesn't help the uber-nerd stereotype that Linux gets attached to it when people act like Jimmy Fallon in the "Nick Burns: Your Company's Computer Guy" sketches.

---

### Post by merlinus on 2007-08-14
I agree. There is an Absolute Beginner Talk Forum for just this kind of thing, however.

-merlin

---

### Post by steveneddy on 2007-08-14
> **merlinus said:**
> And whatever you do, this one is the biggest no-no:

sudo rm -R /

:guitar:

-merlin

Why did you have to say that?

---

