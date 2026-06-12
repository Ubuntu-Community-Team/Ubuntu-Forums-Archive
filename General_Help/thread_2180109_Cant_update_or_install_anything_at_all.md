---
title: "Cant update or install anything at all"
date: 2013-10-11
forum: General Help
---

### Post by Tristan_Williams on 2013-10-11
I have posted this in the ubuntu studio section but i thought maybe id find more assistance here. 
The thread i posted in the ubuntu studio section is [http://ubuntuforums.org/showthread.php?t=2179758](http://ubuntuforums.org/showthread.php?t=2179758)

Basically my problem is I cant install or update anything at all.

When I run "sudo apt-get update" i get this:
```

tristan401@tristan401-Vostro-220-Series:~$ sudo apt-get update
[sudo] password for tristan401: 
Err http://extras.ubuntu.com raring Release.gpg                     
  Connection failed
Err http://us.archive.ubuntu.com raring Release.gpg                 
  Connection failed
0% [Waiting for headers] [Waiting for headers] [Waiting for headers]

```

And when i try to ping any of the software sources:
```

tristan401@tristan401-Vostro-220-Series:~$ ping http://archive.canonical.com/ubuntu
ping: unknown host http://archive.canonical.com/ubuntu
tristan401@tristan401-Vostro-220-Series:~$ 

```

On a related note, when i try to ping [http://www.google.com](http://www.google.com), i get the same error message.
But when i ping google.com, or even [www.google.com]("http://www.google.com"), It works perfectly... 


I have re-written the sources.list file to the origional contents, and have disabled all PPA's (also tried re-enabling them)

I also find it weird how update manager works perfectly fine, that is, when it manages to find any updates (it has stopped finding updates for the time being)

I have tried selecting a different mirror... Didn't work.
I tried using the "Select best server"... Didn't work

Basically i have brought it down to:
1) Proxy issue
2) Error in sources.list 
3) Satan
(feel free to add to the list)

Please help. I need certain software for projects that are my only income :(



EDIT:

I can update from update manager... but nothing else

---

### Post by L486XGW on 2013-10-11
You cannot use ping to ping urls it is only for hosts. The problem is more than likely a firewall issue, but possibly could be a dns issue too.

Can you do:

```

ping [COLOR=#000000][FONT=Ubuntu Mono]us.archive.ubuntu.com

```

if it resolves then its not a dns issue and is a firewall blocking the port you are trying to connect to.[/FONT][/COLOR]

---

### Post by Tristan_Williams on 2013-10-11
ping [COLOR=#000000][FONT=Ubuntu Mono]us.archive.ubuntu.com[/FONT][/COLOR] worked. So how do i go about disabling whatever firewall is causing this? I haven't (knowingly) installed or activated any firewalls

Edit:

I have tried the following:

```

sudo iptables -F

```
  and...
```

sudo ufw disable

```

Neither of which did any good.

---

### Post by L486XGW on 2013-10-11
Are you on a network that requires authentication to a proxy server or something? Can you open [COLOR=#000000][FONT=Ubuntu Mono]http://extras.ubuntu.com in a web browser?[/FONT][/COLOR]

---

### Post by Tristan_Williams on 2013-10-11
> Are you on a network that requires authentication to a proxy server or something?
No, i am on a private network. The only authentication that is required anywhere on my system is sudo privileges.

> Can you open [COLOR=#000000][FONT=Ubuntu Mono]http://extras.ubuntu.com in a web browser?[/FONT][/COLOR]
Yes, i can open it and browse through it with absolutely no issues. 

The problem lies somewhere within Synaptic and apt-get. 
Software center and Update Manager seem to work fine. (a few kinks, but they work, unlike synaptic and apt-get)

---

