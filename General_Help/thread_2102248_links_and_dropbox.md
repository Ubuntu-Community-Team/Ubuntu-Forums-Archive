---
title: "links and dropbox"
date: 2013-01-06
forum: General Help
---

### Post by tc101 on 2013-01-06
I made some links to files in a folder.  When I added that folder to drop box, the links contained duplicate copies of the files linked to.  Have you had this problem?  Do you understand what is happening?  Is there a solution?

---

### Post by Paddy Landau on 2013-01-06
Please would you explain more clearly. A link cannot "contain" a file, so I do not know what you mean.

---

### Post by tc101 on 2013-01-06
> Please would you explain more clearly. A link cannot "contain" a file, so I do not know what you mean


Sorry.  I understand your confusion.  This is hard to explain.

I mean that after connecting to dropbox, the file which had been a link was changed to a duplicate of the file linked to.

In the "type" column of the file manager, before connecting to drop box, Link_to_notes was shown to be a link and the size was 32 bytes.  After connecting to drop box, Link_to_notes was shown to be a plain text document and the size was 18.7 kB, the size of the notes file.

---

### Post by Paddy Landau on 2013-01-06
Ah. I think what is happening is that DropBox does not recognise links. By adding the folder to DropBox, you are asking for the *link* — not the *file* — to be backed up.

I rather suspect that DropBox is not aware of this, sees it as a file, and synchronises the file, thereby replacing the link. (I have never used links with DropBox, so I cannot be sure.)

I suggest that you put the actual file within the DropBox folder, and link to it from wherever else you need the link.

For the same reason, I would suggest that you use normal symbolic links (which is what you are already using) and avoid hard links.

Try this, and see how well it works for you.

---

### Post by tc101 on 2013-01-06
> use normal symbolic links (which is what you are already using) and avoid hard links.


What is the difference?  I just right click on the file and select "Make Link".  I have never heard of symbolic or hard links.

---

### Post by tc101 on 2013-01-06
OK, I did a google and read a little about hard vs symbolic links.  The deep tech answer is beyond me.  I am a light weight user.  The only thing I am curious about is what kind of link I create when I right click on the file and select "Make Link".

---

### Post by Paddy Landau on 2013-01-07
Your method creates symbolic links, so you're already doing it the best way (for you).

A symbolic link is equivalent to Windows short-cuts.

Don't worry about hard links, if you're new to all this.

Try the way I suggested (putting the files into the DropBox folder and using links outside it) and let us know if your problem has been solved or if you still get problems.

---

### Post by tc101 on 2013-01-07
It seems to work if the link is not in dropbox.  I'll let you know if there is any problem.  I'm going to see if ubuntu one has a similar problem to dropbox, but I doubt it will.

Thanks for your help.

---

### Post by Paddy Landau on 2013-01-08
> **tc101 said:**
> It seems to work if the link is not in dropbox.  I'll let you know if there is any problem.  I'm going to see if ubuntu one has a similar problem to dropbox, but I doubt it will.

Thanks for your help.
Please let us know your results with Ubuntu One.

DropBox, Ubuntu One, SpiderOak and the like all have to cope with Windows and Mac in addition to Linux, so it may not be possible to deal sensibly with links — what happens if you synchronise with a Windows box, or even another Linux box where the link will point nowhere?

I imagine that is the reason why DropBox fails to synchronise the links as you would have expected. Links can sensibly be synchronised only where the relevant directory structure is equivalent, and DropBox cannot guarantee this.

Please also [mark your thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others with the same question.

---

