---
title: "[SOLVED] How to change User Name?"
date: 2008-06-07
forum: General Help
---

### Post by dkc.com on 2008-06-07
Hi friends,
I have recently installed Ubuntu 8.04 LTS. When I go to system>preferences>about me,
I can see an option there to change the password but is there any was to change the user name?

---

### Post by TeoBigusGeekus on 2008-06-07
Perhaps if you logged in as root and then fiddled with
System->Administration->Users and Groups
might do the trick.

---

### Post by hut101 on 2008-06-07
To the best of my knowledge there is no mean to change the name of a user once that account if created in Ubuntu. You'll have to create a new user with the desired name and move all files from the old user account to the new user account before deleted the old user.

---

### Post by nick_h on 2008-06-07
I think you can use the -l option with the usermod command.

For the manual page, type:
```
man usermod
```

---

### Post by bodhi.zazen on 2008-06-07
Change username : [http://ubuntuforums.org/showthread.php?p=4968235](http://ubuntuforums.org/showthread.php?p=4968235)

---

### Post by dkc.com on 2008-06-08
> **bodhi.zazen said:**
> Change username : [http://ubuntuforums.org/showthread.php?p=4968235](http://ubuntuforums.org/showthread.php?p=4968235)

Thanks mate really worked for me.

---

### Post by TsinganKralis on 2009-09-13
> **bodhi.zazen said:**
> Change username : [http://ubuntuforums.org/showthread.php?p=4968235](http://ubuntuforums.org/showthread.php?p=4968235)
the link isn't working

---

### Post by bodhi.zazen on 2009-09-13
> **TsinganKralis said:**
> the link isn't working

Try again, it is working now

---

### Post by solsen300 on 2009-09-16
when i click the link it says **solsen300**, you do not have permission to access this page.

---

### Post by jondkent on 2009-09-16
> **solsen300 said:**
> when i click the link it says **solsen300**, you do not have permission to access this page.

dito here

---

### Post by bodhi.zazen on 2009-09-16
OK, here is the solution I posted :

I like to directly edit /etc/passwd and /etc/groups

First open a terminal, become root ```
sudo -i
```

Now:

```
usermod -d /home/new -m old

sed -i -e 's_old_new_g' /etc/passwd

sed -i -e 's_old_new_g' /etc/group

sed -i -e 's_old_new_g' /etc/shadow
```

---

### Post by Pasea on 2009-10-22
Isn't working for me either.

---

### Post by bodhi.zazen on 2009-10-22
> **Pasea said:**
> Isn't working for me either.

Look up at my last post ...

---

### Post by x C0MMAND0 x on 2009-10-22
> **jondkent said:**
> dito here

+1 for not being able to access

---

### Post by bodhi.zazen on 2009-10-22
The link is not working as it has been jailed.

If you read my posts as I requested you will see I posted the information on this thread, here :

[http://ubuntuforums.org/showpost.php?p=7958725&postcount=11](http://ubuntuforums.org/showpost.php?p=7958725&postcount=11)

morale of this post : read my previous post please.

---

### Post by dbowlin17 on 2009-10-24
> **bodhi.zazen said:**
> OK, here is the solution I posted :

I like to directly edit /etc/passwd and /etc/groups

First open a terminal, become root ```
sudo -i
```Now:

```
usermod -d /home/new -m old

sed -i -e 's_old_new_g' /etc/passwd

sed -i -e 's_old_new_g' /etc/group

sed -i -e 's_old_new_g' /etc/shadow
```

I am very very new to this all, is there like step by step instructions telling me how to become root?

---

### Post by bodhi.zazen on 2009-10-24
> **dbowlin17 said:**
> I am very very new to this all, is there like step by step instructions telling me how to become root?

Open a terminal :

It is in the main menu

Applications -> Accessories -> Terminal

enter:

```
sudo -i
```

When prompted, enter your login password. You will not see anything on the screen as you type your password, this is normal.

You will then have a root shell.

enter the commands as above.

---

### Post by darck1 on 2009-10-28
> **bodhi.zazen said:**
> OK, here is the solution I posted :

I like to directly edit /etc/passwd and /etc/groups

First open a terminal, become root ```
sudo -i
```

Now:

```
usermod -d /home/new -m old

sed -i -e 's_old_new_g' /etc/passwd

sed -i -e 's_old_new_g' /etc/group

sed -i -e 's_old_new_g' /etc/shadow
```

This is cool but it doesn't address shortcuts, desktop settings and other things that might get broken. DISCLAIMER: I'm a complete Linux n00b so if this breaks your system - don't cry to me! But this is how I do it:
 ```

usermod -d /home/new -m old
find /home/new /etc/ -path '/home/new/idontwanttosearchthisdirbcuzitshugeandiknowitsok' -prune -o -type f -exec sed -i 's,/home/old,/home/new,g' {} +

```

---

### Post by kodylaw on 2009-10-28
same for me :-( .... Also, I never activated my account, but when I follow the link for activation, it says it is already active, and thus the loop perpetuates ....

---

### Post by kodylaw on 2009-10-28
Thanks bodhi!  When you write 's_old_new_g', is that to be taken literally ?

---

### Post by kodylaw on 2009-10-28
I did the instructions as indicated and the home directory now exists, but the user does not seem to  root@law-ubuntu:/home/law$ su law Unknown id: law   please let me know if you have a suggestion.  Thanks alot!

---

### Post by wlraider70 on 2009-10-28
hey me too

---

### Post by bodhi.zazen on 2009-10-28
> **kodylaw said:**
> Thanks bodhi!  When you write 's_old_new_g', is that to be taken literally ?

no, you have to change "old" to your old home directory and "new" to the new.

---

### Post by mohanmehta on 2009-11-20
I want to ask a question about bchunk ad how to use it.However the forum is not allowing me to post my question.What kind of a wierd forum is this

---

### Post by ArielEnter on 2009-12-24
> **solsen300 said:**
> when i click the link it says **solsen300**, you do not have permission to access this page.

same thing here

---

### Post by Barriehie on 2009-12-24
> **ArielEnter said:**
> same thing here

Have to read post #15 :)

Barrie

---

### Post by noiamsamiam on 2010-01-21
likewise I also cannot access this link and from the replies to this thread this sounds like exactly the info I need

---

### Post by syn4k on 2010-02-15
>  Re: [SOLVED] How to change User Name?
The link is not working as it has been jailed.

If you read my posts as I requested you will see I posted the information on this thread, here :

[http://ubuntuforums.org/showpost.php...5&postcount=11](http://ubuntuforums.org/showpost.php...5&postcount=11)

This does not work.
usermod reports: user is currently logged in.

---

### Post by AbangBoltok on 2010-05-18
> **bodhi.zazen said:**
> OK, here is the solution I posted :

I like to directly edit /etc/passwd and /etc/groups

First open a terminal, become root ```
sudo -i
```

Now:

```
usermod -d /home/new -m old

sed -i -e 's_old_new_g' /etc/passwd

sed -i -e 's_old_new_g' /etc/group

sed -i -e 's_old_new_g' /etc/shadow
```


sorry for bringing up this question again.
but i want to give my laptop for my brother and he doesnt want to use my username.

i used this command first:
```
sudo -i
```
and then i was as root on terminal session.
but after i entered this:
```
usermod -d /home/new -m old
```
i changed new as my brther username and old as my username.

but this message comes up.
> usermod: user sparta is currently logged in

how can i use this commands? 
thanks.

---

### Post by bodhi.zazen on 2010-05-18
@ [AbangBoltok]("http://ubuntuforums.org/member.php?u=1061495")

Honestly it is almost easier to make a new user.

If you wish to do this you should either :

1. Boot to recovery mode, this will be command line only, then run those commands.

2. Edit those files directly, use gksu gedit.

---

### Post by jondodson on 2010-06-05
I've just used this and can confirm it works.  The exact syntax I used, in recovery mode (hold down shift at boot to get recovery mode) was
usermod -l new -m -d /home/new old
where new and old are obviously your old and new (ie intended) usernames.

As well as renaming the user, this command also renames your home folder.  

There may be a few bits of tidying up to do afterwards:
1. If you have auto log in set, you'll need to log in manually first time after the change and re-set it up (system>administration>login screen, unlock).  So make sure you know your old username password (which might be different to your root password)
2. You might need to change the command path of programs you have installed yourself outside of software centre/synaptic, depending on where you installed them.  I had to change the path of Google Earth (right click Ubuntu sign>edit menus>internet>google earth>properties, then edit the 'command' line to use your new username.
3. Any other programs you have that use and point to directory paths may need those paths tweaking.  I had MAME installed and so I had to edit the roms directory path, no biggie.  I also had to edit paths in Compiz for  wallpaper/skydome/cubecaps needed redoing as well.

All went smoothly for me. I totally misunderstood what I was doing during the original OS installation and ended up with dellinspiron6000@dellinspiron6000, but now it's a much more sensible jon@dellinspiron6000.

---

### Post by hariks0 on 2010-06-26
Please enable the link.

---

### Post by Fishscene on 2010-08-30
The link is not available to me either. Why is this marked as solved when the solution can't be shared with everyone?

---

### Post by bodhi.zazen on 2010-08-30
> **Fishscene said:**
> The link is not available to me either. Why is this marked as solved when the solution can't be shared with everyone?

A thread I marked as solved when it is solved to the satisfaction of the OP.

You are free to start you own thread.

The "broken link" has bee re-posted on this thread several times.

[http://ubuntuforums.org/showpost.php?p=7958725&postcount=11](http://ubuntuforums.org/showpost.php?p=7958725&postcount=11)

---

### Post by flowermonster on 2010-10-04
[QUOTE=jondodson;9416479]I've just used this and can confirm it works.  The exact syntax I used, in recovery mode (hold down shift at boot to get recovery mode) was
usermod -l new -m -d /home/new old
where new and old are obviously your old and new (ie intended) usernames.

As well as renaming the user, this command also renames your home folder.  


_______________________________
ThanKs, jondodson
That worked for me, too.

---

### Post by Crazedpsyc on 2010-10-04
Thanks bodhi.zazen but when I got to that link it says
> **Crazedpsyc**, you do not have permission to access this page. This could be due to one of several reasons:

[LIST=1]
[*]Your user account may not have sufficient privileges to access this  page. Are you trying to edit someone else's post, access administrative  features or some other privileged system?
[*]If you are trying to post, the administrator may have disabled your account, or it may be awaiting activation.
[/LIST]
what's up with that?
EDIT: Oh, woops sorry didn't notice there were more pages that explain that

---

### Post by fox-mulder on 2011-03-02
someone is withholding information, why?

---

### Post by bellial on 2011-07-04
So, after reading all the back posts, this worked like a charm! Reading is a virtue! :D

---

### Post by aliciapg on 2011-08-13
Same. That's not useful.

---

### Post by gavarchand on 2011-09-30
> **dkc.com said:**
> Hi friends,
I have recently installed Ubuntu 8.04 LTS. When I go to system>preferences>about me,
I can see an option there to change the password but is there any was to change the user name?.

---

### Post by rajke88 on 2012-07-14
i made mistake after installing new system, i was short on time, and i accidently misstyped username. How i solved it.. 

1) i went to user accounts and i added new user with correct username and gave him administrator privileges
2) i rebooted computer and logged in as that other user
3) went again to user accounts setup and deleted previous user that i used to create new user with valid username.

p.s since i didn't have any data on that old account so i used this way. Don't try this if you have important data on the account where you want to change name, you will loose it :P

---

### Post by Quackers on 2012-07-14
This is an old thread rajke88. You may be better off giving the information in a new thread.

---

