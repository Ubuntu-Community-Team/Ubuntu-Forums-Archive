---
title: "Protecting BIOS and Root On Ubuntu"
date: 2008-05-11
forum: General Help
---

### Post by OrcaWave on 2008-05-11
Pretty soon (as any day now) I'm gonna order a 'Wild Dog' box from 'System 76'.

Can anyone here tell me the very best and the most *secure* way to protect the BIOS and the Root of the machine?

It will have Hardy Heron on it.

I know that you can password protect both the BIOS and the Root, but is there something more secure than password protecting these?

And I've heard that Ubuntu leaves the Root of the OS open to where anyone can get to it (hack into it), is this true?

And if it is, how can one "lock up" both the BIOS and the Root of a Ubuntu machine and try to make the box as impenetrable as possible?

Thanks a lot for your help!

Orca Wave

---

### Post by aysiu on 2008-05-11
If your computer is stolen, it's compromised no matter how many passwords you put in. You can make the compromise a little slower or more inconvenient, but you can't prevent it if someone has physical access to your computer, malicious intent, and a little know-how.

---

### Post by OrcaWave on 2008-05-11
Well, I'm NOT worried about someone stealing it in a physical way, but someone hacking into either the BIOS or the Root of the machine.

Understand what I mean?


Thanks, Orca Wave

---

### Post by aysiu on 2008-05-11
So a friend or relative walking up to the machine and wanting to mess around with your stuff, you mean?

---

### Post by OrcaWave on 2008-05-11
Dear Aysiu,

  Yes, the only person who will have *physical access* to my machine is my wife, and even she won't want to use it, as she has a Windows (ughhh!) machine.

I'm worried that a hacker/cracker will hi-hack the machine's BIOS as happened once before to an older machine.

He installed an 'adminstrator controller' thing on it, and a keylogger.....THAT'S what I'm trying to prevent again.

I've read that Ubuntu's Root is easy for a hacker to get into, I'm not sure if this is true or not, though.

I'm a newbie when it comes to Ubuntu OS.

Thanks, Orca Wave

---

### Post by p_quarles on 2008-05-11
It's easy to get into the BIOS or single-user mode on any machine -- if you have physical access. If you don't, then you would need to find way of exploiting it remotely, which is entirely a software issue. If this is something that worries you, be sure to keep up with security updates. 

BIOS exploits have nothing to do with the operating system you are using. If it were possible to exploit the BIOS on your machine, it would be completely irrelevant which OS you happened to have installed on top of it.

---

### Post by Tatty on 2008-05-11
> **OrcaWave said:**
> And I've heard that Ubuntu leaves the Root of the OS open to where anyone can get to it (hack into it), is this true?

Not quite, the root account is disabled by default in a ubuntu system, so it is not possible to log on as root unless you deliberately enable root - but doing so is generally seen as bad practice in ubuntu and is not recommended.

You should read the community wiki page on this for more information [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by p_quarles on 2008-05-11
> **Tatty said:**
> Not quite, the root account is disabled by default in a ubuntu system, so it is not possible to log on as root (except for when booting into recovery mode).
This is a common misconception. What is disabled is the root password, not the account. This means that the initial login cannot be the root account, but it is quite easy to login as root from a sudoer account.

---

### Post by OrcaWave on 2008-05-12
> **p_quarles said:**
> This is a common misconception. What is disabled is the root password, not the account. This means that the initial login cannot be the root account, but it is quite easy to login as root from a sudoer account.


So, can anyone tell me just how a sudoer account works?

And if it can be a "backdoor", just how do I shut it down, or lock it up?

Thanks for your help,  Orca Wave

---

### Post by p_quarles on 2008-05-12
> **OrcaWave said:**
> So, can anyone tell me just how a sudoer account works?
The privileges granted by the "sudo" command are defined in the /etc/sudoers file. In a default Ubuntu setup, the first user created can use sudo to run any command as root. This includes, naturally, the ability to log into a root shell. Users created subsequently do not have any sudo privileges.

> And if it can be a "backdoor", just how do I shut it down, or lock it up?
There are two ways to exploit any computer: with physical access and with remote access. 

For physical access, there is no way to prevent users from gaining root access to the machine. The only thing you can do is encrypt the filesystem so that they can't access your data. 

Remote exploits are considerably more difficult. Generally speaking, they are highly unlikely unless you are running server software of some kind, and have it opened up to the world. Aside from those, the biggest threats are your networking applications, such as Firefox. Stay aware and up-to-date on phishing scams, DNS poisoning attacks and Javascript exploits. 

I am unaware of any stories involving Linux desktop users falling victim to attacks against their web browsers, but that doesn't mean it can't happen. The internet is a pretty inherently dangerous place, so being cautious about the kinds of code you let unknown sites run on your machine should be second nature. If you follow that guideline, the chances of your machine getting exploited are very minimal. 

Anyone telling you that a certain procedure or trick will make your system 100% secure, however, is either lying of uninformed.

Thanks for your help,  Orca Wave[/QUOTE]

---

### Post by 3rdalbum on 2008-05-12
If possible, set a BIOS password that prevents altering configuration of the BIOS unless you type in the password. Then set a password on GRUB, so it can only boot into your default kernel setting unless you type your password.

Also, set up drive encryption.

You'll be fairly safe then, I hope.

---

