---
title: "&quot;sudo -u&quot; doesn't work, but &quot;kdesu -u&quot; does?"
date: 2006-08-27
forum: General Help
---

### Post by msak007 on 2006-08-27
That's the question that I hope someone can answer. Here's a little bit of background:

I set up Kubuntu on my sister's laptop a month ago, and in hindsight I should've created my account first to be the admin. But anyway I just created an account for myself, gave myself admin / sudo privileges, and took all hers away. I was playing around with the "sudo -u <my username> <command>" command to allow myself to run sudo commands under her ID (so I wouldn't have to keep logging into a separate session and switch back and forth to do stuff) and discovered that it wasn't working (no output). I then tried "kdesu -u <my username> <command>, and it worked! It allowed me to run programs with admin rights as myself under her ID, which is the result of what I wanted using sudo.

I thought this was odd so I did a little bit of reading into the sudo and sudoers manual, and discovered a setting called "targetpw", that if set, would prompt for the password of the target user (rather than root) when the -u flag is used. It wasn't in the sudoers file, so I thought great - I'll edit the sudoers file, add that flag, and I'll be all set. Well needless to say that was stupid, and I ended up borking my sudoers file so nobody on the machine had sudo rights (I took my sister's away, I was locked out, and I never enabled the root account). I ended up having to boot into the Live CD, mounting my drive, and overwriting the sudoers file with the one from the CD to get it working again. 

So this leads me back to my initial question - does anybody know why "sudo -u" doesn't work, but "kdesu -u" does? It's not a *huge* inconvenience as I can still run graphical apps as myself, but I much prefer the CLI for speed (hence not wanting to start a second session on her laptop) and would really like to get this working. Any help would be appreciated.

P.S. Just for reference, these are the manuals I was using for reference  (same as the built-in man pages, but much easier to read and search in Firefox :)):
[URL="http://www.gratisoft.us/sudo/man/sudo.html"]sudo manual
[/URL][sudoers maual]("http://www.gratisoft.us/sudo/man/sudoers.html")

---

### Post by mlind on 2006-08-27
sudo -u seems to work like described on the manual page. (sudo prompts user's own password, not root's password).
```

$sudo -u root whoami
root

$sudo -u mlind whoami
mlind

```

If you want to temporarily switch to another user
```

su *username*

```

btw. You should always edit /etc/sudoers using **visudo** only.

---

### Post by msak007 on 2006-08-27
Thanks for the response, unfortunately it didn't help me. I understand how sudo works (prompt for the user's password), and that's why I was trying to use "sudo -u" so I can use a different user ID's password. But that's the thing - it wasn't working as it should for me. User A is the admin (me), I'm logged in as User B (my sister). When I issue a "sudo -u <User A> <command>, nothing happens. And I did edit sudoers using visudo, I should've been a little more clear about how I edited it (I assumed it was a given).

---

### Post by mlind on 2006-08-27
> **msak007 said:**
> Thanks for the response, unfortunately it didn't help me. I understand how sudo works (prompt for the user's password), and that's why I was trying to use "sudo -u" so I can use a different user ID's password. But that's the thing - it wasn't working as it should for me. User A is the admin (me), I'm logged in as User B (my sister). When I issue a "sudo -u <User A> <command>, nothing happens. And I did edit sudoers using visudo, I should've been a little more clear about how I edited it (I assumed it was a given).

How did you specify targetpw on /etc/sudoers? If you're going to use this, you've probably already set password for root account?

I think it's easiest (and more secure?) to use **su** whenever you need to run command as another user (not root).

---

### Post by msak007 on 2006-08-27
I never enabled the root account - that's why I ran into problems when the sudoers file got messed up. But when I edited sudoers, I simply appended "targetpw" to the "Defaults" entry in the file and saved it. I assume now that's the wrong procedure, but really couldn't decipher from the manual how it was to be added. I'd rather not enable root and use "su", so if I can't figure it out I'll look into it more later. I can always start another session as myself or use kdesu to run admin tasks using the GUI as that works. I just wanted to know why one method works and another doesn't...

---

### Post by mlind on 2006-08-27
> **msak007 said:**
> I never enabled the root account - that's why I ran into problems when the sudoers file got messed up. But when I edited sudoers, I simply appended "targetpw" to the "Defaults" entry in the file and saved it. I assume now that's the wrong procedure, but really couldn't decipher from the manual how it was to be added. I'd rather not enable root and use "su", so if I can't figure it out I'll look into it more later. I can always start another session as myself or use kdesu to run admin tasks using the GUI as that works. I just wanted to know why one method works and another doesn't...

I think adding targetpw to Defaults:  is the correct way to do it. Or adding Defaults:*username* entry. You need to have password for root account now, because it's going to prompt root's password, not current user's.
I'm not sure, but you can probably use targetpw to force non-root password too. This is probably what you're after here?


This has nothing to do with root privileges, it's a relogin as another user.
```

su *username* 

```

---

### Post by msak007 on 2006-08-27
My understanding was that if targetpw was set, it would prompt for the user's password (the one specified with -u - the "target"), not root's, so that may be where my source of confusion was. I tried "su -u <my user name>" and that worked! That's really all I was after...being able to run terminal commands as myself using sudo without having to start a second session. It was also my understanding that "su" automatically invokes a root session, and I didn't know a username could also be specified there. I apologize for all the confusion, guess I still have a lot to learn :). Thanks again.

---

