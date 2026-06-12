---
title: "My password in terminal."
date: 2022-03-25
forum: General Help
---

### Post by josephchrzempiec on 2022-03-25
Hello, As I'm still learning more and more about ubuntu and soon fully to move over from crazy windows. I was wondering if it is possing to stop asking me for a password Everytime I would like to install something? I understand for Server needs yes But in Desktop It is for me a little to much. Again Is there a way to bypass it on my laptop please?


Joseph

---

### Post by yetimon_64 on 2022-03-25
**I cannot express strongly enough how dangerous an idea this is.**

Even for desktop installs this is very close to "suicidal madness" with respect to getting malware installed or having remote exploits run on your install if it ever connects to the internet. Not a wise move at all, to put it plainly it is potentially a very disastrous move for you to make as a new linux user.

 Having said that above, read the first link in my signature line, it has the information you want (which I for one will not openly post here). However take a special note at the warning at the top of the section for "Remove password prompt for sudo"; in the bright yellow box surrounded by two red exclamation marks indicating just how dangerous this idea is.

My recommendation is for you to learn a lot more about Linux before you try this idea, you are stomping heavily through a security minefield with this. Even linux installs, with no security (like you are about to do if you remove password prompts), can be taken over and become part of a botnet or worse. This does not only affect you but ALL internet users if you lose control of your machine to a botnet. Passwords are not only for installing applications but also work to block the automatic installation of various malware.

Please don't do it; and if you do "good luck to you" you're going to need it. Regards, yeti.

---

### Post by CharlesA on 2022-03-25
You can remove the prompt for the password from sudo but I don't know if that affects GUI applications or not.

I would also recommend against it unless you have a specific use case for it.

For example, if you have a script that needs to start or stop a service, you might need to allow the user the script runs under to use sudo without a password.

You should read this before you make you decision, as removing the password prompt has a bunch of downsides.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by guiverc on 2022-03-25
I too will caution against it....

It's easy to make mistakes... esp. if *tired*, *in a hurry*, *stressed* etc.. and whilst being asked for the password won't stop you making mistakes, it at least slows you down a little.. 

When asked for that password, I use it as a *prompt* for me to validate if I've allowed for everything that can go wrong & what I've typed is what I intended.

We're all going to make mistakes (*even when we have a password required for `sudo`*), but I'd think really hard about removing a *safeguard* that can help prevent or reduce them.

---

### Post by wildmanne39 on 2022-03-25
If I remember correctly and I am pretty sure I do if you remove sudo you will not be able to install any applications from the moment you have removed sudo, there is a discussion here:

[https://askubuntu.com/questions/434525/can-sudo-be-reinstalled-after-being-removed](https://askubuntu.com/questions/434525/can-sudo-be-reinstalled-after-being-removed)

This was written in 2015 but it still applies.

---

### Post by QIII on 2022-03-25
We're all saying "Don't walk that way.  There's a cliff."

For a BASE jumper, that might just be what they are looking for.  But you haven't been around long enough to weave your parachute.

I've been around this computer gig since the '70s.  I figure the prompt for a password will give me a moment to think about a stupid mistake I am about to make.

---

### Post by DuckHook on 2022-03-26
This is going to feel a little like you are being ganged up on, but here goes:

Yet another vote for rethinking this.

You are a self&#8209;professed Windows refugee. We welcome you to the Linux&#8209;verse.

Before you fully embrace Linux, you may wish to take a read through the link in my sig: Linux is not Windows.

What follows is not personal; it's my standard spiel:

The reason that Linux is a more secure ecosystem than Windows has little to do with the inherent security of the OS itself. OSes are not magic wands that perform amazing miracles of their own accord. Linux security has far more to do with the fact that Linux is mainly the domain of geeks who take security seriously and avoid the bad habits that Windows users have become habituated into thinking as normal.

So, please don't drag bad Windows habits into your new Linux environment. In ignoring Linux security, you become not only a danger to yourself, but also a danger to the rest of us.

Linux may be inherently safer than Windows, but this is true in practice only if its users cooperate and maintain security as a primary goal. Nerfing challenge/response is antithetical to that goal. It undermines the difficult strides that Linux has thus far made to elevate itself from the atrocious morass that make up proprietary user practices.

Other very knowledgeable forum members have cautioned you against the danger to yourself that would result from the absence of challenge/response. I wish to emphasize the danger that you could become to others.

One of the easiest ways for malware to infest your system is through exactly the mechanism you are trying to implement. Consider: if it no longer becomes necessary to respond to a security challenge to install an app you want, then what is there to prevent the installation of an app you do not want? If you nerf challenge/response, then the answer is a very loud "nothing". It becomes child's play for a bad website to inject some nasty into your machine that turns it into another node in a bot farm.

This is, in fact exactly the loosey&#8209;goosey approach to security that turned Windows XP into a security joke—or, at least, it would have been a joke were it not such a catastrophe. Please don't bring that attitude, those practices and those results into Linux. It's not okay and, after all these years, it's not really even forgivable.

I know: harsh words. But when it comes to security, it has become a harsh world out there. Harsh words cannot be spared.

---

### Post by The Cog on 2022-03-26
Try to appreciate the difference between being a user and being an administrator. They are different roles, and this is true of both Windows and Linux. 

Users can install software in their own private area, in both Windows and Linux, but when installing system software you have to be a system administrator. With Windows, you "Run as administrator" the installer, with Linux you use sudo. I know that many years ago Windows didn't have this distinction (e.g. W95) but it has had it for a long time. Unix/Linuix has always had it. These days, the difference in both systems is clear cut. 

I also know that when you are tinkering with a new installation, bedding it in, you spend a lot of time doing system admin type work and have to re-verify your credentials when you go to make system changes, and I know it gets irritiating. But as time goes on that becomes less frequent and less intrusive. When I came to Linux from Windows ME it felt odd to me - I hadn' been aware of the fact that I was switching between user and admin roles - I just did what I felt like doing. Looking back, I think that appreciation of when you are doing system admin so ought to be more thoughtful about your actions is a good thing. So I'm another one who would encourage you to get used to this way of doing things. You do get used to it, in the same way that you get used to wearing car seat belts. An experiencd mechanic could easily disable the "put your seat belt on" buzzer, but they don't.

In summary, like DuckHook's well written response, I advise to go with the flow on this one. My contribution is to try to encourage you to be aware of the difference between being a user and being an admin, and to appreciate that they are different roles.

P.S. In the terminal, when you use sudo, a timer starts that allows that terminal to use sudo again (within 15 minutes I think) so you don't have to keep on entering the password. The next step up is to use "sudo -i" which turns the terminal into a root login so you don't need to keep typing sudo either. I do that if I know I'm going to need more than one or two commands as root.

---

### Post by yancek on 2022-03-26
>  I was wondering if it is possing to stop asking me for a password Everytime I would like to install something? 

This doesn't seem like something which could be a major problem.  I would think most home computer users would review software available immediately after installing the OS and install needed software.  Your post makes it sound like something that happens very frequently which should not be the case unless you are installing and testing a large variety of software.  Ubuntu/Linux ask for a password, windows asks to mouse click run as administrator.

---

### Post by Impavidus on 2022-03-26
> **yetimon_64 said:**
> @ OP, this is a good idea; instead of undermining security of your install by removing the sudo prompts completely create a custom script for installing applications without a password as per your first post. This will allow installing (only) without a password, it is a bit involved to set up but once set up will allow you to install applications without a password but retain system security more generally.

Example: create a script and store in your home directory bin folder. If the ~/bin folder doesn't exist create it...
```
mkdir $HOME/bin
```
Log out of the desktop and log back in again so your $HOME/bin is in you user's path.
Edit: Post this has been quoted from deleted. The quoted part doesn't appear dangerous.

When I read that I think of the folowing lines in sudo's man page:```
     Users should _never_ be granted **sudo** privileges to execute files that are
     writable by the user or that reside in a directory that is writable by
     the user.  If the user can modify or replace the command there is no way
     to limit what additional commands they can run.
```
If a user can run a specific script with sudo and without a password, and the same user can modify that script, that user can run every command with sudo and without a password from that script. I would store the script in /usr/local/sbin/ and make sure only root can modify the script.

---

### Post by yetimon_64 on 2022-03-26
> **Impavidus said:**
> When I read that I think of the folowing lines in sudo's man page:```
     Users should _never_ be granted **sudo** privileges to execute files that are
     writable by the user or that reside in a directory that is writable by
     the user.  If the user can modify or replace the command there is no way
     to limit what additional commands they can run.
```
If a user can run a specific script with sudo and without a password, and the same user can modify that script, that user can run every command with sudo and without a password from that script. I would store the script in /usr/local/sbin/ and make sure only root can modify the script.
After reading this I have asked staff to remove my post. I may have to remove the links and move my custom scripts to /root/bin directly or /usr/local/sbin as you mention. Thanks for pointing that out.

I will have to review my set up with respect to this. Cheers, yeti.

---

### Post by josephchrzempiec on 2022-04-16
Hello, I'm Sorry I was away Burrying a good friend of mine. And When I got back today I read all the reply comment back. I now fully understand why a password is needed in terminal. I will not be removing it or trying to figure out how to remove it. Thank you all for helping me to understand it.


Joseph

---

### Post by HermanAB on 2022-04-16
The problem is that access to Linux machines are highly sought after by hackers since they frequently belong to sysadmins and offer easy access to powerful servers. So, protect your login information carefully, even on a lowly little laptop.

---

### Post by ActionParsnip on 2022-04-16
Mild inconvenience removal or system security? Hmmm..... Tough one. Tell me, do you protect your email with a password and 2FA? It's such a hassle to type your password to access it. And your online banking... Just get rid of the password, makes login so much quicker....

---

