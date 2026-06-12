---
title: "[SOLVED] Auto sudo ( disable sudo prompts )"
date: 2007-10-31
forum: General Help
---

### Post by sistoviejo on 2007-10-31
is there a way to make ubuntu automatically enter sudo password for me?
I was able to do this in vista using this program: [http://www.tweak-uac.com/](http://www.tweak-uac.com/)
It disables all "Enter administrative password" prompts in windows vista.
I was wondering if I could do this in ubuntu.

One alternative could be to run X using root user maybe? But I don't want ubuntu warning me that it is unsafe to run X as root. So can I disable that warning?

I would prefer to run X as a plain user though.. and have the sudo prompts disabled or have the password entered automagically.

Any help appreciated.
Thanks.

---

### Post by volksman on 2007-10-31
At a CLI:

visudo

In Gutsy I had to remove the %admin line and add a line for my user:

username ALL=NOPASSWD: ALL

That will do it... ;)

---

### Post by mcduck on 2007-10-31
That would be just as insecure as running always as root. I seriously recommend against doing anything like this.

---

### Post by sistoviejo on 2007-10-31
> **volksman said:**
> At a CLI:
visudo
In Gutsy I had to remove the %admin line and add a line for my user:
username ALL=NOPASSWD: ALL
That will do it... ;)

thanks! it worked

[QUOTE=mcduck]
That would be just as insecure as running always as root. I seriously recommend against doing anything like this.
[/QUOTE]

I know what I'm doing... I've been using linux for years.
Care to explain why running as root is insecure?

---

### Post by sistoviejo on 2007-10-31
volksman:
Actually it didn't work.
And now I can't sudo.
I can't even visudo because I can't sudo.
Any ideas?

here's what I'm trying to do:

silvio@silvio-laptop:~/gDesklets-0.36beta$ visudo
visudo: /etc/sudoers: Permission denied
silvio@silvio-laptop:~/gDesklets-0.36beta$ sudo visudo
silvio@silvio-laptop:~/gDesklets-0.36beta$ sudo bash
silvio@silvio-laptop:~/gDesklets-0.36beta$ visudo
visudo: /etc/sudoers: Permission denied
silvio@silvio-laptop:~/gDesklets-0.36beta$ sudo visudo
silvio@silvio-laptop:~/gDesklets-0.36beta$ 


sudo doesn't do anything now.

---

### Post by aysiu on 2007-10-31
> **sistoviejo said:**
> volksman:
Actually it didn't work.
And now I can't sudo.
I can't even visudo because I can't sudo.
Any ideas?

here's what I'm trying to do:

silvio@silvio-laptop:~/gDesklets-0.36beta$ visudo
visudo: /etc/sudoers: Permission denied
silvio@silvio-laptop:~/gDesklets-0.36beta$ sudo visudo
silvio@silvio-laptop:~/gDesklets-0.36beta$ sudo bash
silvio@silvio-laptop:~/gDesklets-0.36beta$ visudo
visudo: /etc/sudoers: Permission denied
silvio@silvio-laptop:~/gDesklets-0.36beta$ sudo visudo
silvio@silvio-laptop:~/gDesklets-0.36beta$ 


sudo doesn't do anything now.
This should help you fix sudo:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by sistoviejo on 2007-10-31
> **aysiu said:**
> This should help you fix sudo:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

I can't boot in recovery mode..
I get this error message: 
"error receiving uevent message: no buffer space available"

------------------------------------------------------------------------------------------------------------

UPDATE:

Solved!

Here's the solution if you can't sudo and can't boot into recovery mode:  
1 - Boot live CD
2 - Mount root partition from the hard drive
     mkdir /media/hdd
     mount -t ext3 /dev/sda3 /media/hdd
3 - fix your sudoers file
     cd /media/hdd/etc
     vi sudoers

Procedure for fixing your sudoers file will change depending on what is wrong with it. 
In my case I had to change this:

# Members of the admin group may gain root privileges
#%admin ALL=(ALL) ALL
username ALL=NOPASSWD: ALL

to this:

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
#username ALL=NOPASSWD: ALL

------------------------------------------------------------------------------------------------------------

I lost my interest in having sudo auto auto enter the password for me.
I guess this was the security problem mcduck talks about? LOL. just kidding.

---

### Post by mcduck on 2007-10-31
> **sistoviejo said:**
> 
I know what I'm doing... I've been using linux for years.
Care to explain why running as root is insecure?
Using minimum privileges required for the task at hand is pretty much the base of security in Linux/Unix. If you run as root, every single program you run has root privileges, and thus any security problem in any of your programs becomes a serious security risk and possible way to gain full access to your machine.

The basic rule is to never log into graphical desktop as root.

If you make sudo not require a password means that anybody getting access to your account (by some way or other) would also get full access to your system.

---

### Post by sistoviejo on 2007-10-31
> **mcduck said:**
> Using minimum privileges required for the task at hand is pretty much the base of security in Linux/Unix. If you run as root, every single program you run has root privileges, and thus any security problem in any of your programs becomes a serious security risk and possible way to gain full access to your machine.

The basic rule is to never log into graphical desktop as root.

If you make sudo not require a password means that anybody getting access to your account (by some way or other) would also get full access to your system.

How could they get access to my basic account?
What would prevent them from them from erasing my basic account's documents if they obtained access?
Why would I care if they got root access after they got basic access and deleted/copied everything that the basic account has access to?

---

### Post by scorp123 on 2007-10-31
> **sistoviejo said:**
>  How could they get access to my basic account? There are many ways ... 

> **sistoviejo said:**
>  What would prevent them from them from erasing my basic account's documents if they obtained access?  Erase? No. They want your credit card data, your mail passwords, all the spicy details about your private life .... Erasing stuff is too obvious. Messing around with your private life is much more fun ...

> **sistoviejo said:**
>  Why would I care if they got root access after they got basic access and deleted/copied everything that the basic account has access to?  If they got *that far* then it's already too late for worrying. :)

---

### Post by sistoviejo on 2007-10-31
> **scorp123 said:**
> There are many ways ... 

 Erase? No. They want your credit card data, your mail passwords, all the spicy details about your private life .... Erasing stuff is too obvious. Messing around with your private life is much more fun ...

 If they got *that far* then it's already too late for worrying. :)

If that is a risk even while using my basic account I guess running as root doesn't impose such a large security risk.
I do it on my home web server. But I don't see the reason for doing it on my laptop.

---

### Post by mcduck on 2007-10-31
> **sistoviejo said:**
> If that is a risk even while using my basic account I guess running as root doesn't impose such a large security risk.
I do it on my home web server. But I don't see the reason for doing it on my laptop.

Ever heard of bot networks, spammers and such? Getting root access on your machine would pretty much turn it into somebody else's machine, usually used to do all kinds of illegal things.

---

### Post by sistoviejo on 2007-11-01
So basically the effect of having the sudo password auto entered for me is increased risk of viruses and spyware.
what anti virus software do you guys recommend for linux?

---

### Post by mcduck on 2007-11-01
> **sistoviejo said:**
> So basically the effect of having the sudo password auto entered for me is increased risk of viruses and spyware.
what anti virus software do you guys recommend for linux?

There isn't really any Linux viruses or spyware around so no need for any software to scan for that kind of stuff.

But there definitely are all kinds of crackers and script kiddies etc. who are just as big threat to Linux users as they are to those running OS X or Windows. And the only way to protect yourself from them is good overall security, and of course a firewall (if you run _any_ services responding to incoming connections).

---

### Post by blackbelt_jones on 2007-11-19
> **mcduck said:**
> That would be just as insecure as running always as root. I seriously recommend against doing anything like this.

While there may be an argument to be made against enabling sudo for no password, by no stretch of the imagination is it just as insecure as running always as root.    When you're running as root, everything that every program you're running does has the ability to overwrite anything else.  sudo assigns root privelages to  a single command and nothing more.  

Assuming that the physical computer itself is secure ( e.g., located in a home and not an office) I'm not sure what the added security risk is.   If a person has obtained remote access to my user account, what are the odds that he or she already has my password?   I'm not good at assesing the risk, but no way is it comparable to running as root all the time.  Can't I assume that Ubuntu (and Slackware, and Vector, and no doubt many more distros) wouldn't have put the option in the sudoers file if it was that dangerous?

---

### Post by blackbelt_jones on 2007-11-19
> **sistoviejo said:**
> If that is a risk even while using my basic account I guess running as root doesn't impose such a large security risk.
I do it on my home web server. But I don't see the reason for doing it on my laptop.
Let me say again for emphasis, it's a safe bet that enabling sudo with no password is less secure overall than keeping the password, but it's a long long way from running all the time as root.

What?  Did you just that you're running a home web server as root?  My GOD, that sounds like a bad idea.     I've never ran a home webserver, but I've heard more than once that a home webserver is like a beacon to attract malevolent hackers.

I don't really have the experience to speak authoritatively on this stuff.  Anybody?

Incidentally,  a live CD can be great for keeping sensitive data  from being left behind on your hard drive.   I always use kanotix for online shopping when I reboot, nothing of my credit card information is left for someone else to find.

---

