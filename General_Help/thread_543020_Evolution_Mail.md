---
title: "Evolution Mail"
date: 2007-09-04
forum: General Help
---

### Post by gavinjb on 2007-09-04
Hi,

I have recently moved to Ubuntu as my Primary OS and am looking at EMail clients and so far the only system I have found any where near as powerful as Barca on Windows seems to Evolution, but after looking at it I cant find any way of doing a couple of operations.

1. Is it possible to export mail from Evolution, if I decide at a later date that I prefer Thunderbird....

2. Is it possible to backup my Mail regularly (on Windows I used a client called Barca and I had a script that once a day backed up all mail boxes to a particular folder).  If Evolution can't do this is there any other tool/or can a script be written.

Thanks,


Gavin,

---

### Post by cmnorton on 2007-09-04
Your evolution mail is alreadyin in mbox format, at least on my system (6.06 LTS). I have not imported into Thunderbird, but cannot imagine it would not be able to import from mbox. The only problems I have had are Outlook to/from mbox format.

---

### Post by ayoli on 2007-09-04
I think thunderbird can import mail from evolution mailboxes (you just have to give paths)
I dunno a tool/script to backup but this is easy to copy your mail dir to a folder /usb deive or whatever, just copy the .evolution dir that is in your home dir:
```
/home/<YOUR8USERNAME>/.evolution
```
do not forget the leading dot (which means hidden folder on *nix systems. you can show hidden folers/files by hitting CTRL+H in nautilus).

---

### Post by gavinjb on 2007-09-08
Thanks, 

I have used this to create a regular backup of my mail.

One more question, I have installed popfile to help classify my email, but I am trying to create a filter to move all mail classified as junk to teh junk folder but evolution wont let me select the junk folder, it seems I am limited to only select folders I created, how can I get around this or is the easier solution going to be Thunderbird.


Thanks,


Gavin,

---

### Post by ayoli on 2007-09-08
check out this : [http://ubuntuforums.org/showthread.php?t=99603&highlight=evolution+spamassassin](http://ubuntuforums.org/showthread.php?t=99603&highlight=evolution+spamassassin)

---

### Post by gavinjb on 2007-09-13
Thanks, but not sure if this is what I want, as all I want to do is tell Evolution when X-Text-Classification head equals Junk to move message into Junk Folder, I can setup the first half of this fine, but Evolution just wont let me move mail to the Junk folder.

I really dont want to use Evolutions Junk Mail handler as from previous experience with in built Spam Filters from Outlook to Thunderbird to Barca, I have found that none can compete with popfile once trained correctly.


Thanks,



Gavin,

---

### Post by gavinjb on 2007-09-13
I think I might have figured it out, only problem is it isn't working, I have set the following

Specific Header X-Text-Classification Is Junk The Move To Folder TEST

I have changed the Then from Set Status to Junk as this wasn't working and I wanted to check what was not working, and it seems to be that for some reason Evolution is not recognizing the header, if I try the equivalent in Thunderbird, it works fine, can you please help.

For reference when I look at the header it is as follows 
```
X-Text-Classification: junk
```


Thanks,


Gavin,

---

