---
title: "I got hacked twice on Ubuntu 18.04, don't want third time"
date: 2021-05-22
forum: General Help
---

### Post by andymyvps on 2021-05-22
Hosting gave me fresh installation of Ubuntu 18.04. I changed password for root, created other user (but never used it), installed Apache, PHP, MySQL, created remote user for Mysql and uploaded my website. After few days hosting shut down the server, because it was attempting to connect to other servers.

I reinstalled whole thing. And few days I was shut down again. **But I don't know how I'm getting hacked.**

-------

"kthreaddi", which is some crypto miner. Could this help me? Check which user created it, what rights it has (if they somehow compromise root or what)? I still have infected server running here (disconnected from internet), any input is very welcome.  

[IMG]https://i.imgur.com/NxST3Sj.png[/IMG]

---

### Post by QIII on 2021-05-22
I recommend you don't use root at all.  Delete the account's password and you will effectively disable the account.  Use your other account as a super-user and make sure your password is complex.

Do you use SSH to log in?  Don't allow root login, don't use password login.  Use public/private keys.  Allow SSH only over a high-numbered port.

You currently have SSH on port 22 (the standard) and you are using a root account.  That means a hacker need only brute-force your root password to get in.  He has the port and the user already.

How frequently do you review your logs?

---

### Post by andymyvps on 2021-05-22
> **QIII said:**
> I recommend you don't use root at all.  Delete the account's password and you will effectively disable the account.  Use your other account as a super-user and make sure your password is complex.

Do you use SSH to log in?  Don't allow root login, don't use password login.  Use public/private keys.  Allow SSH only over a high-numbered port.

You currently have SSH on port 22 (the standard) and you are using a root account.  That means a hacker need only brute-force your root password to get in.  He has the port and the user already.

How frequently do you review your logs?


First time I was hacked after about 7 months. But second time I was hacked within 24 hours. Second password was "karel4029euplavby" - not the best, but how do you brute force it in 24 hours, especially it being non-interesting target?

I understand that better login security is a way to go. But before I wipe out infected server is there something more I can do to identify where did it come from?

---

### Post by CharlesA on 2021-05-22
> **andymyvps said:**
> First time I was hacked after about 7 months. But second time I was hacked within 24 hours. Second password was "karel4029euplavby" - not the best, but how do you brute force it in 24 hours, especially it being non-interesting target?

I understand that better login security is a way to go. But before I wipe out infected server is there something more I can do to identify where did it come from?

You will need to review logs, but if you don't have a firewall in place that logs outbound traffic, it's unlikely you'll find anything useful outside of checking which processes are running.

In the OP, you didn't really say what you did to lock your server down or what you were running on it - only that you had a database and web server with PHP. Are you running Wordpress or another CMS?

---

### Post by andymyvps on 2021-05-22
> **CharlesA said:**
> You will need to review logs, but if you don't have a firewall in place that logs outbound traffic, it's unlikely you'll find anything useful outside of checking which processes are running.

In the OP, you didn't really say what you did to lock your server down or what you were running on it - only that you had a database and web server with PHP. Are you running Wordpress or another CMS?


Hosting disconnected my server once they got reports about it trying to connect to other servers.

Website made on Laravel. I only installed Apache, PHP, MySQL, Composer.

---

### Post by CharlesA on 2021-05-22
> **andymyvps said:**
> Hosting disconnected my server once they got reports about it trying to connect to other servers.

Website made on Laravel. I only installed Apache, PHP, MySQL, Composer.

If you don't have access to the server, your best bet would be to wipe the instance and start from scratch.

There are some good guides for hardening your server - most of them include steps to lock down SSH access and enable key-based authentication for SSH.

Here are a couple examples:
[https://www.linode.com/docs/guides/securing-your-server/](https://www.linode.com/docs/guides/securing-your-server/)
[https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-20-04)

FWIW, I have SSH locked down at both the firewall level and via SSH keys on my VPSes.

You can't get attacked if it isn't open to the world. If the firewall fails for some reason, the attacker would still need my private key in order to connect.

---

### Post by TheFu on 2021-05-23
I doubt someone is cracking your password in that time, but you really shouldn't be using passwords at all - use ssh-keys.  There are thousands of how-tos for that.

I think these are the problem: Apache, PHP, MySQL.  It is easy to not configure those to be secure and crap php code is the most likely problem.  

For fun, bring up the server, don't enable apache, put all your stuff onto it, but don't allow apache to run.  I bet it doesn't get hacked.  Out of the box, Ubuntu Server doesn't get cracked unless you are using passwords that are better for luggage - 123456.  But really, any password should be randomly generated by your password manager for all enabled accounts and you should use ssh-key-based authentication.  Also, run fail2ban, so any brute force attempts are automatically blocked.  Validate that too.  Late 1 night, try to connect with bogus passwords until you are locked out - a dynamic firewall rule will be enabled.  I think the default period is 1 hour.  The next morning, you'll be able to get in.

Re-look at your settings and security posture for php, apache and mysql.  Do you block access for each of those so that only the end-users who need access can gain access?  If you are in the UK and don't expect any paying clients from Latin America, perhaps some firewall rules to block that access are needed.  Any country that shouldn't have access ... er ... shouldn't have access to anything on the server.   If only you and a few IPs that you know should have access to ssh in, don't let anywhere else have access.

And setup versioned backups, so you can compare the system between when it was installed and when it gets hacked. Wouldn't that be helpful to determine exactly what you've done wrong?

It should be obvious, but we can't really help you. We don't have logins (and don't want any) on this system.  Get paranoid.  Look up "best practices" for each tool/server you install. Follow the best practices. Look up how to crack each tool/service you install too and ensure you don't allow those methods. I suspect you have assumed that some guide installs everything in a secure manner, which just isn't true.  They are interested in a working system, not a secure system, for the most part.

There is a mod_security for apache which can ruin your day/week too.  I don't use it. Tried, but there were just too many settings.  In the end, I setup a VPN and blocked all access to the servers that didn't connect through the VPN first.  I have a low confidence in being able to secure any php webapp myself, so I don't allow php webapps to be accessed over the internet.

---

### Post by andymyvps on 2021-05-23
> **TheFu said:**
> I doubt someone is cracking your password in that time, but you really shouldn't be using passwords at all - use ssh-keys.  There are thousands of how-tos for that.

I think these are the problem: Apache, PHP, MySQL.  It is easy to not configure those to be secure [COLOR=#ff0000]_**and crap php code is the most likely problem.**_[/COLOR]  

For fun, bring up the server, don't enable apache, put all your stuff onto it, but don't allow apache to run.  I bet it doesn't get hacked.  Out of the box, Ubuntu Server doesn't get cracked unless you are using passwords that are better for luggage - 123456.  But really, any password should be randomly generated by your password manager for all enabled accounts and you should use ssh-key-based authentication.  Also, run fail2ban, so any brute force attempts are automatically blocked.  Validate that too.  Late 1 night, try to connect with bogus passwords until you are locked out - a dynamic firewall rule will be enabled.  I think the default period is 1 hour.  The next morning, you'll be able to get in.

Re-look at your settings and security posture for php, apache and mysql.  Do you block access for each of those so that only the end-users who need access can gain access?  If you are in the UK and don't expect any paying clients from Latin America, perhaps some firewall rules to block that access are needed.  Any country that shouldn't have access ... er ... shouldn't have access to anything on the server.   If only you and a few IPs that you know should have access to ssh in, don't let anywhere else have access.

And setup versioned backups, so you can compare the system between when it was installed and when it gets hacked. Wouldn't that be helpful to determine exactly what you've done wrong?

It should be obvious, but we can't really help you. We don't have logins (and don't want any) on this system.  Get paranoid.  Look up "best practices" for each tool/server you install. Follow the best practices. Look up how to crack each tool/service you install too and ensure you don't allow those methods. I suspect you have assumed that some guide installs everything in a secure manner, which just isn't true.  They are interested in a working system, not a secure system, for the most part.

There is a mod_security for apache which can ruin your day/week too.  I don't use it. Tried, but there were just too many settings.  In the end, I setup a VPN and blocked all access to the servers that didn't connect through the VPN first.  I have a low confidence in being able to secure any php webapp myself, so I don't allow php webapps to be accessed over the internet.

You actually solved it!

Due to limited experience with running servers I was convicted I did something wrong and it has to do something with server/Ubuntu. It didn't. It was website itself, which I didn't analyze until you mentioned it.

Pulling some PHP error logs I was able to find out, that it was due to vulnerable Laravel package [https://github.com/facade/ignition/issues/350](https://github.com/facade/ignition/issues/350)

Thanks!

---

### Post by dragonfly41 on 2021-05-23
I also use Laravel 8 for php coding.  
It is a fine framework (there are others) but you have to configure correctly for production usage.
As the link above explains ..

> &#8226; never set APP_DEBUG=true in production
&#8226; you could disable runnable solutions completely by setting enable_runnable_solutions to false in the ignition.php config file   


Looking at a typical Laravel 8 app I created recently on localhost (for testing) I read ..

    'enable_runnable_solutions' => env('IGNITION_ENABLE_RUNNABLE_SOLUTIONS', null),

So clearly in production mode you need to tighten security.


**[Later edit]**
Found security reports..

[https://www.cybersecurity-help.cz/vdb/SB2021021402#:~:text=The%20vulnerability%20exists%20due%20to,complete%20compromise%20of%20vulnerable%20system](https://www.cybersecurity-help.cz/vdb/SB2021021402#:~:text=The%20vulnerability%20exists%20due%20to,complete%20compromise%20of%20vulnerable%20system).

[https://www.ambionics.io/blog/laravel-debug-rce](https://www.ambionics.io/blog/laravel-debug-rce)

---

### Post by andymyvps on 2021-05-23
> **dragonfly41 said:**
> I also use Laravel 8 for php coding.  
It is a fine framework (there are others) but you have to configure correctly for production usage.
As the link above explains ..




Looking at a typical Laravel 8 app I created recently on localhost (for testing) I read ..

    'enable_runnable_solutions' => env('IGNITION_ENABLE_RUNNABLE_SOLUTIONS', null),

So clearly in production mode you need to tighten security.


**[Later edit]**
Found security reports..

[https://www.cybersecurity-help.cz/vdb/SB2021021402#:~:text=The%20vulnerability%20exists%20due%20to,complete%20compromise%20of%20vulnerable%20system](https://www.cybersecurity-help.cz/vdb/SB2021021402#:~:text=The%20vulnerability%20exists%20due%20to,complete%20compromise%20of%20vulnerable%20system).

[https://www.ambionics.io/blog/laravel-debug-rce](https://www.ambionics.io/blog/laravel-debug-rce)


I read in new projects (Laravel 8) is not an issue anymore, as it uses Ignition version where it is fixed. Unfortunately my server is running project in Laravel 7, so I followed similar steps that you mentioned. Solved. I guess maybe I could just update Ignition instead. I'm glad we figured it out.

I was surprised that you can seriously infect server this way. I would expect that you need root access. No. Apparently one wrongly implemented file_get_contents (or what was the underlying problem) can turn server into a crypto mining machine that is attempting to connect to other server and trying to infect them too.

---

### Post by dragonfly41 on 2021-05-23
Also turn off debug mode ..

[https://www.e2enetworks.com/debug-mode-in-laravel-causes-websites-to-compromise/](https://www.e2enetworks.com/debug-mode-in-laravel-causes-websites-to-compromise/)

---

### Post by HermanAB on 2021-05-23
A server should also use some kind of mandatory access control - Tomoyo, SELinux or AppArmor.  If you want to know what is happening, send the log files to a different machine and sit and watch them regularly.

---

### Post by TheFu on 2021-05-23
> **andymyvps said:**
> You actually solved it!

Due to limited experience with running servers I was convicted I did something wrong and it has to do something with server/Ubuntu. It didn't. It was website itself, which I didn't analyze until you mentioned it.

Pulling some PHP error logs I was able to find out, that it was due to vulnerable Laravel package [https://github.com/facade/ignition/issues/350](https://github.com/facade/ignition/issues/350)

All code has mistakes ... except possibly code written by Don Knuth. He's pretty famous for having nearly bug free code. He was the first guy to pay for bug bounties.  People usually don't cash his checks when they come, because finding a bug in his code is extremely rare. They put the letter and check into a picture frame and mount it on their wall.

I used to work in an environment were we were introducing 1 bug every 2 yrs in about 1M SLOC. That's the work of 10-22 developers - among all of their code changes, 1 bug, every other year.  At one point, we believed all the serious bugs had been found using statistical methods.  
The project continued another 15 yrs. During those 15 yrs, over 100 "severe bugs" were uncovered that had been in the code at the time it was claimed to be bug free.  A "severe bug" was one that could cause loss of life or total vehicle loss.  None of those ever happened in the real world, thankfully.

php is an easy language to learn and use. It has about the lowest amount of skill to get something working of any computer language.  Thousands of new people learn a little php every day and put their code on the internet.  Their inexperience is the main issue, though it used to be the core language developers who were the problem in the 2000s.  They released new versions with known, serious, security, bugs multiple times.  And they were caught doing it!
OTOH, people complain about C or perl as being difficult languages and easy to create crap code if used. This means that noobs generally avoid using those 2 languages. That leaves programmers with more expertise, who still make mistakes, but not the trivial ones.  

There is no perfect language that is both powerful, will create secure software by default, and that is easy to pick up by people new to programming.  In the 1990s, Java was making the claim that it was THE language for those needs. We know better today.  Java has all sorts of problems, just like C, php, perl, and the 500+ other languages.

Anyways, the best we can do as system maintainers is to 
[LIST]
[*]ensure our systems are running patched code - not necessarily the newest version - just patched and currently supported.
[*]understand all the dependencies for our system and ensure it is all fully patched and supported code too.
[*]implement the idea of least privilege access. Only allow people/places that NEED access, to have access.
[*]have automatic, daily, versioned, backups.  Backups are my #1 security mandate. They provide information and safety against hundreds of problems.
[/LIST]

Anyway, happy that you found the root issue and were able to address it.  Please patch the dependencies weekly and keep an eye out for critical faults in each which might need to be patched quicker due to the risks involved.  Setup-and-forget doesn't work, unless you are ok rebuilding the system from scratch every few months after it gets hacked.

---

### Post by scorp123 on 2021-05-23
> **andymyvps said:**
>  ... Second password was "karel4029euplavby" ... not the best ...


Only lower case letters and a few numbers? That's way too simple
Please create more complex passwords, e.g. use a command to do that for you, e.g. **"pwgen -y 14 50"** and then pick one from the results.

Example:

```
> pwgen -y 14 50

ahx|eoJ0AhH2ie aquae=X7Uogh/e eipoh!ng1AY9Oh loo7reip9Eugo~ aSh2ieth1voo,j
Eer_e3Hiobu`o` eexa4Pohs+ah]L bah9Iech-i.Phe caiY7loo8hie|v Aejaich,or0Pie
shi4ohj2uChi!a boh;Shiej8roo! aeJ@eeF5Keid7v aqu"eilohP9Aim lu5AL4gu>ikeop
miyae7zoo!k6Oo aen1jae4Ree,xe aegh5bai)Nei|M Eh6IexiTh8bo~f Tiqu*ah3he]w7u
ees.oo-Gu&hah5 wio^NuuDalai5b an3on#oh2Ox@oh eeVa'u0ooxaef* cohGhai$H9eek0
Zei`w5eid/o.pe eevae"ph7phi5N ohf`e"Zui|soa1 zi#Ng[u8ooh8Ph cah&gh3Aeb}ee3
er(oh>Gae9ID6E Aibahxai0oP+ei ue8yua2aeGai,x Ulei5mohm#ie\c ahQu:aiw3dee#s
Eilu!n3Bei3ang iePai<n3ood5oh ohFoo_cei0uyah Rie4xoce/ce5aa Woh0phu%gh6ieN
Veit4ohDau*w1e thi9loh*Foe4la eet7tie6xe^Z'u AeB\aephoc0zao xiengee>riePh8
pa2cheif?o}y1Y Eengiesei\qu9j oc#ee&phiN7que airooSa@s7vi,a xaelahDee.y0bu
```

> **andymyvps said:**
>  ... but how do you brute force it in 24 hours, especially it being non-interesting target?


There are programs for that. And password collections are a thing. If you know where to look you can download 100+ GB of known cracked passwords (so called "Password dictionaries"), breach compilations, etc. And there are programs that are capable of taking already known passwords (e.g. *"karel"*) into consideration and then generate transmutations that the cracker can try too (e.g. *"karel01", "karel02", "karel03" ... "karel40" ...* ). Also: maybe that's not even the password that was cracked? Was that your SSH password? What if you forgot to secure your MySQL installation, or you left some other gap open and the intruder came in that way??

In addition what was already written regarding deleting root's password, changing the SSH port and only allowing login via SSH keys you should also familiarize yourself with **"fail2ban"** and straight up block wannabe-intruders. Just make sure you configure it properly so you don't lock yourself out.

> **andymyvps said:**
>  is there something more I can do to identify where did it come from?

Check output of **"sudo last"** and **"sudo lastb"** maybe? Although a hacker will usually wipe the traces they left in those log files if they manage to get in. But sometimes they forget to do that. One more reason to implement **"fail2ban"** and straight up ban any IP address that produces too many incorrect login attempts. Also check logs e.g. from MySQL or any other software you might have installed.

---

### Post by TheFu on 2021-05-23
Learning how professional password crackers work is eye opening.  
IronGeek posts conference videos on his website ... but they are all just youtube links.
https://www.youtube.com/user/irongeek/playlists[/url] has security videos and practical cracking information
Found this: [https://www.youtube.com/watch?v=WRtWQZSerCE](https://www.youtube.com/watch?v=WRtWQZSerCE)

If we are using passwords for external authentication, we've already lost.  Humans suck at making up passwords/passphrases.
If you cannot use key-based authentication, all we can do is:
[LIST]
[*]Don't use the same password 2 places.
[*]Use long, random, complex, generated passphrases.
[*]Use 2FA - device-based is best - avoid SMS/phone based.  Phones are some of the least secure devices.
[*]Setup strict firewall rules to prevent all access from unknown places and have a whitelist for places we know need access.
[*]If you can memorize the password, it isn't complex or long enough.
[/LIST]

Really, we should only memorize 2-3 passwords - and only for those things we have to physically touch and enter the password. This assumes the device won't support 2FA in some manner.

Sure, the "math" says that 13 random characters should be sufficient, but I disagree. We aren't trying to just protect encrypted stuff for today. We have to worry about 10-50 yrs into the future.  Since I'm never going to type any passphrase into a computer that I access over the internet anyways, longer and random is better than shorter and random. It doesn't matter whether it is 20 characters or 120 characters to me, so why not choose longer?

---

### Post by dragonfly41 on 2021-05-23
Another Password Generator ...

[https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)

---

