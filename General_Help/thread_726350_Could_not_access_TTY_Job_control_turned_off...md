---
title: "Could not access TTY: Job control turned off.."
date: 2008-03-16
forum: General Help
---

### Post by VincentTucker on 2008-03-16
'Course! What a heavenly error

So, I had school and work to pay attention to so I put my computer in storage for a while. I only just brought it back. Now I know this has nothing to do with the error, just the reason it makes me reeeeal sad like. Anywho. It boots up fine and I made the god-awful mistake of letting my brothers use it. Now I'm all protective of my files and what-not so I have them on a separate account so they don't have permission to get to them. Now what I didn't know was that they new the password to the root account so they snuck in there and tried to set the permissions so they could look at my files.

But they didn't do that by simply going to my main file and changing the permissions. No no no. They went to the big almighty folder. Because why just set  a few files to give everything access to when you can have access to the entire computer! So, they tried changing all of that, but they apparently got tired of waiting for it to finish, seeing how it was apparently taking too long. So they tried to just shut it down, which didn't actually work so they had to hold down the button.

 They left, I went back in, I tried to turn it onnnnn. Woahdamn, blackscreen. Oh look at them tiny letters. What's they say. "Could not access TTY: No job control.....BUT HERE'S A COMMAND PROMPT! HAVE FUN! 8D"


It took a while to force all them details out of them, but I figured the more detail the better.

So. Is this fixable?

---

### Post by scragar on 2008-03-16
if you could pin down what exactly they did you may be able to reverse the damage, although without being able to launch TTYs the odds are some commands may not work(for starters find out if they used sudo or actualy got into root, then:
```
cat /home/USERNAME/.bash_history | less
```or```
cat /root/.bash_history | less
```as required and scroll down to the end of the list for most recent commands.

---

### Post by VincentTucker on 2008-03-16
I do know that they did use the root account. 
I'll have to wait a while until I try anything. I'm stuck going to the Public Library 'till I fix this.

---

