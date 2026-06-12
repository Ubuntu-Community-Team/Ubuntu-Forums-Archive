---
title: "two users, one email address?"
date: 2007-05-24
forum: General Help
---

### Post by maphew on 2007-05-24
Hello Everybody,

My wife and I have been sharing the same email address for a decade or so, on a single computer with no local accounts (e.g. no login). Now that we've more or less made the transition to ubuntu we're having trouble sorting out how to deal with email. We like having separate logins and our own desktop settings etc. but have become accustomed to reading each others mail; we rarely need to ask each other "did you see....?"

Currently I've set things up so Evolution leaves the mail on our ISP's server and we both download everything. It's a pain downloading the same 5mb video from the relatives though. And then I have to periodically login in via webmail and clear the account out so we don't fill our quota and have mail start bouncing. Surely there must be a better way?

[Edit] One thing this current setup does not do, is let us see each others sent mail. And yes that is a problem. Now to see if a particular email has already been dealt with we need to Switch Users, fire up Evolution and then look at the Sent folder.

thank you for your thoughts.

---

### Post by ruy_lopez on 2007-05-24
Only one of you are logged in at a time, right?

Removing the mail folder contents from one account (in the .evolution folder), then creating hard links to the other account, should mean that when one person reads mail and downloads it, it will be added to the other account. 

I'm not too familiar with evolution, so maybe someone else can tell you the files that relate to the inbox, that you'd need to link. 

You'd also have to juggle the permissions a little, creating a shared group, and making the inboxes readable and writeable for that group.

If you can specify where evolution looks for the .evolution folder in the first place, that would be even easier, you'd just copy one account to a neutral folder (such as /home/) and point both evolution clients towards it.

---

### Post by ruy_lopez on 2007-05-24
Actually, my suggestions above would be a complete headache for evolution. Are you attached to evolution? Because sharing inboxes across home folders is trivial with Thunderbird.

---

### Post by techdude2007 on 2007-05-24
I just use webmail for all of my email uses, except at work.  Regarding the email quota...maybe you should get a GMail email account which gives you 2.8 GB of Space.  If you are still filling that up, try 30gigs.com which is providing 30 GB Of Email Space or Yahoo Mail, which is not providing unlimited space.

---

### Post by gjtoth on 2007-05-24
As previously mentioned, getting  GMail accounts would probably be your best bet.  Then, you can have your ISP forward your mail to both accounts.  I have this setup for my wife and I.  Seems to work quite well... so far.  ;)

---

### Post by matigol on 2007-05-24
Try thunderbird.
It's easy to work with many accounts.

:)

---

### Post by thelinuxguy on 2007-05-24
The alternatives mentioned above are viable. And Thunderbird is definitely worth a try. However, if you want to stick to evolution and you current mail setup, I tried out ruy_lopez's solution since I had already done that with Cedega.

[COLOR="Red"]Backup ~/.evolution folder before doing anything.[/COLOR]

1) Move ~/.evolution to a common place (I put it under /opt)
2) Delete your wife's .evolution folder after backing up any important mails
3) Create links to the common folder from your as well as your wife's home folder
```

ln -s /opt/.evolution ~/.evolution

```
4) Grant appropriate permissions. For testing, I made the folder writable by everyone. You may need to work on this
```

chmod -R 0777 /opt/.evolution

```

A small glitch. Whenever new mail arrives or you do anything in Evolution that creates a new file/folder in the common place, the creator gets the permissions and whenever the other person fires up Evolution from his/her login, there are errors all over the place. So both of you will have to execute step 4 before logging off everytime.

This setup worked when I tested but I found it very annoying. I am still in favor of Thunderbird though.

---

### Post by tgm4883 on 2007-05-24
> **thelinuxguy said:**
> The alternatives mentioned above are viable. And Thunderbird is definitely worth a try. However, if you want to stick to evolution and you current mail setup, I tried out ruy_lopez's solution since I had already done that with Cedega.

[COLOR="Red"]Backup ~/.evolution folder before doing anything.[/COLOR]

1) Move ~/.evolution to a common place (I put it under /opt)
2) Delete your wife's .evolution folder after backing up any important mails
3) Create links to the common folder from your as well as your wife's home folder
```

ln -s /opt/.evolution ~/.evolution

```
4) Grant appropriate permissions. For testing, I made the folder writable by everyone. You may need to work on this
```

chmod -R 0777 /opt/.evolution

```

A small glitch. Whenever new mail arrives or you do anything in Evolution that creates a new file/folder in the common place, the creator gets the permissions and whenever the other person fires up Evolution from his/her login, there are errors all over the place. So both of you will have to execute step 4 before logging off everytime.

This setup worked when I tested but I found it very annoying. I am still in favor of Thunderbird though.

Could step 4 be added to a shutdown(logoff) script?

---

### Post by thelinuxguy on 2007-05-24
> **tgm4883 said:**
> Could step 4 be added to a shutdown(logoff) script?

I tried adding it to ~/.bash_logout and also /etc/bash.logout but it didn't seem to work for me. I couldn't figure out what I was doing wrong.

---

### Post by psusi on 2007-05-24
You should just make the directory owned by a group both accounts are in.

---

### Post by onbongos on 2007-05-24
personally, i would just share a gmail account. there are fewer and fewer reasons to run a desktop email client these days

---

### Post by thelinuxguy on 2007-05-24
> **psusi said:**
> You should just make the directory owned by a group both accounts are in.

This seems more practical than the permissions thing I mentioned above. Any progress op?

---

### Post by maphew on 2007-05-25
> Only one of you are logged in at a time, right?

usually, but not always

> Are you attached to evolution?

not yet; been using thunderbird for several years and am accustomed to it. Since Evolution is the default ubuntu mail client though I figured we'd better give it a fair trial run. I'm assuming the debate about which client to set as default was long and vigorous and there must be some merit to Evolution.

> As previously mentioned, getting GMail accounts would probably be your best bet. Then, you can have your ISP forward your mail to both accounts.

How is this different from our current setup? As far as I can tell the only thing this would gain is no worries about quotas (which would certainly be a plus). We'd still be downloading messages twice and not be seeing the Sents.    I do use gmail, but am not particularily fond of using it via the web unless searching archives. It's terribly slow and awkward compared to a local client.

> sharing inboxes across home folders is trivial with Thunderbird.

uhh, how trivial? care to elaborate or point me to some place which describes how?


> Move ~/.evolution to a common place (I put it under /opt)
> [and symlink to] owned by a group both accounts are in.

I think we'll try this route and see how it goes. 

Thank you everyone for your ideas.

---

### Post by MagicThinker on 2008-02-01
> **tgm4883 said:**
> 
Backup ~/.evolution folder before doing anything.

1) Move ~/.evolution to a common place (I put it under /opt)
2) Delete your wife's .evolution folder after backing up any important mails
3) Create links to the common folder from your as well as your wife's home folder
Code:

ln -s /opt/.evolution ~/.evolution

4) Grant appropriate permissions. For testing, I made the folder writable by everyone. You may need to work on this
Code:

chmod -R 0777 /opt/.evolution

A small glitch. Whenever new mail arrives or you do anything in Evolution that creates a new file/folder in the common place, the creator gets the permissions and whenever the other person fires up Evolution from his/her login, there are errors all over the place. So both of you will have to execute step 4 before logging off everytime.



:)To solve this small glitch call evolution via a script example: Copy the following text, paste into a file and make it executable:

:KSnote: Important to create common folder owned by "nobody" belonging to group "fileshare" that houses your .evolution information that you wish to share with other accounts before running script.  This bit in the script ([COLOR="Purple"] '/home/shared/Emails_Internet/evolution'[/COLOR] ) is where i house my evolution email information and will need to be adjusted to where you have put your evolution folder. 
[INDENT][INDENT]#------------------------------------------------------------------------------
#!/bin/sh

# This will change the folders permissions so that everything is available you BEFORE running evolution.
	chgrp fileshare -R '/home/shared/Emails_Internet/evolution'
	chmod g+rw -R '/home/shared/Emails_Internet/evolution'

# This will launce evolution
	evolution --component=mail

# any changes that have been made including any new emails will be owned by you, so they will need to be changed so that every user can use them.
	chgrp fileshare -R '/home/shared/Emails_Internet/evolution'
	chmod g+rw -R '/home/shared/Emails_Internet/evolution'

# reason why permissions are changes before and after is to avoid any errors such as 
# "not able to sync mail, or so permissions ect.
#-----------------------------------------------------------------------------[/INDENT][/INDENT]

I have been using this script alittle over 3 months sharing the same email box, calendar, tasks and contacts with different user accounts.  Works well each user must run evolution through the script in order for there to be no errors.  This avoids having to mess with startup and logoff scripts.

---

