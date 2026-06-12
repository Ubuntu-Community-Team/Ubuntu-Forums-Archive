---
title: "Simple Home File Server-need help please"
date: 2008-03-02
forum: General Help
---

### Post by wolfwatcher51 on 2008-03-02
I am trying to take an old computer and make a "Simple Home File Server" out of it using the Howto Forge.com tutorial.

I was doing pretty good until top of page 3.

It says to run sudo passvd root and give it a password. I typed sudo passvd root at the chris@server1tilde)$ prompt. It came back with [sudo] password for chris: I typed my password for new user password that we established earlier in the install. It came back with sudo: passvd: command not found. I guess I was supposed to enter a new, different, password? Now when I entersudo passvd root, it keeps coming back with sudo: passvd: command not found and not letting me try again to put in a password.

Please help, what do I do now? Thanks in advance, Chris.

---

### Post by SpaceTeddy on 2008-03-02
i think the command you are looking for is "sudo pass**w**d root" which would set the root password for your root account. This (on an ubuntu computer) will also disable the ability for normal users to run commands as root with their own password (afaik).

---

### Post by wolfwatcher51 on 2008-03-02
Thank you for the reply and you are absolutely correct, it is a w not a v. Gotta love us noobies who do not know what we are doing and just trying to follow instructions.

I figured it out as I was shutting down for the night, the screen capture in the tutorial looked like a v.

Have you seen the tutorial I am trying to follow, by chance? I am down to 5 "Configure the network".
I cannot get the command to give me the information he shows. Maybe part 5 does not follow after what you did in part4? Am I supposed to go back (how?) to another level to do part 5?

Sorry, I do not know how to put a link in here, but it is [www.howtoforge.com/ubuntu-home-fileserver](www.howtoforge.com/ubuntu-home-fileserver). I am up to page three. Any help would be greatly appreciated. I guess that because I am using the server version there is no GUI? Thanks in advance, Chris.

---

### Post by SpaceTeddy on 2008-03-03
capter 5 looks right for a static ip configuration for your server - only thing i don't like is that the root password get set, but that is just flavor and does not really matter. there is nothing there that should prohibit you from editing the network configuration.

if you could specifiy where you troubles are (i.e. which command) i can help you, but in general the tutorial looks fine and should work.

---

