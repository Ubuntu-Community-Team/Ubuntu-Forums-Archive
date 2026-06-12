---
title: "Why All the Passwords?"
date: 2007-02-17
forum: General Help
---

### Post by lexen on 2007-02-17
I love Ubuntu and have been using it as my only OS for a few months now.  I honestly believe that it is the best OS out there, but I really don't understand why I need to put in my password so much.  I haven't heard anyone else bring this up, but it seems so unnecessary. 
     The only thing that I can come up with is that it is a matter of security, but do I really need that much security from someone sitting down at my PC?  I don't believe this stops the threat of online hackers, so I guess they think that someone is going to mess something up, but every user has administrative privileges so they could just sign in and do whatever they wanted.
     What I am really trying to say is, it would be nice if at installation they asked you if you wanted to password protect your OS, or, if your like me, you would have the option to simply turn off said protection.
     If there is some reason why it is set up the way it is and I simply wasn't aware of it, then please let me know.  Otherwise, I think 7.04 should have the option to turn passwords off.



 - Lexen

---

### Post by Hiram Abiff on 2007-02-17
This is my 3rd day with Linux so I might be way off base but I remember reading somewhere that it prevents software from installing itself without your knowledge.  Not to protect itself from the user.  You could log in as root but it's not recommended

---

### Post by CCBalla10 on 2007-02-17
> **lexen said:**
> I love Ubuntu and have been using it as my only OS for a few months now.  I honestly believe that it is the best OS out there, but I really don't understand why I need to put in my password so much.  I haven't heard anyone else bring this up, but it seems so unnecessary. 
     The only thing that I can come up with is that it is a matter of security, but do I really need that much security from someone sitting down at my PC?  I don't believe this stops the threat of online hackers, so I guess they think that someone is going to mess something up, but every user has administrative privileges so they could just sign in and do whatever they wanted.
     What I am really trying to say is, it would be nice if at installation they asked you if you wanted to password protect your OS, or, if your like me, you would have the option to simply turn off said protection.
     If there is some reason why it is set up the way it is and I simply wasn't aware of it, then please let me know.  Otherwise, I think 7.04 should have the option to turn passwords off.



 - Lexen

You already answered your question.  It is because of security.  With all these passwords to run programs, it helps from getting viruses.  Did I mention that windoze has 400,000+ viruses while I have yet to hear about Linux getting anything.  Makes for a really stable OS...Be thankful for this because all of your information is really secure.
CHEERS!
Austin

---

### Post by llamakc on 2007-02-17
[B]but every user has administrative privileges so they could just sign in and do whatever they wanted.

[/B]No they don't, unless you give them admin privileges. The only user with admin privileges as default is the first one created during the install.

---

### Post by lexen on 2007-02-17
I hear what you guys are saying, but like you said CCBalla10, there are next to no viruses for linux.  Besides, other versions of linux don't have as many passwords as Ubuntu and they are still secure.  I think that there has to be a better way of duing this.  If you don't want programs running without you permission then I would think that you could have that done automaticly, because I have never seen it ask me for a password when I wasn't doing something.

     You guys have a lot of valid points, but with linux already being so secure, it seems wastful.




Thanks for all the comments,
     Lexen

---

### Post by mkw87 on 2007-02-17
Just because there isn't viruses/spyware for Linux now doesn't mean there won't be, and if they waited for that to happen it would be a bit late to implement security wouldn't it be?  What it prevents is software that install itself automatically.  It is done with various purposes, most often to turn your computer into a zombie/slave/bot for them to do spamming with, etc.

For more its not a big deal to type in the password, and its well worth it to know you won't be losing all of your data because you visited a shady website or got a malicious email.

---

### Post by Muzik83 on 2007-02-17
This is totally insecure, so dont do it.

Here is how you can make your system not ask for passwords every time (very unsecure, dont do it!) you need to do an administrative function.

Be very careful doing this, if the sudoers file is edited wrong, you wont be able to sudo.  I suggest you set the root password first, so you can log in with root in case you do wreck the sudoers file.

Use your favourite editor to edit the file
/etc/sudoers

Then add a line like this:
%myadmingroup ALL=(ALL) NOPASSWD:ALL

where myadmingroup is a group of users whom you don't want to have to enter a password with

Again....unsecure, dont do this (but shh, I do)

-sean

---

### Post by namelessone on 2007-02-17
> Besides, other versions of linux don't have as many passwords as Ubuntu and they are still secure.

Actually, Ubuntu has *less* passwords than other Linux distros. In Ubuntu, the password you use to gain root access is the same as the password you use to log in.

It should also be noted that the root password doesn't just make your machine safer and less prone to viruses, but it makes it safe from dumb users like me accidentally destroying the computer with commands like

> rm -r /

which deletes everything on your hard drive. This is, of course, an extreme example, but you should get the idea. Requiring the user to type in a password before doing anything that has the possibility of damaging the system makes the user think twice before he does anything stupid.

---

### Post by aysiu on 2007-02-17
As namelessone said, Ubuntu has fewer passwords than other Linux distros. It also asks you to enter your password only once every 15 minutes, whereas most other Linux distros will ask you to enter your password every time you want to switch to root user.

If it bothers you that much, enable a root login (System > Administration > Login Window) and log in as root. Don't say we didn't warn you, though...

---

### Post by Maestro23 on 2007-02-17
> **aysiu said:**
> As namelessone said, Ubuntu has fewer passwords than other Linux distros. It also asks you to enter your password only once every 15 minutes, whereas most other Linux distros will ask you to enter your password every time you want to switch to root user.

If it bothers you that much, enable a root login (System > Administration > Login Window) and log in as root. Don't say we didn't warn you, though...

Pandora's Box...:)

---

### Post by g8m on 2007-02-17
What passwords?

You can define autologin in gdm/kdm so you get automatically logged in.

You can set "nopasswd" in visudo, so the thing doesnt ask for a password with sudo.

The only time I have to login is, is after a reset of X or logoff.

Safety, I defend my computer personally. 

And I am behind a router, that holds of internet attacks.

---

### Post by namelessone on 2007-02-17
> **g8m said:**
> What passwords?

You can define autologin in gdm/kdm so you get automatically logged in.

You can set "nopasswd" in visudo, so the thing doesnt ask for a password with sudo.

The only time I have to login is, is after a reset of X or logoff.

Safety, I defend my computer personally. 

And I am behind a router, that holds of internet attacks.

Just because you are behind a router with a firewall doesn't make you safe. As long as you are hooked up to the internet in any way, shape, or form, your computer is vulnerable to attacks.

---

### Post by aysiu on 2007-02-17
> **namelessone said:**
> Just because you are behind a router with a firewall doesn't make you safe. As long as you are hooked up to the internet in any way, shape, or form, your computer is vulnerable to attacks.
For example:
[&#8216;Drive-by pharming&#8217; means routers with default passwords at risk](http://www.itwire.com.au/content/view/9658/1103/)

---

### Post by g8m on 2007-02-18
Yeah, like I would be so stupid to not change all the passwords on my router. Even the upnp is turned off because of possible attacks. It doesnt react to pings so no denial of service. No services like dhcp. Only weak point is the wireless access. 

But then again, if you lock your house completely, it just means the damage the burglar causes to force entry will be higher. Not saying you shouldnt lock your house, but just the normal precautions will be enough to lock out most. If someone really wants to enter, and has the means to he will anyway.

---

### Post by namelessone on 2007-02-18
Hackers, like burglars, tend to look for the easy machine to exploit. If your machine is password protected, and is behind a firewall (or more than one firewall), your machine will be less prone to malicious individuals and software than a machine without.

In other words, security is good. Use passwords.

---

