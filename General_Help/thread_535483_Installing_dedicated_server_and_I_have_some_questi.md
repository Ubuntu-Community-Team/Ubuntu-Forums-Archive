---
title: "Installing dedicated server and I have some questions"
date: 2007-08-26
forum: General Help
---

### Post by kentl on 2007-08-26
Hi!

I'm not new to Linux, but I am by no means experienced yet. However I do like learning and have my goal set.

I've built a PC which I intend to have running as a dedicated server which will:
[LIST]
[*]Serve my homepage using Apache+PHP5+MySQL
[*]Act as an Subversion and Darcs repository
[*]Act as an SFTP file-server
[*]Download selected torrents by filtering an RSS-feed
[/LIST]

I have:
[LIST]
[*]Decided to use Ubuntu Server 7.04
[*]Built the computer
[/LIST]

What I'm thinking about and here's where I would like your comments and suggestions:
[LIST]
[*]I've got no experience configuring software firewalls on Linux. What options are there? Is it recommended that I use one? Got any nice tutorial links on how to use <firewall-you-recommend>?
[*]I plan to only communicate with this server by LAN and thus have no monitor, mouse or keyboard attached. Which method should I use for remote control? Is said method secure by default or do I have to do something?
[*]Should I use the option to install a LAMP-server when installing the server? Or should I do it manually myself? What nice and bad side effects do you see in these two paths? Is the security level of the LAMP-server installation good enough?
[/LIST]

Thanks for reading my post. If you have any comments or suggestions I'd be happy to hear them! :)

---

### Post by kidders on 2007-08-28
Hi there,

> **kentl said:**
> I've got no experience configuring software firewalls on Linux. What options are there?The Linux firewall is called iptables. Strictly speaking, a firewall is probably not necessary, but most people don't feel comfortable *not* running one. If your network doesn't have a firewall, I suggest using iptables to protect it.

> **kentl said:**
> I plan to only communicate with this server by LAN and thus have no monitor, mouse or keyboard attached. Which method should I use for remote control? Is said method secure by default or do I have to do something?Use SSH.

> **kentl said:**
> Should I use the option to install a LAMP-server when installing the server? Or should I do it manually myself?I can't imagine why doing either would give you significantly different results ... after all, you'll probably want to reconfigure anything Ubuntu sets up anyway.

---

### Post by kentl on 2007-08-28
Thanks! I've got my server installed with OpenSSH, which I am trying to secure. After that I'll look at securing the LAMP-part.

---

### Post by kidders on 2007-08-29
How much punishment will your server have to stand up to?

---

### Post by kentl on 2007-08-29
I don't know. :-) I just like to make it pretty secure as it will be public and always turned on. I'll have my homepage on it and one of its purposes is to host the web applications I'll develop, as a hobby. Perhaps one of those will get a fair amount of traffic some day. And I want to be prepared.

There seems to be a lot of brute force hacking attempts at my SSH daemon on port 22. DenyHosts has blocked one so far and I just got it working properly. I've disabled keyboard authentication and now solely use RSA2 keys. The last step I'll do is to change the port of SSH. Then I'm satisfied with it.

To learn how to secure LAMP (even more) I'll guess looking up tutorials on tightening security for each component of the AMP part. If you got any nice links or tips I would appreciate it a lot.

As I'm new to this I find it hard to know where to stop. Making it to insecure will be a problem. Making it "too" secure is just a matter of spending a lot of time for me, or possible disabling useful features. The latter I haven't had to just yet, as I don't have a problem with key authentication in SSH.

---

### Post by kidders on 2007-08-29
Hey again,

> **kentl said:**
> I don't know. :-) I just like to make it pretty secure as it will be public and always turned on.

The two major security concerns in the Linux world are (a) not keeping abreast of vulnerabilities in the software you are using, and (b) doing something blatantly silly. In practice, with specific reference to your setup, that might translate into...

**Cap the amount of software you install**
Running large amounts of experimental software on a publicly accessible box increases the probability of ending up with exploitable security vulnerabilities, by making undesirable interactions between applications more difficult to predict. On a Ubuntu server, you should ...[LIST]
[*]Confine yourself to software from the main repository for your distro.
[*]Absolutely never install anything without involving the package manager.
[*]Try to install as little as possible.[/LIST]**Try not to get paranoid**
Script kiddies knocking on your SSH server's door aren't really anything to worry about on a properly configured box. It's just annoying. Confining yourself to key-based authentication is a handy way to put your mind at ease, but do also make sure your local usernames & passwords aren't too obvious.

As far as software goes, default configurations of most things are usually sufficiently secure for general use. SSH servers are a good example. Over-securing yourself can often yield absolutely no benefit, and simply wind up making life unnecessarily hard for yourself (as you mentioned).

**Adhere to established norms**
Be sure to use standard solutions to standard problems. Thankfully, it's quite difficult to come up with a truly "original" problem, so chances are tried & trusted solutions exist already for anything you might encounter. Be sure to use them.

**Be careful with PHP**
PHP can pose serious security problems, so ...[LIST]
[*]Don't make low-quality code public accessible.
[*]Don't enable PHP components you're not using.[/LIST]PHP makes your system particularly vulnerable to lax filesystem access controls, since there is always the possibility that someone may succeed in performing a so-called arbitrary code execution. Failing to adequately control access to your filesystems qualifies as "blatantly silly", and is something Linux will crucify you for.

PHP can also act as a vehicle for attacks via a MySQL server. There is usually nothing you can do with a database server to reduce this risk, beyond the common-sensical (eg not using an unduely privileged MySQL account to access databases, and ensuring all SQL is properly escaped).

**Plan for disaster with your databases**
_Provided your local network is trusted_, trying to secure a MySQL server against outside interference is pointless. Needless to say, you should never make one publicly accessible. Consequently, be sure you have a way of quickly restoring one that becomes corrupted for some reason.

Anyhow, that's just a few random thoughts. One thing I would strongly recommend is learning to use iptables. You'll invariably need it at some point, and knowing how to configure it securely is important.

---

### Post by kentl on 2007-08-30
Thanks for your informative reply! I'm loving it. :-) I'll try to return the favor to someone else when I have something to contribute, to keep the ball of friendliness rolling.

> Cap the amount of software you install
I'll be sure to think about that. I've got some services I really need/want, and I'll try not to get carried away by installing everything I can get a hold of. Of course, part of the goal with the home server is to play around a bit and have fun, but I still like to keep it fairly secure.

> Try not to get paranoid
Good advice. I'll try. :-) However as for SSH I've already got it up and running. After following the advice in a five step, secure SSH, article I found: [http://thinkhole.org/wp/2006/10/30/five-steps-to-a-more-secure-ssh/](http://thinkhole.org/wp/2006/10/30/five-steps-to-a-more-secure-ssh/)

> Adhere to established norms
Yeah. I'm doing it already by asking you guys and gals here at the forum. Combined with doing my research on the Wiki, guides and on the net in general.

> Be careful with PHP
I'll check into which PHP components that were installed by default and disable those I won't be using. I'll also look into which account PHP uses and its privileges. So that I may restrict the amount of harm I'll get if someone somehow gets into my server using it.

Apart from watching out so that I don't make my own applications open to, for example, SQL injection, I don't really know what to do.

I will also look into which account MySQL uses. And make sure it has no more privileges than it needs.

> Plan for disaster with your databases
When I get something in there worth saving I'll implement some kind of backup solution.

I'll use a versioning system when coding, thinking about Mercury as I want something simple and decentralized, but for the database versions I guess I'll do a database dump. This paragraph is sort of out of context, I'm just thinking out aloud. :-) 

iptables seems very hard. At least judging by the brief snippets of config files I've seen. At the moment I'm using the firefall on my Linksys WRT54GL. Later on I plan to install OpenWRT on it, so that I have linux and iptables on it, by then I have to study this stuff.

---

### Post by kidders on 2007-08-30
You certainly seem to have sorted yourself out quite nicely. :-)

Just to save you some trouble...

> **kentl said:**
> I'll also look into which account PHP uses and its privileges.
...
I will also look into which account MySQL uses. And make sure it has no more privileges than it needs.
Standard practice in Linux (and similar OSs) is to run high-risk server apps using dedicated accounts.
[LIST]
[*]Such accounts are usually shell-less and passwordless, so they can't really be "used", as such ... but root can launch processes using them.
[*]For added security, processes run using dedicated accounts can be chrooted (aka "jailed") into their home directories. In your case this may be overkill though.
[*]MySQL servers typically have an account to themselves; Apache PHP modules tend to run as the same user as the web server. Altering either is not recommended ... particularly with Ubuntu.[/LIST]Incidentally, database dumps may be low-tech, but they work a treat. I tend to habitually dump LDAP and SQL databases before performing upgrades ... to guard against boo-boos.

> **kentl said:**
> iptables seems very hard.Some of how it works can be a bit subtle, but it's a really nice router/firewall with some great features. Although it has many front-ends designed to make working with it a little less like brain surgery, I tend not to use them, personally.

A firewall built into your internet gateway will do a perfectly good job though ... iptables would just be a little more flexible.

---

