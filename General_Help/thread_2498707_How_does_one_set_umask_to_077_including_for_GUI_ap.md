---
title: "How does one set umask to 077 including for GUI apps?"
date: 2024-06-24
forum: General Help
---

### Post by Paddy Landau on 2024-06-24
I know how to set umask to 077 (equivalent to [FONT=courier new]umask u=rwx,go=[/FONT]) in [FONT=courier new].bashrc[/FONT] and [FONT=courier new].profile[/FONT]. However, that only affects CLI apps that run from the terminal.

I want everything in my home to be [FONT=courier new]umask 077[/FONT], even when using GUI apps such as Nautilus or GIMP.

I've searched the internet and found several answers. Only one of them worked, but there's a problem.

Here's the one that worked:

[LIST=1]
[*]Edit [FONT=courier new]/etc/login.defs[/FONT]
[*]Change [FONT=courier new]UMASK 022[/FONT] to [FONT=courier new]UMASK 077[/FONT]
[*]Change [FONT=courier new]USERGROUPS_ENAB yes[/FONT] to [FONT=courier new]USERGROUPS_ENAB no[/FONT]
[*]Restart the machine.
[/LIST]
This does indeed work (with a couple of curious exceptions such as in flatpak's [FONT=courier new]~/.var[/FONT]).

The problem is that this affects not just my user but also root, which has the potential to cause problems.

I want something that will affect only my user (and, optionally, and other non-root user).

Is this possible?

I'm using Ubuntu 22.04.

Thank you

---

### Post by currentshaft on 2024-06-24
You could try setting umask in /etc/passwd, but I have to ask ... what do you think a more restrictive value will meaningfully add to your system?

---

### Post by Paddy Landau on 2024-06-24
> **currentshaft said:**
> You could try setting umask in /etc/passwd
Thank you, I'll try that. Is there a "proper" way to do it, or do I simply edit the password file?
> **currentshaft said:**
> what do you think a more restrictive value will meaningfully add to your system?
It feels like the right thing to do. The default umask is 022, which means that files by default grant access to all. That seems strange; if two or more users share a computer (each with their own user account), surely they should be able to expect privacy by default? I could use umask 027 instead of 022, I suppose, but the question remains.

---

### Post by Paddy Landau on 2024-06-24
I've been looking up the syntax of the password file, and it doesn't contain information about the umask.

Did you mean /etc/passwd, or something else?

---

### Post by currentshaft on 2024-06-24
It's /etc/password, specifically the GECOS field ([https://en.wikipedia.org/wiki/Gecos_field](https://en.wikipedia.org/wiki/Gecos_field))

It's an optional field that is usually blank.

Looks like the "chfn" command supports setting it via the "other" field - [https://manpages.ubuntu.com/manpages/focal/en/man1/chfn.1.html](https://manpages.ubuntu.com/manpages/focal/en/man1/chfn.1.html)

In my opinion, and this is not meant to be derogatory nor discourage anyone from hardening their system, I believe the user separation boundary on a Linux system is extremely trivial to cross, and while umask is a good hygiene practice, it is not a meaningful security control.

---

### Post by Paddy Landau on 2024-06-24
> **currentshaft said:**
> It's /etc/password, specifically the GECOS field ([https://en.wikipedia.org/wiki/Gecos_field](https://en.wikipedia.org/wiki/Gecos_field))
Thanks, but that field seems to hold only information (name, telephone, that sort of thing), nothing to do with umask.
> **currentshaft said:**
> Looks like the "chfn" command supports setting it via the "other" field - [https://manpages.ubuntu.com/manpages/focal/en/man1/chfn.1.html](https://manpages.ubuntu.com/manpages/focal/en/man1/chfn.1.html)
Thank you.
> **currentshaft said:**
> In my opinion, and this is not meant to be derogatory nor discourage anyone from hardening their system, I believe the user separation boundary on a Linux system is extremely trivial to cross, and while umask is a good hygiene practice, it is not a meaningful security control.
OK, thanks. Perhaps it's sufficient to set /home/[user] to user-access only.

I still think that the default shouldn't allow read-access to everyone, though.

---

### Post by #&amp;thj^% on 2024-06-24
If you wanted to try a short term first, and I do it on occasion:
```
umask -S
u=rwx,g=rx,o=rx

```
That's a normal return with umask default.
```
umask
0022

```
Remember short term here.
My change with:
```
[root@cachyos-zfs me]# umask 077
[root@cachyos-zfs me]# umask
0077

```
That was root permissions as seen above. (Only use if you what and why)
This for a normal session:
```
umask 077
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> umask && umask -S
0077
u=rwx,g=,o=

```

Maybe give it whirl first to test how it affects your system.

---

### Post by Paddy Landau on 2024-06-24
> **1fallen said:**
> If you wanted to try a short term first…
Thanks, @1fallen, but that doesn't work with GUI apps. I already set umask 077 in both ~/.bashrc and ~/.profile, so it's automatically set in the console and the terminal (for my user only, which is what I want). GUI apps don't see it unless you start the GUI from the terminal.

---

### Post by #&amp;thj^% on 2024-06-24
Understood and Respectfully,  I really should have read your first post. ;)

I don't know of a way to do this, and I'm pretty sure you don't really want to do it.

I know someone who experimented with locking down the default perms (as you're trying to do), then It changed their network settings, and some of the network settings files wound up unreadable and the network became unusable. You may not think of System Preferences as an app that creates files, but it is and it does.

Paddy are you joining MI6....:)

---

### Post by Paddy Landau on 2024-06-24
> **1fallen said:**
> I'm pretty sure you don't really want to do it…
I shall defer to your greater wisdom.
> **1fallen said:**
> Paddy are you joining MI6....:)
Ha ha! I am simply growing more paranoid these days. My ex-wife was just scammed (again), and I keep reading stories of people who fall prey to hackers, and it makes me think.

But, given what you and @currentshaft have said, it seems as though my efforts are a waste of time!

I'll leave it as is.

Thank you both for your input!

---

### Post by currentshaft on 2024-06-24
My top 5 infosec tips:
* Full disk encryption with LUKS
* Password manager (keepassxc is fantastic)
* Multi-factor authentication, preferably hardware-based, but at least through an app
* uBlock Origin in the browser and probably block third party cookies while you're at it
* Lock your credit and get your free report annually (for USPERS)

Doing these should keep you out of most trouble online and in general.

---

### Post by Paddy Landau on 2024-06-25
> **currentshaft said:**
> My top 5 infosec tips:
Nice ones.

[LIST]
[*]*Full disk encryption with LUKS* — Done
[*]*Password manager (keepassxc is fantastic)* — Done
[*]*Multi-factor authentication, preferably hardware-based, but at least through an app* — Done
[*]*uBlock Origin in the browser and probably block third party cookies while you're at it* — I use AdBlock Plus. I don't care about third-party cookies; but Chrome is set to disable them by default anyway.
[*]*Lock your credit and get your free report annually (for USPERS)* — That sounds like an American thing? I get automatic emails when my credit score changes significantly.
[/LIST]

---

### Post by #&amp;thj^% on 2024-06-25
Along with currfentshaft has written, and to add to the confusion....LOL
Paddy I also put umask in "/etc/profile" and my results are:
```
# '/home/me/umask.sh' 
nobody    This account is currently not available.
systemd-coredumpThis account is currently not available.
systemd-networkThis account is currently not available.
systemd-oomThis account is currently not available.
systemd-journal-remoteThis account is currently not available.
systemd-resolveThis account is currently not available.
systemd-timesyncThis account is currently not available.
tss       This account is currently not available.
_talkd    This account is currently not available.
avahi     This account is currently not available.
colord    This account is currently not available.
dnsmasq   This account is currently not available.
geoclue   This account is currently not available.
git       lightdm   This account is currently not available.
nm-openvpnThis account is currently not available.
openvpn   This account is currently not available.
me        0077
flatpak   This account is currently not available.
fwupd     This account is currently not available.
passim    This account is currently not available.
libvirt-qemuThis account is currently not available.
qemu      This account is currently not available.

```

So unless your playing with some bad actors or a bad site you should be safe enough.

---

### Post by Paddy Landau on 2024-06-25
> **1fallen said:**
> I also put umask in "/etc/profile" …
I haven't touched [FONT=courier new]/etc/profile[/FONT]. I've only put it in [FONT=courier new]~/.profile[/FONT] and [FONT=courier new]~/.bashrc[/FONT].

Anyway, you all have very much put my mind at ease, thank you. I'll stop messing with umask.

---

### Post by TheFu on 2024-06-26
> **currentshaft said:**
>  
In my opinion, and this is not meant to be derogatory nor discourage anyone from hardening their system, I believe the user separation boundary on a Linux system is extremely trivial to cross, and while umask is a good hygiene practice, it is not a meaningful security control.

It depends on the attacker.  Most attackers are NOT very sophisticated.  IF they are, there's little that can be done, beyond having multiple layers of security. We will disagree on this, based on our different experiences.  I only have 30 yrs of experience, so there are certainly other views on this topic.

I would never suggest anyone alter the default setting system-wide. That's a good way to break things.  Changes like this need to be limited to single users.

The default HOME directory setup is [FONT=Courier New]drwxr-x---[/FONT] for 22.04 and later releases.  The umask is still 002, but since the HOME directory doesn't allow "other" any access, it generally doesn't matter. Other cannot get into the HOME for users, unless the user modifies the permissions.

---

### Post by currentshaft on 2024-06-26
> **TheFu said:**
> It depends on the attacker.  Most attackers are NOT very sophisticated.

This attack doesn't require sophistication.

alias sudo="evil; sudo -S" >> .bashrc

Now all the attacker has to do is wait for the user to enter their password once to impersonate them, and likely escalate to root on almost all hosts.

Multi-user and "root" security on Linux are kind of a joke. Once an adversary has code execution on your box, that's it, it's game over, no amount of umasks, anti-virus program or firewalls is going to help.

That's why critical workloads need proper isolation, virtualization and containers to make security guarantees.

---

### Post by #&amp;thj^% on 2024-06-26
Pardon my 2 cents worth here, is this a good place to be speaking about Linux Security as a whole?

"Linux" (as some aggregate of all the installations) typically has quite a bit more than just a password denying external access.

So even if a running service is compromised (an HTTP server, for instance), if it is itself not running under the highest privileges, it is limited in the amount of lasting damage it can do. This mindset of running under limited privileges is what makes it a more secure system. (But Not Bullet Proof)

There is no secure system. There are only systems which might be sufficiently secure against specific kind of attacks, and attack scenarios might change fast.

No magic Pill just the user's knowledge on security. You still have to know what you're doing and keep everything up-to-date.


And I agree with TheFu " never suggest anyone alter the default setting system-wide" unless they know why or how. (As warned possible breakage)

---

### Post by TheFu on 2024-06-26
> **currentshaft said:**
> alias sudo="evil; sudo -S" >> .bashrc

Tricking a user into running somethings evil is an issue on every OS and has been since the first computers existed.  It is nothing new.

There's no replacement for a smart user who cannot be tricked.  You can create an alias for your user, but not for mine.  If you can trick me into running a script that you wrote, then I deserve what I get.

I'd believe more strongly that someone would infect most users through a USB device with an auto-type script built into the "load driver" function.  The truly paranoid already know that everyone in the world is out to get them ... not personally, but everyone they can.  There's a huge ecosystem in most Linux distros to prevent untrusted software from getting installed.  This isn't MS-Windows with a setup.exe that people are expected to run.  If users only get software from a trusted distro repo, stay updated, and on a supported OS, they've just prevented many of these foolish attack vectors.

But you'll have some other example of how a little mistake can cause take over of a Linux system. That's true. Nothing replaces a smart admin.

Which comes back to my statement ... 
> I would never suggest anyone alter the default setting system-wide. That's a good way to break things. Changes like this need to be limited to single users.

---

### Post by currentshaft on 2024-06-26
> **1fallen said:**
> So even if a running service is compromised (an HTTP server, for instance), if it is itself not running under the highest privileges, it is limited in the amount of lasting damage it can do.

The history of software vulnerabilities is replete with examples counter to this.

Search for "local privilege escalation linux cves"

[https://ubuntu.com/security/CVE-2024-1086](https://ubuntu.com/security/CVE-2024-1086) is just one recent example

Just assume any code you run on Linux has the capability to be become root.

---

### Post by currentshaft on 2024-06-26
> **TheFu said:**
> Tricking a user into running somethings evil is an issue on every OS and has been since the first computers existed.  It is nothing new.

There's no replacement for a smart user who cannot be tricked.  You can create an alias for your user, but not for mine.  If you can trick me into running a script that you wrote, then I deserve what I get.

My friend, there is no trickery involved, nor another user. The code you run as your user already grants adversaries the potential privilege to do what I had demonstrated. Do you audit every line of every application, script and web site you execute and visit? I highly doubt it, and even if you did, much of modern software is hilariously vulnerable to common exploits.

There are weekly examples of remote code execution in browsers, mail clients and media software. Many of them require no user interaction, simply visiting a webpage or receiving an email is enough for an attacker to execute code (as you). After than, root escalation is a walk in the park.

Bottom line is friends don't let friends run critical workloads without virtualization or containers, or other means of isolation/sandboxing.

---

### Post by TheFu on 2024-07-02
> Bottom line is friends don't let friends run critical workloads without virtualization or containers, or other means of isolation/sandboxing. 
Agree.

If you are running "critical workloads" on a desktop install, you deserve what you get.

If you allow your browser to run code from other people outside some sort of constraint system, outside display-only tags, I think you are fool.  Most of the world doesn't know any better.  We do.

Friends shouldn't allow other friends to run their browsers in a careless way.
Friends shouldn't allow other friends to run their fat email clients in a careless way.
Friends shouldn't allow other friends to use cloudy services, unless they completely understand the privacy they are giving up.
> Cloud computing is careless computing.
 - RMS  [https://www.theguardian.com/technology/2008/sep/29/cloud.computing.richard.stallman](https://www.theguardian.com/technology/2008/sep/29/cloud.computing.richard.stallman)

and
> The concept of using web-based programs like Google's Gmail is "worse than stupidity", according to a leading advocate of free software.

People who allow others to run code on their local machines aren't too bright.  Allowing webRTC or javascript to run inside a browser from untrusted servers is pretty stupid.  If they can't gain local access, then they can't use a local escalation.  Seems pretty obvious.  Sadly, many new admins think that just because something works, their job is done.  Hardly.

---

