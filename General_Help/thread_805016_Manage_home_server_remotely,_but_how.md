---
title: "Manage home server remotely, but how?"
date: 2008-05-23
forum: General Help
---

### Post by FilmAficionado on 2008-05-23
Hello, just some quick questions. I've been googling and alas the only "solution" I've found, though I'm not even sure if it's the right one, is to install sshfs on my laptop in order to somewhat remote manage my home server over ssh and the open internet.

BTW, it's not server edition, just regular Ubuntu installed on a tower pc that I want to manage like a server when I'm away from home...

What I want to do: login using my laptop from another state/isp and ssh into my homeserver and manage it as if I were sitting right in front of it (not looking to do VNC because the performance is horrid, huge lags with Heron's remote desktop viewer). I'd like something command line.

I have so many semi-random questions so I apologize in advance:

[I]1. I can wakeonlan my server from the net. I figured that out. But how does one "confirm" when he is hundreds of miles away from home that it worked; is there a way to see the boot process or just something to assure me that it is starting up?

2. When I ssh from my laptop to my home server: my router at home is set to use dyndns to keep our dynamic ip updated and thus keep a specific port open so I can use wakeonlan from the open internet to find and start my home server:

Is using dyndns creating a security hole or anything for when I use ssh? Can someone sniff my data or see what I'm doing since I'm going through them? Basically my ssh or scp commands look like this with the actual username.dyndns.org URL in them (thanks for the help on this last night): ```
scp sysadmin@username.dyndns.org:~/Desktop/oc.mov Desktop/oc.mov
```

3. Last night you guys helped me figure out how to use scp and it's awesome. But what if I want to stream whole folders full of music or send backups of files back and forth? Can I do it securely on someone elses wifi, in a coffee shop, etc?

4. A question on ssh in general: I don't remember seeing any options as to "how secure" it is; as in what kind of encryption is used, how many bits, and what should I be aware of? Is it safe to transfer private/important data from my home server to my laptop across the open internet that way (especially since I use dyndns as the intermediary?).

5. If I do use vnc, are there any clients better than the remote desktop viewer included in Heron? I use the password option but it seems almost trivial? Does it ssh tunnel too? Is it safe? There's a lot of lag.

6. Can anyone point me to some good tuts or sites for remote management and creating some cool, server-oriented stuff. I have a feeling there's not much out there for noobs since it's probably not the most user-friendly or popular route... But I'm learning and this is quite fun.
[/I]
If a few of you could take stabs at one or two questions each, and point me in the right direction, I'd really appreciate the guidance!

Thanks in advance,

---

