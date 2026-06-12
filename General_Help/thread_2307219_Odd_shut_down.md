---
title: "Odd shut down"
date: 2015-12-22
forum: General Help
---

### Post by Terone on 2015-12-22
I'm using Kubuntu 14.04. Now usually when I shut down my computer, it would show the kubuntu logo and shut down normally, but recently I noticed it doesn't do that anymore. It merely shows a black screen with two lines of code for a split second and then shuts down the computer weirdly. And by weirdly, I mean it shuts down as if I long pressed the power button for a forced shutdown. 

I've only been using Linux for a week now and would love some advice on how to fix this.

---

### Post by veddox on 2015-12-25
Hi Terone,

Welcome to the Ubuntu Forums and the Linux world! That sounds like an odd problem you're having, I think we need some more information to try and diagnose what's wrong. So here are a couple of questions for you:


[LIST=1]
[*]Did you change anything on your computer before the problem started? Changes can include installing new programs, uninstalling old ones, deleting system files, changing system files, etc.
[*]Did the computer crash or where there any other anomalies just before the problem first started?
[*]How exactly do you shut your computer down? Do you do it graphically via the "shut down"-menu, using the physical power button or via terminal?
[*]What exactly are the "two lines of code" that you say are shown on the screen when it shuts down? Knowing what they are could be very important, as they might contain an error message. If you can't read the writing because it disappears to fast, film the screen with a camera as you shut the computer down, then try to decipher the text from one of the movie clip frames.
[/LIST]

Hopefully the answers to these questions will make it a bit clearer what the root of the problem is.

Merry Christmas!
veddox

P.S. On the off-chance that this is actually a very simple thing, try pressing ESC while the computer is shutting down and tell us what happens. (If you want to know why and aren't afraid of details, you can read up here: [https://wiki.ubuntu.com/Plymouth](https://wiki.ubuntu.com/Plymouth))

---

### Post by Terone on 2015-12-26
> **veddox said:**
> 

[LIST=1]
[*]Did you change anything on your computer before the problem started? Changes can include installing new programs, uninstalling old ones, deleting system files, changing system files, etc. 
[*]Did the computer crash or where there any other anomalies just before the problem first started? 
[*]How exactly do you shut your computer down? Do you do it graphically via the "shut down"-menu, using the physical power button or via terminal? 
[*]What exactly are the "two lines of code" that you say are shown on the screen when it shuts down? Knowing what they are could be very important, as they might contain an error message. If you can't read the writing because it disappears to fast, film the screen with a camera as you shut the computer down, then try to decipher the text from one of the movie clip frames. 
[/LIST]


1. Yes, I installed Synaptic Package Manager. It was more easier to install packages that way. (On a side note, I installed Bibus, Conky manager and reinstalled mscorefonts to get the lovely "Times New Roman")(Double side note, Conky is a lot of fun. Learning how to create my own conky but there was nothing related to shutdown scripts, only on boot.)
2. During the day I did 1. the problem started.
3. I shut down via the graphical interface. Simply, the start menu and then "shut down". (I'm using the KDE)
4. Well.... Few days later, it started shutting down like normal again. So I guess this is "solved"? I'm surprised those messages aren't saved in some log somewhere.
Can't I do something like dmesg | grep -i boot?

---

### Post by Terone on 2015-12-26
Oh, and Merry Christmas btw. Fun celebrating Christmas by tweeking ubuntu. lol.

---

### Post by Petro Dawg on 2015-12-26
> **Terone said:**
> ...I'm surprised those messages aren't saved in some log somewhere...

I can only point you to in a general direction.  Log files are typically saved in the /var/log directory.  I'm not an expert on log diagnostics so I am not sure which, if any, of those many log files would capture shut down issues.

---

### Post by Petro Dawg on 2015-12-26
> **Terone said:**
> Oh, and Merry Christmas btw. Fun celebrating Christmas by tweeking ubuntu. lol.

Yup, I celebrated Christmas today battling a random power off problem, BIOS upgrade, and setting up my home file server for the umpteenth time.  Now that all that is behind me I think it was a good educational day.  

Just in case you weren't aware, there is a Conky mega-thread [here]("http://ubuntuforums.org/showthread.php?t=281865") on the forums.  If you are interested in posting what you have accomplished or learning how to do more with your Conky set-up, it is a good place to go.

Merry Christmas to you as well.

---

