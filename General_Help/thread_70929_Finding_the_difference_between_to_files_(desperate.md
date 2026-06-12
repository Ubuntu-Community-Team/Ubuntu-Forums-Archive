---
title: "Finding the difference between to files (desperate)"
date: 2005-10-01
forum: General Help
---

### Post by Panthios on 2005-10-01
Hi all.
First of, you guys are my last hope. I have tried asking on many forums on my own language, but no one can help me.
Here is the deal:
I have a website with phpBB forum running.
The newest mySQL backup file I have (through phpmyadmin) is from the 5th august.
Last night, a member was going beserk and deleted all his posts (around 600 posts).
I want those posts back again, but the backup from 5th august is too old - many other posts from other users will then go lost.
So I figured, that the best solution must be, to take a mySQL backup today and then melt that with the one from 5th august.
You understand me so far?
New backup, from today:
Got ALL the posts, since the start of forum till today - but without the one who gone beserk.
Old backup from 5th august:
Got all the posts from start till 5th august - including many posts of the one who gone beserk.
I tried with diff and diff3 in hope to get something usefull, but nothing yet.
Is it possible to do what I want?
I want to take the lines out of the old backup (5th august) that does not appear in the new backup (from today) and melt them into the new one - not just add them to the end of the backup file, that's no good.
Anyone who can help me?
Im quite desperate :(
And sorry for my bad english, I hope you understand.

---

### Post by Zotova on 2005-10-02
Just to clear a few things up in my head - is the phpbb forum hosted on your computer? Or an isp's server which happens to be using linux? - It shouldn't however really matter too much.

Either way you mentioned phpmyadmin which I have a bit of experience with as I have setup and run several phpbb forums myself.

I would like to add before I start, there is probably a much easier solution than what I'm about to give but this is how I would go around fixing the problem personally:

If you have the space available I'd first setup a blank phpbb forum/database and restore the August backup file to that and make sure everything is working from the backup.

Then I'd access the new database with phpmyadmin and export only the posts table (I'm presuming this user hasn't deleted their account as well?)

What I'd then do is make a complete backup of your current database (just as a backup if this doesn't work). Once you have your complete backup I'd then do this:

Now make a backup of only the posts table in your current database (so you have a backup of all the posts apart from the user who deleted their posts).

Now delete the posts table in your current database and then upload and import the August post table (ie the posts which contain upto August 15th and also include the user who deleted their own posts). 

Once that is done I would then upload the backup we made of the current posts table (ie the posts which are up-to-date but do not contain the user who deleted their posts) - this should then ignore the duplicate posts but add the posts after August 15th to your post table.

You should then have a post table which contains all the data from both the August backup and the current forum.

I hope that makes sense and is of some help to you. I do want to make it clear though that I may be wrong with what I've written above so please do make sure you have a working backup before you try any of that.

---

### Post by Panthios on 2005-10-03
Hi. Thank you for your reply.
I followed your instruction, many many times with many combinations, but it does not have the effect that I want.

For example, there was around 3.700 posts in the phpBB right before some where deleted. Thatfore there should also be 3.700 rows in phpbb_posts.
With the august-backup there is 2.800 rows, and the current-backup there is 3.000 rows.
If I follow your instructions I end up with 5.800 rows all the time.
Im going mad here :confused: 

Hope you or someone else have more ideas for me.
Best regards

---

