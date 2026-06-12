---
title: "Logging SSH password attempts"
date: 2008-05-20
forum: General Help
---

### Post by ryanfx on 2008-05-20
As the title says.. i did some searching but I couldn't find anything.

Is there any way to log not only the user name attempted to login to my SSH server, but the password associated with it?

---

### Post by Monicker on 2008-05-20
I think if you change the LogLevel in sshd_config to DEBUG, it may show that information.

---

### Post by tamoneya on 2008-05-20
i think you will have trouble finding something that does that since it isnt a very good security policy because that means that all password attempts are stored as plaintext instead of as a hash.  This means that if the system is compromised that all the users passwords would be easily readable.  If you really want to do this you could try looking into linux key logger.  It is available in the repositories and you can search for it.  I believe the package name is lkl so you could install with the following command.
```
sudo apt-get install lkl
```

---

### Post by ibuclaw on 2008-05-20
Wouldn't that be a security risk for all the right attempts?

Or are you just needing the wrong attempts?

Erm...
I think [Sebek]("http://www.honeynet.org/tools/sebek/") is capable of this.
[A small bit of citation.]("http://www.honeynet.org/tools/sebek/faq.html#faq1")

Regards
Iain

---

### Post by ryanfx on 2008-05-20
I simply need all of the wrong attempts logged as my server does not even allow for user name / password authentication.  It exclusively uses public key authentication but bots are still trying user name's and passwords.

So.. doing this would create no security hole

---

### Post by hyperair on 2008-05-20
Even if it were a wrong attempt, logging the attempted password is very bad for security, and an invasion of privacy towards the users of that system (if you're not the only one). 

Here's a potential scenario:
Let's say my password is "linuxrocks". I mistype it while attempting to log in, as "linyxrocks". Don't you think that if this was logged, an attacker will know it's a typo and just correct the wrong letter? 

Another potential scenario:
I have a series of passwords I use for multiple places. One day I use one of my existing (but wrong) passwords while logging in via SSH. An attacker will hence know one of my passwords and it will be compromised.

---

### Post by MaindotC on 2008-05-20
> **tamoneya said:**
> i think you will have trouble finding something that does that since it isnt a very good security policy because that means that all password attempts are stored as plaintext instead of as a hash.  

I think he means remote attempts not people sitting at the machine in question.  Hell if unauthorized people had physical access it's all over.

---

### Post by ibuclaw on 2008-05-20
> **hyperair said:**
> Even if it were a wrong attempt, logging the attempted password is very bad for security, and an invasion of privacy towards the users of that system (if you're not the only one). 

Here's a potential scenario:
Let's say my password is "linuxrocks". I mistype it while attempting to log in, as "linyxrocks". Don't you think that if this was logged, an attacker will know it's a typo and just correct the wrong letter? 

Another potential scenario:
I have a series of passwords I use for multiple places. One day I use one of my existing (but wrong) passwords while logging in via SSH. An attacker will hence know one of my passwords and it will be compromised.

Yeah, true, but there are lots of ways that you can increase security, for example, encrypting the data with [Vigenere's Cipher]("http://ubuntuforums.org/showthread.php?t=772016&highlight=Vigenere"). (Link is to old Ubuntu Forums Programming Challenge).

And when you come to view it, you read it through a pipe, instead of directly.

Regards
Iain

---

### Post by ryanfx on 2008-05-20
> **hyperair said:**
> Even if it were a wrong attempt, logging the attempted password is very bad for security, and an invasion of privacy towards the users of that system (if you're not the only one). 

Here's a potential scenario:
Let's say my password is "linuxrocks". I mistype it while attempting to log in, as "linyxrocks". Don't you think that if this was logged, an attacker will know it's a typo and just correct the wrong letter? 

Another potential scenario:
I have a series of passwords I use for multiple places. One day I use one of my existing (but wrong) passwords while logging in via SSH. An attacker will hence know one of my passwords and it will be compromised.

I am the only user to this system.  This experiment is more of a honeypot than anything, and as I said the only authentication measure accepted is public key authentication. No passwords are allowed, so if a password IS supplied, it is a fraudulent attempt.

---

### Post by hyperair on 2008-05-20
> **tinivole said:**
> Yeah, true, but there are lots of ways that you can increase security, for example, encrypting the data with [Vigenere's Cipher]("http://ubuntuforums.org/showthread.php?t=772016&highlight=Vigenere"). (Link is to old Ubuntu Forums Programming Challenge).

And when you come to view it, you read it through a pipe, instead of directly.

Regards
Iain

No matter how much you increase the security, I don't believe the system administrator has the right to view the users' passwords. Doing something like this is abuse of power and invasion of privacy IMO. Unless, of course, the system administrator is the only user of that system.

> **ryanfx said:**
> I am the only user to this system. This experiment is more of a honeypot than anything, and as I said the only authentication measure accepted is public key authentication. No passwords are allowed.
In that case, perhaps Sebek as mentioned above is the perfect solution for you.

---

### Post by ibuclaw on 2008-05-20
> **hyperair said:**
> No matter how much you increase the security, I don't believe the system administrator has the right to view the users' passwords. Doing something like this is abuse of power and invasion of privacy IMO. Unless, of course, the system administrator is the only user of that system.

Yes I can totally side with that, but the difference in how I see it is that I think that admins should know what the incorrect passwords are.

That way, you can configure Linux to prevent users having these passwords (and sometimes usernames) altogether.
[Read this interesting article here.]("http://www.securityfocus.com/infocus/1876") It's good to know what scripts are going for.
It also makes me happy that Ubuntu has the root account disabled by default! :D

Although for admins to know (or acquire) your password is wrong in every sense.
It was like that when I was at college. And if it was found that a student had a potentially offensive password, then they were punished for it!
They also had complete access to our files too, and people who named their files something stupid like "kd4klrf4fsdkl389.doc" got similiar treatment too.

...It was a nightmare. I can tell you that much.

One good way to bring down the number of attacks is to put your server on an "Uncommon" port. For example, an SSH server on port 1439 instead of the very popular port 80.

---

### Post by MaindotC on 2008-05-20
Hyper - listen to what he's saying - "honeypot" - he's talking about REMOTE attempts as in automated ssh scripts to brute-force the login.

However, I find your point very intriguing.  Yes, it could be quite unethical to view user's password attempts even though they're accessing his machine.  It could also be very ethical in the interests of security and perhaps retaliation (proving the user of a specific host was doing something criminal by showing they use the same password for all other authentication).  However, in the interests of privacy, I could see it better to simply deny any password attempt authentication and not log the actual password being entered.  For example, instead of the police saying "we're going to ensure no gun-carrying amerikans enter by conducting a private search" they could just say "we don't allow any amerikans (but canadians are ok :).

Very interesting point, hyperair.  I just read a book for a network administration class called The Visible Employee" - it dealt with the concept of monitoring and when it's ok and when it's not - and how to integrate monitoring without pissing off employees.

---

### Post by hyperair on 2008-05-20
> **tinivole said:**
> Yes I can totally side with that, but the difference in how I see it is that I think that admins should know what the incorrect passwords are.

That way, you can configure Linux to prevent users having these passwords (and sometimes usernames) altogether.
[Read this interesting article here.]("http://www.securityfocus.com/infocus/1876") It's good to know what scripts are going for.
It also makes me happy that Ubuntu has the root account disabled by default! :D

Although for admins to know (or acquire) your password is wrong in every sense.
It was like that when I was at college. And if it was found that a student had a provocative (potentially offensive) password, then they were punished for it!
They also had complete access to our files too, and people who named their files something stupid like "kd4klrf4fsdkl389.doc" got similiar treatment too.

...It was a nightmare. I can tell you that much.

One good way to bring down the number of attacks is to put your server on an "Uncommon" port. For example, an SSH server on port 1439 instead of the very popular port 80.
Port 80 is HTTP!

---

### Post by MaindotC on 2008-05-20
I know lol - I was gonna say what happened to 22

---

### Post by ibuclaw on 2008-05-20
> **hyperair said:**
> Port 80 is HTTP!

Lol, Oops...**22**, Sorry.

Erm, I need some coffee, fatigue is taking over... Not thinking straight :lolflag:

---

### Post by ibuclaw on 2008-05-20
You could check to see if ssh stores these details itself in one of the log files.

Something like
```
cat /var/log/* | grep ssh | less
```
could find it,


Though I think it may be inside a log called "messages".
Try:
```

sudo updatedb
locate messages.log

```
And see where that leads you.

Regards
Iain

---

### Post by ryanfx on 2008-05-20
> **tinivole said:**
> You could check to see if ssh stores these details itself in one of the log files.

Something like
```
cat /var/log/* | grep ssh | less
```
could find it,


Though I think it may be inside a log called "messages".
Try:
```

sudo updatedb
locate messages.log

```
And see where that leads you.

Regards
Iain

No it doesn't - even with verbose logging enabled :)

---

