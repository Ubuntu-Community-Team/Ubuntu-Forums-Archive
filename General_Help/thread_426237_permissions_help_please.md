---
title: "permissions help please"
date: 2007-04-28
forum: General Help
---

### Post by likwid on 2007-04-28
Actually, no it didn't but read on anyway, please......

When i use nautilus, or other applications such as ktorrent, to create a file, how can i set default permissions to group read write. It seems a simple question but i have not found the answer in weeks. The reason i wish for such permissions is for samba networking.

umask doesn't work
chmod g+s doesn't work

I could link countless theads on this forum that were never solved some from two years ago. Can someone please help me out, or tell me that this simple thing is somehow not possible.

---

### Post by Theimon on 2007-04-28
By using a title like that you're not making yourself popular. Use normal subjects with a clear summary of the problem. Not some useless rant, people don't like that and would probably stop helping others.
I know I would....

---

### Post by KrazyPenguin on 2007-04-28
Please delete this post!!!

---

### Post by likwid on 2007-04-28
Thanks for your help..

To be honest i don't couldn't care less if it makes me unpopular, I just want a simple question answered. Having found previously that asking questions about file permissions gets zero attention, i thought this would be the rational thing to do. 

Reading my post, i can't see where you interpret me as ranting.

---

### Post by Theimon on 2007-04-28
By unpopular I mean, people will not help you. It's a basic part of (n)etiquette you obviously fail to understand. When you ask for other peoples help through a forum you should make a to-the-point subject with a short and clear summary of the problem you are experiencing. This not only counts for this forum but practically all forums on the web.
Maybe your subject fits perfectly in some off-topic subsection of the forums but it seems to me you came here looking for help.
At the greater part of the forums I attend, moderators usually close these kind of topics immediately.

---

### Post by likwid on 2007-04-28
Don't worry, i understand that already, it was the part about me ranting that i questioned.

As i said already, posts about file permissions tend not to get answered so i tried another approach.

[Here's]("http://ubuntuforums.org/showthread.php?t=396279") an example of such.

---

### Post by ashz on 2007-04-28
were u ranting before or after u edited ur post?

i did know the answer but somehow my community spirit seems to have run away along with it!!

and as a person who does help people, i dont like it when people dont say thank you after i have helped them its only right that they do, i put their names down in a little box in my head labelled (removed), which means i wont be helping them again, guess whos name im adding to that list, not because u didnt say thank you but because of all the idiots who search google with the words ubuntu and virus and find ur post and then moan at me saying ubuntu has a virus!! (because they wont read the whole thing)

---

### Post by likwid on 2007-04-28
I can clearly state that no ranting has been edited from my posts.

Right clicking on a folder won't work if you're not the owner, and i want to change default behaviour . 

I understand your point about search engines and would be happy for staff to edit the topic title.

---

### Post by josephus on 2007-04-28
anyway back to the original post.

a quick search turned up a couple of relevant pages - first what version of ubuntu are you using?  nautilus seems to ignore umask settings in earlier versions of ubuntu.  

[https://launchpad.net/ubuntu/+source/nautilus/+bug/88994](https://launchpad.net/ubuntu/+source/nautilus/+bug/88994)
[https://launchpad.net/bounties/nautilus-ignores-umask](https://launchpad.net/bounties/nautilus-ignores-umask)

edit/create ~/.gnomerc and add 

```
umask <permissions number>
```

tried it in feisty and it works.

---

### Post by ashz on 2007-04-28
i saw those as well though i thought umask was used to reduce permissions

---

### Post by josephus on 2007-04-28
umask sets the maximum permission level that an application can set when creating a file.

the numbering system with umask is weird.

---

### Post by likwid on 2007-04-28
Thank you very much for the help. :)

On the pc (server) i'm running 6.06 but checking now by sharing a folder from my workstation and creating gnomerc as described does indeed work. This is brilliant news, although i wasn't planning on upgrading the lts i'm happy to if it fixes this long term annoyance of mine.

I'm sorry for the stance but understand this was borne from very much frustration. I am very much in love with ubuntu, and the switch to the open source community. The more i learn, the better it gets. You have to admit it can be a difficult transition that would test anyone's patience.

If i might request that the staff do edit the thread title, it would be appreciated. I'd do it myself (see my previous edit) but for the fact that thread tools don't allow this.

---

### Post by ashz on 2007-04-28
if i read it right the bug is still in edgy, but has been fixed in feisty.

---

### Post by likwid on 2007-04-28
Yes, this does seem to be the case.

---

