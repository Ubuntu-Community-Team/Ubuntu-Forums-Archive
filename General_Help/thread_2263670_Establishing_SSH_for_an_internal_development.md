---
title: "Establishing SSH for an internal development"
date: 2015-02-02
forum: General Help
---

### Post by Matthew_Harrop on 2015-02-02
A few days ago a friend asked me to establish an development server (With GIT and SSH connection protocol) for a company he wants to start. 

While setting it up, I followed the following steps:

1. Downloaded Ubuntu Server 14.04
2. Connected it to my BT Home hub 
3. Downloaded all the appropriate updates and software.
4. I followed the guide on the Ubuntu website to set up the SSH server and client. - I was using password authentication, but did generate the RSA keys in anticipation of roll out to his development team

At this point everything was working fine. I was able to connect to the server from my Mac perfectly fine, run commands and treat it as an extended terminal (As you would expect)

At this point I shut the server down and went to bed.

Now, when I turn the server on again the next morning I find i am unable to connect and receive the message "Write failed: Broken pipe" 
I do some googling and find some fixes and try them out (Even some on this forum). They do nothing except close port 22, to the point now that when using "ssh user@localhost" on the server it even returns a "Connection Denied on port 22"

I am now so totally lost. I've removed and re-installed openssh-server, replaced the settings with the backup copy, but to no avail. I have no idea why, whats changed over night or what I've done wrong. 

Does anybody have any clue what might have happened and a guide to explaining openssh-server, its options and how to configure it? I am so totally lost :(

---

### Post by Lars Noodén on 2015-02-02
Normally it works fine out of the box.  Here are three things to check on the server itself.  

Is it running?

```

service ssh status 

```

What port is it really listening on?

```

sudo  netstat -ntlp | grep sshd

```

Is the firewall doing anything special in regards to that port?  It should allow that port in.

```

sudo ufw status verbose

```

---

### Post by Matthew_Harrop on 2015-02-03
Thank you for you reply!

The responses I got are:

> ssh status/running

I didn't get any response for the second command... :/

However running just netstat reveals i have no open tcp ports, and the only protocol currently running is Unix...

For the ufw command i received:

> 
To                            Action         From
--                            --------        --------
20                           Allow In      Anywhere
20/tcp                     Allow In      Anywhere
22                           Allow In      Anywhere
22/tcp                     Allow In      Anywhere
20(v6)                     Allow In      Anywhere (v6)
20/tcp (v6)              Allow In      Anywhere (v6)
22 (v6)                    Allow In      Anywhere (v6)
22/tcp (v6)               Allow In      Anywhere (v6)





EDIT: I've investigated some of your suggestions and carried out some more configuring (Specifically on ufw)

---

### Post by Lars Noodén on 2015-02-03
> **Matthew_Harrop said:**
> I didn't get any response for the second command... :/

Hmm.  That means that in spite of what upstart says, [sshd](http://manpages.ubuntu.com/manpages/trusty/en/man8/sshd.8.html) is really not running.  Perhaps there is an error in the configuration file?  You could try running the SSH server manually in debug mode to see if it gives any warnings or errors.

```

sudo /usr/sbin/sshd -d

```

If the configuration file loads, then it will allow you to connect once and then exits.

---

### Post by Matthew_Harrop on 2015-02-03
It informed me that I had problems with my /etc/ssh/sshd_config file, Which i rectified by uninstalling all ssh related components and reinstalling them all (Again) That seems to have fixed the problem, although i am perplexed as to why it went wrong in the first place...

Thank you very much for your help, I wouldn't have been able to fix it without your help.

On a side note - Your signature links to the wikibooks article about ssh, did you write it?

---

### Post by Lars Noodén on 2015-02-03
No worries.  I'm glad it's working.  It's always good to make backup copies of the last-known-working configuration files before editing, if that's what might have happened.  Be sure to have strong passwords or, better, use keys because as soon as you put it on the net, people's bots will start testing it.  

About the wikibook, yes, some years back I noticed that I had so many notes on having used OpenSSH at work that I figured I could put them together as a cookbook.  The initial wikibook was rather meager, not having the technical reviewers that the print publishing process has.  But then I took a second pass at it and then fleshed it out.  A few people have helped with some corrections and one suggested a method.  It's still missing stuff about certificates though, as I know little about them.  There are some changes for 6.8 that I plan to add when the time comes, but if you notice something that needs changing or adding, feel free to edit it or let me know.

---

### Post by Matthew_Harrop on 2015-02-03
Well, I wanted to thank you really! 
It was a great help and its not often you get to thank the author of a book.

What do you mean by one contributor suggested a method? Like a basic method of installing and configuring openSSH server?

---

### Post by Lars Noodén on 2015-02-04
Glad it helped.  

They suggested a method for one of the cookbook sections about using it as a SOCKS proxy via an intermediate host, which needed only a little editing.  
[https://en.wikibooks.org/w/index.php?title=OpenSSH/Cookbook/Proxies_and_Jump_Hosts&stableid=2756453#SOCKS_proxy_via_an_Intermediate_Host](https://en.wikibooks.org/w/index.php?title=OpenSSH/Cookbook/Proxies_and_Jump_Hosts&stableid=2756453#SOCKS_proxy_via_an_Intermediate_Host)

I suppose the fact that the method can be chained could be mentioned there too, if it's not obvious.  I'll have to think on that.

---

