---
title: "duplicate user groups"
date: 2008-01-02
forum: General Help
---

### Post by brianmulc on 2008-01-02
When I inspect my user groups, I have duplicates of many groups:), including: root, fuse and others.   The individual groups have different users checked as group members and do not allow editing of these checks. Is this normal?  Should there be duplicates?  If so, why?  If not, how did they get there and how do I correct it?  I believe it is interfering with my setting up of the system.  Thanks

---

### Post by blueridgedog on 2008-01-02
Is it only duplicated in the gui tool or in the file /etc/group as well?

To look at it:

```
cat /etc/group
```

---

### Post by stumped on 2008-01-15
Does anybody have an answer to this question:
[click here]("http://ubuntuforums.org/showthread.php?t=656706&highlight=groups")
I have a very similar problem,but I can edit the checks, and no, its is not duplicated in cat /etc/group, only in the gui tool.
I have noticed that when I first open it and click on manage groups, there are no duplicates.
Under manage groups, when I click on one of the groups, then properties,then ok, then thats when all of the duplicates show up.
Also when I first open the gui, if I click on a user, then properties, then advance tab, and set the main group for that user, then click ok, it changes the main group for one of the other users to something different then it was on. I hope this makes sense, as I'm not that good at explaining things.
I am currently running ubuntu edgy eft. 
Does anyone have any idea on how to fix this?

---

### Post by bodhi.zazen on 2008-01-15
Threads merged

Please Post /etc/group (or at least the duplicates) as requested.

---

### Post by stumped on 2008-01-15
Everything in the list is in there twice in the same order.
example,  root, users, dhcp,  etc etc   root, users, dhcp etc etc

---

### Post by blueridgedog on 2008-01-15
Can you post the output of 

cat /etc/group

and 

sudo cat /etc/group-

So I and others can see the group ID's and the exact duplication. I do take your word for it, but I am curious to see the ID's.

---

### Post by stumped on 2008-01-16
Sorry, but I can't now.  I had reinstalled my system before I noticed the problem, and I found a few other things that were also not working right.
I decided that maybe it just didn't install correctly, so I reinstalled it again, and now everything is working perfect so far.
It was just really strange as every time I would go in the users and groups gui and changed a group setting, another group setting would also change at the same time.
Thank you all for your help !!

---

### Post by blueridgedog on 2008-01-16
No trouble.  Sorry we could not figure it out.

---

### Post by stumped on 2008-01-16
I now have edgy completely reinstalled and it has been working great.
I did some update thing that updated parts of firefox and installed the w32codecs and now I am having the same exact problem.  
I can not post the outcome of cat /etc/group and sudo cat /etc/group- because this forum says that I am trying to post 108 pictures and can only post 8.  I don't get that because it is not a picture. I highlighted the outcome of each, copied and pasted here. The forum won't let me post it.  If you can tell me what I am doing wrong I will post it.

---

### Post by blueridgedog on 2008-01-16
Strange.  You are trying to simply copy and past from a terminal as plain text?

---

### Post by stumped on 2008-01-17
Yes, thats all I am doing.  Highlight it in the terminal select copy, come here and paste and I get this error code here.....

You have included 108 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

---

### Post by stumped on 2008-01-17
Sorry to use another post, but, I think this groups problem has something to do with the firefox upgrades for some reason. If I remember right everything worked on the last install until I upgraded the firefox stuff through synaptic just like on this install.

---

### Post by blueridgedog on 2008-01-17
Well, if you can't post it, lets try some questions.

compare the users in

```
cat /etc/group
```

with 
```

sudo cat /etc/gshadow
```

Are the they same?

group is the editable list of groups and gshadow is the root only list of groups that is actually used.  If gshadow is correct, we can remake group from it, but let me know what you see first.

---

### Post by stumped on 2008-01-17
I managed to figure out how to show them to you. See these attachments.
Please note that "craig" is my user account and "anybody" is the name of a second account.

---

### Post by bodhi.zazen on 2008-01-17
Not really seeing duplicate groups.

some groups have multiple members.

all seems normal to me.

---

### Post by stumped on 2008-01-17
I also don't see any duplicates in those. It is in the gui that I see all the duplicates.  Everytime I click on one of the buttons in the gui, duplicates are automatically added for some reason. The more I click on a button, the more duplicates show up.  It always stays the same in etc/group.
Does this mean that only the gui is messed up and it isn't affecting anything that matters?

---

### Post by bodhi.zazen on 2008-01-17
yes

I suggest a bug report : 

How to : [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

	[https://bugs.launchpad.net/distros/ubuntu/+bugs](https://bugs.launchpad.net/distros/ubuntu/+bugs)

Include a screen shot and the above files.

---

### Post by blueridgedog on 2008-01-17
Agree re bug report.  A screenshot would be great.

---

### Post by stumped on 2008-01-17
I will do that.
As a side note, If I edit /etc/group manually, it works. If I edit through the gui, it doesn,t.
Thank you for all your help.

---

### Post by nathanv117 on 2008-01-19
just installed 7.10. same problem with gui.groups. it is duplicating every time you change. after a change, get out and get in. looks alright. i beleive appending problem  after a change.

---

### Post by organica on 2008-02-27
> **nathanv117 said:**
> just installed 7.10. same problem with gui.groups. it is duplicating every time you change. after a change, get out and get in. looks alright. i beleive appending problem  after a change.

Ditto

---

### Post by timjohn7 on 2008-03-24
i'm having the same problem... terminal check there are no duplicates, but in gui, many. (Using Gutsy)

---

### Post by stanz on 2008-03-25
Here too....
GUI shows multiple group entries,
/etc/gshadow and /etc/group show once.

Using Gutsy

:guitar:

---

### Post by stanz on 2008-03-31
Just checking back to see if there's a fix.
I tried to search if a bug was submitted -- with no results.

stumped -- did you report one?

Anyone else?

I'd like to 'clean house' so to say...  ;)



:guitar:

---

