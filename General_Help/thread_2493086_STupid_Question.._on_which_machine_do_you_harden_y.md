---
title: "STupid Question.. on which machine do you harden your ssh config file?"
date: 2023-12-03
forum: General Help
---

### Post by blahboybaz on 2023-12-03
So I have my laptop that is physically in my hands and there is some "remote" machine I want to connect to. If I harden the ssh config file on my laptop then it effects any machine that would connect to my laptop right? In this example it is the machine connecting to my laptop that is called the "client" right? just using that as an example. Conversely, if I want to connect to a remote machine using my laptop and I want to harden that connection then it is the remote machine's ssh config that I would alter right? And in that example it is my laptop that would be considered the "client"?

Thanks for any help clearing these things up.

---

### Post by TheFu on 2023-12-03
Both.

On the client-side, there is little that can be done, but not being stupid, not using passwords for authentication and not using out of date crypto ... like RSA ... would be a good start.

On the server-side, much more can and should be setup to protect from nefarious inbound connections. There are lots of webpages which outline different steps, depending on your skill and perceived risks.  The most important setting is to block passwords as possible authentication and only allow ssh-keys or ssh-certs for that role.  Automatically blocking brute force attacks would be smart too, obviously.

---

### Post by blahboybaz on 2023-12-03
> **TheFu said:**
> Both.

On the client-side.. On the server-side


Thanks but its kind of not what I was asking. I'm trying to be certain on which machine in a connection is considered the "client" and which is considered the "server". The word "remote" I understand because it does not have multiple meanings the way the word server does (it just causes confusion).

Also I'm trying to understand which machine's configuration file effects the connection. I can look up the specifics of configuring/hardening the ssh config file and am even familiar with doing that. It's isolating which machine does what and is responsible for what in a situation where you have 2 machines involved.

Would it be accurate to say that the machine that holds the private key in a connection is the one responsible for regulating the connection with machines connecting to it?

I just keep seeing the same language everywhere I look and it isn't helping. That's why I'm trying to word things in a way I can understand but ask for help to make sure if it's right or wrong.

Thanks

---

### Post by TheFu on 2023-12-03
> **blahboybaz said:**
> Thanks but its kind of not what I was asking. I'm trying to be certain on which machine in a connection is considered the "client" and which is considered the "server". The word "remote" I understand because it does not have multiple meanings the way the word server does (it just causes confusion).


The system that is "listening" for new ssh connections is the server.  Typically, that would be a remote machine, but it doesn't need to be that way. There are examples where the remote system is the client and the local system is the server.  X/Windows would be an example of that.  The X/Server runs on the machine we sit at and the X/Clients are all remote systems.  But ... the way that X/Windows works is backwards from the way that nearly all client/server systems work.

> **blahboybaz said:**
> 
Also I'm trying to understand which machine's configuration file effects the connection. I can look up the specifics of configuring/hardening the ssh config file and am even familiar with doing that. It's isolating which machine does what and is responsible for what in a situation where you have 2 machines involved.

There are a client config files (/etc/ssh/ssh_config and/or ~/.ssh/config)  and there is a server config file (/etc/ssh/sshd_config).  The manpages for each have the options, some are related to security.  Both the client config and the server config can drastically impact ssh security.  It isn't a 1 or the other question. Sorry.

> **blahboybaz said:**
> Would it be accurate to say that the machine that holds the private key in a connection is the one responsible for regulating the connection with machines connecting to it?
No. It would not, but that depends on your definition of "regulating".  The client system has the private key and the server system would have the matching public key, assuming ssh-keys are used for authentication. There are also server keys which are used to ensure the client and server "know" each other. How strongly this server-to-server validation is mandated is configured in the ssh server sshd_config file.

It is easy to confuse the term "server", since we use it for software and hardware, and for the opposite system that the client connects with (which could also be a peer system). The terminology isn't 100% clear.  At least it isn't as bad as "domain" which has 10 meanings, at least.

---

### Post by The Cog on 2023-12-03
TheFu is dead right, but I'll say the same thing in different terms.
Assume the "client" is me sitting at my laptop, and the "server" is my raspberry pi recording greenhouse temperature and the pi needs some config change. The client is the one that initiates the ssh connection - me at my laptop. The pi is the server, with sshd (ssh daemon) listening for incoming calls. When my client connects to the server, the server tries to authenticate/authorise me. It may demand a username+password, or if the pi is configured to accept my public key as proof of ID then it just accepts the connection. My pi is hardened in that it is configured not to ask username+password, but only accept keys.

The ssh client also checks the server key is one that you have already approved. The first time you connect it doesn't recognise the server's key, and asks if you really want to connect. You **should** check the reported fingerprint by some means other than the internet (telephone, written letter etc.) to make sure you are talking to the real server and not a fake. Most people just say yes because checking is a nuisance, but there are environments where not checking first is a disciplinary offence. Having been told to trust it, the ssh client records the fingerprint and checks it on every subsequent connection. Further hardening here may be to configure the client so it doesn't ask if you accept the unknown fingerprint but simply refuses to connect at all, in which case you have to manually configure the fingerprint into the list of known hosts. This is more inconvenience, but more secure.

When I type **[FONT=Courier New]ssh pi@pi400[/FONT]** on my laptop, it just connects with no fuss or questions. But I know that they have just exchanged and verified each other's keys so I'm talking to the real pi, and nobody else in the world could connect to it (except my desktop which the pi also accepts).

---

### Post by blahboybaz on 2023-12-04
Ok I'm sure I've got it. Apologies for not giving a more specific example / question but I don't think I knew how until reading these responses. Please forgive if I'm in error with my following specific example. I'd like to be sure I'm on target with my understanding of what has been said so far.

If I want to connect to some remote machine using my local machine then my local machine is the client and the remote machine is the server. Now suppose I also am authorized to do whatever I want on the remote machine (maybe I own it too or something). Further suppose we are using openssh on both machines and rsa keys. If I want to deny password login then it is the /etc/ssh/ssh_config file that is on the server (the machine I want to connect TO) that I need to make the change in? Because it is the machine being connected to and it's configuration files that regulate the incoming connection from clients? Conversely, if some remote machine were to attempt to connect to my local machine (suppose for the sake of the example that I allow that) and I want to deny password login then it is the /etc/ssh/ssh_config file on my LOCAL machine (now in this context considered the "server") that I would make the change to - because it is the server that regulates the connection coming in from clients attempting to connect to it?

I hope I got that right.

---

### Post by The Cog on 2023-12-04
> If I want to connect to some remote machine using my local machine then my local machine is the client and the remote machine is the server.  Yes.
> If I want to deny password login then it is the /etc/ssh/ssh_config file that is on the server (the machine I want to connect TO) that I need to make the change in?
No, it's the /etc/sshd_config on the (remote) server that you need to change. sshd is the daemon that listens for incoming calls. Set **PasswordAuthentication** to **no**.
> Conversely, if some remote machine were to attempt to connect to my local machine...
Then it's /etc/sshd_config on your local machine that you would have to edit. You would have to install openssh-server first, to get your local machine listening for incoming calls. But you probably don't have it installed on your local machine, it's not installed by default.  And think about your firewall rules.

---

### Post by TheFu on 2023-12-04
I see the confusion. So does The Cog.  I had a similar confusion a few decades ago, so I like to think it isn't unusual.

/etc/sshd_config = server settings

/etc/ssh_config = client settings, but those are base client settings only.  Use the ~/.ssh/config file for individual user ssh client settings.

Client-side settings have no control over whether an ssh server will or will not accept passwords.

The normal way to remember config files for servers is that a "server" usually runs a daemon .... "d" and the both the name of the server program and the server config will have a "d" at the end.
sshd = ssh server daemon.
ssh = ssh client program.

There are lots of other examples that work that way.  chrony**d** and chronyc.  The c is helpful, but not always (or even usually) there.
atd, cupsd, virtlogd, rpc.statd, rsyslogd, saned, thermald, plymouthd, libvirtd, pppd, update-inetd,   The 'd' at the end of all those is for "daemon" ... i.e. a server.  Sometimes you'll see it spelled "dæmon".

What is a dæmon process? [https://en.wikipedia.org/wiki/Daemon_(computing)](https://en.wikipedia.org/wiki/Daemon_(computing))    Basically, it is a server.

---

### Post by dragonfly41 on 2023-12-04
My thoughts from following this discussion and other like discussions of clarification of terms .. we could perhaps all benefit from a Ubuntu (or Linux?) ontology of terms. There are ontologies in other vertical domains .. but I could not find one for Ubuntu.

---

### Post by TheFu on 2023-12-04
> **dragonfly41 said:**
> My thoughts from following this discussion and other like discussions of clarification of terms .. we could perhaps all benefit from a Ubuntu (or Linux?) ontology of terms. There are ontologies in other vertical domains .. but I could not find one for Ubuntu.

Ubuntu isn't that different from Linux to warrant a separate document.  
90% of Unix is the same as Linux for end-users (not admins), so just find what you seek for Unix and Linux in general.  
That would get most people 95% of the things they need .... and wikipedia has most of those terms explained already.

There's no way to keep up with all the "Canonical-isms" that show up weekly thanks to marketing trying to give things a marketing name.

I would be good if someone put those 3 jargon dictionaries in a list that could be referenced, but since we all come from different backgrounds, what completely makes sense for 1 person doesn't usually translate usefully to others.  A 1500 page book of jargon isn't exactly helpful.

Every industry does this and every company does it too.  For the first 3-12 months, it is helpful, but after that, you've probably learned the jargon you need to know for your job - or been fired.

---

### Post by dragonfly41 on 2023-12-04
> [COLOR=#000000]There's no way to keep up with all the "Canonical-isms" that show up weekly thanks to marketing trying to give things a marketing name.[/COLOR][COLOR=#000000]

Actually that is quite feasible and uses the same learning methods as the current wave of AI tools.

If a Canonicalism is introduced it is picked up. Every online document needs to be thrown into a giant mill and words (strings, tokens) pop out like a coffee bean grinder. I worked on that more than 20 years ago but today we have the modern Chat-GPT.

If I have time (not right now) I might knock together a proof of concept experiment. Just needs scraping of Canonicalisms buried deep in URL's.
[/COLOR]

---

### Post by TheFu on 2023-12-04
I still see AI "hallucinating" far too much to be trusted.

---

### Post by dragonfly41 on 2023-12-04
Well I've kicked off my engine. Will explore findings.

---

### Post by blahboybaz on 2023-12-04
@The Cog
@TheFu

That's really wonderful. Thanks for bearing with me while I learned.

---

