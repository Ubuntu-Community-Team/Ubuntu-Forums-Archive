---
title: "The Ubuntu and or Mint main password torture."
date: 2013-05-08
forum: General Help
---

### Post by Costas100 on 2013-05-08
I was a user of Ubuntu for at least 10 years  and enjoyed every minute of it, including all the amazing software included with  each different version.

The unfortunate issue is that each new installation must have a main password occasionally called “keyring”. The problem is not with the Keyring, which most of the times is accepted, mine is simple and maybe this helps.

The problems begin when I try to access even a minor event (such as opening the gparted software or even simpler at times). As soon as I type my administrator password I get the reply that my password is incorrect, try again. 

I got to the point that I am looking for a linux distro with allowable availability of a simpler password, or even a no password at all .

Unfortunately lately I started using Linux Mint also a derivative of Ubuntu and the same issue started all over again.

So at the moment I am trying to find a solution in the available distros and who knows and  maybe something good will come out of it, for me and maybe for many users who are suffering on a daily basis, just like me.

I will post this letter to both the Ubuntu Forum and the Mint Forum and I hope this will help us all to find a solution.

Costas  Lazarou

---

### Post by fantab on 2013-05-08
Yours is a unique issue, if you are indeed typing your password correct.

Perhaps your issue could be of keyboard missing a key. Check the keyboard keys you use to type in your password maybe its missing a beat. Also try changing your password and see if it helps. 

I don't think you will find any distro that recommends no password feature. Its just not the Linux way.

---

### Post by tdockery97 on 2013-05-08
Is the password prompt box a little different than the others?  Just a shot in the dark, but maybe an update or something messed up your gksu configuration.  Try typing Alt+F2 to get the command prompt.  Enter the command:
```
gksu-properties
```
If it shows su as the command, change it to sudo.

---

