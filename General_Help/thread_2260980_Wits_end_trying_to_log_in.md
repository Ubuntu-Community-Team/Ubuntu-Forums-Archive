---
title: "Wits end trying to log in"
date: 2015-01-15
forum: General Help
---

### Post by Stephen_Meyer on 2015-01-15
[solved]
I am using an older 2010 intel laptop that has dual boot Ubuntu/Windows.  As windows gets worse and worse, I installed Ubuntu a few months ago, after updating to LTS14.04 I can no longer log in to my laptop.  All 10 pages of notes from other posts on the forums have failed.  NEED help.

After boot up, the login screen is displayed.
Usual stuff at the top - on the left (myname)-laptop displays.  The usual stuff on the right.
Log in box
     (myname)     Ubuntu icon  [ can switch to Gnome login but that doesn't work either]
     Password box - entering my password here fails, screen blanks then returns to the login screen.
     Guest session - this works as expected as temporary.
CTRL+ALT+F2 opens terminal as expected.
(myname)@(myname)-laptop login: (myname)
Password:  (password)
(myname)@(myname)-laptop:~$
     I can preform all the sudo commands I have tried.  I can change to root with my password {root@(myname)-laptop:~#} and seem to be working there
But I cannot login to a session.

All suggestions welcome.

---

### Post by Bashing-om on 2015-01-15
Stephen_Meyer; Wellll ...

From that CTRL+ALT+F2 opened terminal - logged into the system - :
Do you have authority to access your desktop ?
```

ls -al .ICEauthority
ls -al .Xauthority

```

Who owns your desktop ?
```

ls -al /home
ls -al /home/Stephen_Meyer

``` substitute 'Stephen_Meyer' for the actual "username" you use on the system.

Depending on what is, we can give 'YOU" authority .. and we can give "YOU" ownership.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Stephen_Meyer on 2015-01-15
Thanks Bashing-om for the quick response, here is what it says:

ls -al .ICEauthority
     -rw-------1 (me) (me) 33934 Dec 24 02:22
ls -al .Xauthority
     no such file

ls -al /home
     total 12
     drwxr-xr-x 3 root root 4096 Nov 9 2010 . [dot is blue]
     drwxr-xr-x 23 root root 4096 Dec 12 13:59 ..  [dots are blue]
     dr-xr-xr-x 45 (me) (me) 4096 Jan 8 14:45 (me)   [me is blue]

ls -al /home /(me)
     304 then a big list.

So what does that mean?

---

### Post by Bashing-om on 2015-01-15
Stephen_Meyer; Welp;

The deal is:
> 
ls -al .Xauthority
no such file


Without that file, no one has authority to access X.

I am aware of a dirtyish (?) hack to make up that file, but let's await and see what others here can advise to create that file.
-it is supposed to be created when you start your session -.
I would be interested in knowing if there is a better way.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Stephen_Meyer on 2015-01-15
Candor appreciated Bashing-om, I can wait for a bit.  When I saw no file I figured I must have messed up something along the way.

---

### Post by steeldriver on 2015-01-15
@Bashing-om, the .Xauthority file should be created automatically on successful session-start

I rather think the problem is

```

d[COLOR=#ff0000]**r-x**[/COLOR]r-xr-x 45 (me) (me) 4096 Jan 8 14:45 (me)   [me is blue]

```

the user has no write permission to his own home dir

@Stephen_Meyer try

```

sudo chmod u+w /home/*username*

```

where *username *is of course replaced by your actual username

---

### Post by Bashing-om on 2015-01-15
@steeldriver; Hey thanks

Good catch - Me with that case of tunnel vision.

Do that and 
[INDENT][INDENT]I betcha, yes[/INDENT][/INDENT]

---

### Post by Stephen_Meyer on 2015-01-15
Steeldriver - THAT was the ticket...thanks so much.  Using Ubuntu now, yeah!
I will try to understand what you told me to do and improve.
Thanks also to Bashing-om, all good intentions....

Now to finish transfering files and dump that windows partition...

I'll be back (best Arnold impersonation I can manage)

---

### Post by steeldriver on 2015-01-15
Well Bashing-om did the heavy lifting - with EXACTLY the right diagnostics

Anyhow glad we got you up and running - please mark the thread as [SOLVED] to help others who may find themselves with the same issue

---

### Post by Stephen_Meyer on 2015-01-15
dont know if that was right...

---

### Post by Bashing-om on 2015-01-15
Stephen_Meyer; Yeah;

That was right. all done with this matter and I look forward to the next adventure.

[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

---

