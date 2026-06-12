---
title: "fun with chmod :P"
date: 2008-03-03
forum: General Help
---

### Post by mickey13 on 2008-03-03
I was trying to restrict access for "other" users to everything but to the /home/ directory.  So I thought I was being really clever when I did the following:

sudo chmod 750 ../

[from the /home/ directory]

So now I can't move anywhere in the directory structure outside of /home/.  I did this remotely (ssh) and now I can't even log back in.  From PuTTy, I get "Network error: Software caused connection abort".  Needless to say I don't feel very clever any more, but does anyone have any ideas.  I haven't been near the physical server to try to reboot it, but I'll try that later.  Thanks for the help.

Mickey

---

### Post by PinkFloyd102489 on 2008-03-03
Yeah that wasnt smart. I dont know of anything to do, since almost every file and folder is chmodded differently.

I accidently did this once on /usr and had to reformat.

---

### Post by matthewcraig on 2008-03-03
Well - you did do what you set out to do.  Prevented users from accessing /, including yourself.
Unfortunately, it is very much appropriate and necessary for users to have access to files beyond their home directory.

Can you run the command 'sudo chmod 755 /' ?  Otherwise, I foresee a reinstall in your future.

Careful running that sudo command.

---

### Post by jken146 on 2008-03-03
delete

---

### Post by mickey13 on 2008-03-03
"Prevented users from accessing /"

I didn't realize that the 3rd digit was for all users.  If limiting that digit causes me to lose all access, then what's the point of the first two digits (keep in mind that it was chmod 750)?

I'll have to try the sudo chmod 755 / later.

Thanks for the replies.

---

### Post by matthewcraig on 2008-03-03
Owner, Users in Owner's Group, Everyone else.
These are the meanings of the three digits of the chmod command, which is probably something you should have checked before running the command with sudo.  I say this with no teasing.  If you are going to run commands with sudo, then you had better know exactly what they are doing.

---

### Post by mickey13 on 2008-03-03
Right, but I'm the owner, not just a user.  So why the problem.

Your guys' tone sucks.

---

### Post by seventhc on 2008-03-03
well, I'm not sure what you can do, but to help you better understand how permissions work here is a link to a permissions calculator. It does help put everything into perspective and can be useful. Have a look [http://www.robolink.co.uk/calculators10.htm](http://www.robolink.co.uk/calculators10.htm)

Nobody's tone sucks, you're just upset b/c you are locked out, you're not alone, I've done it myself. You might be able to fix it using the live cd in recovery since recovery mode gives you root permissions. Although not sure if that was effected or not but you can try it.
another place to look with some explanations [http://www.webweaver.nu/html-tips/chmod.shtml](http://www.webweaver.nu/html-tips/chmod.shtml)

---

### Post by mickey13 on 2008-03-03
Ok, for the people who find themselves in the same situation as me and need some help, this is what worked for me.  I'm running 7.10 (server).

I rebooted my machine, typed "root", then the password associated with the initial login name (my usual login name), ran "sudo chmod 755 /" and I'm good to go.  I hadn't done anything before to create a root user, it was just there.

Mickey

---

### Post by mickey13 on 2008-03-03
Seventhc:
I was aware that I could have done something really bad to my system.  I was as "happy-go-lucky" as I could be when I wrote the original post (see original post), but all the help I got included "that wasn't smart", and "you did what you did", and etc.  All I was asking for was a little help.  I think negative attitudes can keep some people from ever posting in the first place.

Anyways, I hope someone finds my solution useful.

---

### Post by seventhc on 2008-03-03
Yeah, I know, I do think there is a way to fix it, but I am not sure of what it is myself. I have seen other threads with similar situations and pretty sure they got it fixed. Hopefully someone here will post a solution for you.
I personally don't think it's stupid, hell I break mine all the time lol, but it is how I learn.
So don't worry and hang tight until someone can post a workable solution for you. :)

---

