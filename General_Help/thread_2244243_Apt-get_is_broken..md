---
title: "Apt-get is broken."
date: 2014-09-14
forum: General Help
---

### Post by hdry on 2014-09-14
So I have to install Ubuntu Server 12.04 as part of my industrial training, but I ran into some problems while trying to use apt-get.

Namely, whenever I try to install any new software, it will either result in this:

[IMG]http://i.imgur.com/gFECQ8X.jpg[/IMG]

or 

[IMG]http://i.imgur.com/MzHzWUL.jpg[/IMG]

and I've edited the /etc/apt/sources.list in vi, so now it looks like this:

[IMG]http://i.imgur.com/JOeOzXc.jpg[/IMG]
[IMG]http://i.imgur.com/Z6jgAuK.jpg[/IMG]
[IMG]http://i.imgur.com/pXfeRWX.jpg[/IMG]

(The changes I've made are for the last four entries.)

I've tried fixing it using apt-get update and upgrade will usually result in this:

[IMG]http://i.imgur.com/sGcW3uB.jpg[/IMG]

And when I tried using aptitude, this will usually happen:

[IMG]http://i.imgur.com/Utl2hU5.jpg[/IMG]

I've also tried:

```
sudo apt-get autoclean $$ apt-get clear cache
```

Which resulted in:

[IMG]http://i.imgur.com/hT4ZBWI.jpg[/IMG]

So I think the apt-get component of this install is broken. Any advice on how to fix this?

---

### Post by ian-weisser on 2014-09-14
Your resolvconf, which translates domain names (foo.com) into IP addresses seems broken.

Test it: Ping the same server using the domain name, then again using the IP address.

If your network is configured using DHCP, then often the DHCP server will tell your system where to find the nameserver.
Otherwise, you must tell the system where the nameserver is.

---

### Post by hdry on 2014-09-14
> **ian-weisser said:**
> Your resolvconf, which translates domain names (foo.com) into IP addresses seems broken.

Test it: Ping the same server using the domain name, then again using the IP address.

If your network is configured using DHCP, then often the DHCP server will tell your system where to find the nameserver.
Otherwise, you must tell the system where the nameserver is.

So how do I do that?

EDIT: Assuming this is what you meant;

[IMG]http://i.imgur.com/5mmGkvH.jpg[/IMG]

It doesn't seem to be working.

---

### Post by hdry on 2014-09-15
I'm assuming it's a networking issue as well now:

[IMG]http://i.imgur.com/y1E79ks.jpg[/IMG]

They're able to ping each other in the same subnet, though:

[IMG]http://i.imgur.com/WBNIkny.jpg[/IMG]
[IMG]http://i.imgur.com/fCTfvXq.jpg[/IMG]

---

### Post by Bashing-om on 2014-09-15
hdry; Hi !

A DNS issue ?
what happens when you ping Google by IP ?
```

ping -c3 8.8.8.8

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by hdry on 2014-09-15
> **Bashing-om said:**
> hdry; Hi !

A DNS issue ?
what happens when you ping Google by IP ?
```

ping -c3 8.8.8.8

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

I tried pinging google by IP address and here's the result:

[IMG]http://i.imgur.com/j6Zjulq.png[/IMG]

---

### Post by Bashing-om on 2014-09-15
hdry; Hey;

Humm, Not getting past the router !

OK, let's talk to the router by addressing it .
To find the router's IP:
```

route -n

```
Then we go looking at who is routing what, where.

[INDENT][INDENT]a failure to communicate
[/INDENT][/INDENT]

---

### Post by hdry on 2014-09-15
> **Bashing-om said:**
> hdry; Hey;

Humm, Not getting past the router !

OK, let's talk to the router by addressing it .
To find the router's IP:
```

route -n

```
Then we go looking at who is routing what, where.

[INDENT][INDENT]a failure to communicate
[/INDENT][/INDENT]

So I executed the command you gave and this is the result:

[IMG]http://i.imgur.com/EV3v0Tp.jpg[/IMG]

---

### Post by Bashing-om on 2014-09-15
hdry; Ouch !

That says there is no path to the router .

Is there indeed a wired connection to the router ? (dual NICs ?)

Past my thinkability here now and I am calling it a night for this session. My eyes are blurring out and my think'n has become forced.

Will consider this and get back on it in my PM ( chores to get done in my AM ).

In the meantime, others will also pick up and push this little matter along.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]all of 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ritesh3 on 2014-09-15
Try to change the network settings of Virtual box.
Go to machine (on top of the virtual box machine) -> settings -> Network -> change "attachment to" settings with "Bridged adapter" -> select "ok" -> restart your virtual machine. 

After restart your machine "ping -c3 8.8.8.8" command. I hope this will fix your problem.

---

### Post by hdry on 2014-09-15
> **ritesh3 said:**
> Try to change the network settings of Virtual box.
Go to machine (on top of the virtual box machine) -> settings -> Network -> change "attachment to" settings with "Bridged adapter" -> select "ok" -> restart your virtual machine. 

After restart your machine "ping -c3 8.8.8.8" command. I hope this will fix your problem.

Alright, so I changed the network setting from "Internal Network" to "Bridged" and I was able to do this:

[IMG]http://i.imgur.com/dtZ0cge.jpg[/IMG]

But I still encounter this problem:

[IMG]http://i.imgur.com/tX3wPE6.jpg[/IMG]

And the reason I used an Internal Network earlier was because I needed it to connect to the other server for database replication purposes. When both computers are connected through the internal network they could see and ping each other (since they're on the same subnet) but even if I used both internal and bridged on the main vm, they can't see and ping each other.

---

### Post by The Cog on 2014-09-15
I think the virtualbox internal network has no internet access by design - it's internal only. You need to use bridged or NAT to get to the internet for the software repositories.

You need to update the apt database from the repositories before you can install anything because until the update, it doesn't know what is in the repositories. So try:
```
sudo apt-get update
sudo apt-get install ruby
```

---

### Post by hdry on 2014-09-15
> **The Cog said:**
> I think the virtualbox internal network has no internet access by design - it's internal only. You need to use bridged or NAT to get to the internet for the software repositories.

You need to update the apt database from the repositories before you can install anything because until the update, it doesn't know what is in the repositories. So try:
```
sudo apt-get update
sudo apt-get install ruby
```

I think I've mentioned before that even apt-get update doesn't work, but in case I didn't, here's the results:

[IMG]http://i.imgur.com/wtLtBTa.jpg[/IMG]

---

### Post by hdry on 2014-09-16
Well, even after a reinstall the problem still remains.

---

### Post by Bashing-om on 2014-09-16
hdry; HUH ??

Are you installing 2 different versions of ruby ? Explain to us how you are installing the application, and post back the output of:
```

apt-cache policy ruby
dpkg -l ruby

```

we see what we can do
[INDENT][INDENT][INDENT]to finger out what is going on here
[/INDENT][/INDENT][/INDENT]

---

### Post by hdry on 2014-09-16
> **Bashing-om said:**
> hdry; HUH ??

Are you installing 2 different versions of ruby ? Explain to us how you are installing the application, and post back the output of:
```

apt-cache policy ruby
dpkg -l ruby

```

we see what we can do
[INDENT][INDENT][INDENT]to finger out what is going on here
[/INDENT][/INDENT][/INDENT]

Well, I got:

```

apt-cache policy ruby
ruby:
[INDENT]Installed: (none)[/INDENT]
[INDENT]Candidate: (none)[/INDENT]
[INDENT]Version Table: (none)[/INDENT]
dpkg -l ruby
No packages found matching ruby

```

---

### Post by ian-weisser on 2014-09-16
As TheCog implied, apt will not download anything because your network settings seem to be wrong.
A reinstall won't help; the problem appears to be with the host VM manager network settings.

Specifically, your 'bridged' network apparently cannot resolve domain names. Apt uses domain names, not IP addresses.
Usually, the DNS information is provided by the DHCP server. If you are setting up a static network, you must manually tell the system where to find a DNS.

Is your bridged network static or dhcp?

---

