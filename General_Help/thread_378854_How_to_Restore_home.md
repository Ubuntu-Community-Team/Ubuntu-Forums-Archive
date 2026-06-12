---
title: "How to Restore /home??"
date: 2007-03-07
forum: General Help
---

### Post by Darko Beta on 2007-03-07
Aww crud.  I had followed the psychocats guide to move my /home to its own partition, but for some reason everything got transferred (files and apps), but my desktop was just like it is on install--no them configurations or anything carried over.  My firefox, too, was like it was brand new--no extensions, bookmarks, etc.  I didn't mind fixing that stuff, but then I opened Amarok and it was the same story--no ratings, playlists, or anything, so I didn't want to have to redo those.

So I decided to follow the instructions to go back to my original /home which I had backed up.  Now I have problems!  I carried out the instructions, and now I can't get into Ubuntu.  Here is the deal though:

The error says, "Your home directory is listed as '/home/username' but it does not appear to exist...

I logged into a failsafe terminal session and cd'ed there, and here's the structure:

home > home_backup > username

So I need to remove the 'home_backup' folder from in-between somehow.  Is the only way I can do this to copy all of the contents from username to home_backup, and *then* get rid of the contents of /username?  I'm not 100% sure I have enough room on the partition--I reduced it because I didn't think /home was going to be on there!

I would greatly appreciate any suggestions.

---

### Post by Darko Beta on 2007-03-07
I guess to make this a lot simpler:

What is a command to remove a folder from the middle of a file path, and still retain the rest of the path?

home/home_backup/username

needs to become:

home/username

with all of the contents of /username preserved.

---

### Post by tribble222 on 2007-03-07
You have a few options.  You could copy the contents of home_backup to home like you said.  Of course you'll want to make sure you have enough space.  If you don't have enough space you could move them instead of copying them but if something goes wrong during the move it could be bad.

I'm not very sure about this one, but perhaps another thing you could do is leave the files where they are and edit your /etc/fstab to mount that directory in /home.

i.e. add a line like

/dev/hdb2/home/home_backup    /home 	   ext3	       nodev,nosuid    0       2

where hdb2 is the partition your home_backup is on.

---

### Post by Dr. Nick on 2007-03-07
You wont technically remove the directory in the middle, but a simple 

[B]sudo cp -R /home/home_backup/username /home/username

[/B]should get it copied back over.

---

### Post by Sef on 2007-03-07
Check out [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by Mr. C. on 2007-03-07
> **Darko Beta said:**
> 
What is a command to remove a folder from the middle of a file path, and still retain the rest of the path?

home/home_backup/username

needs to become:

home/username

with all of the contents of /username preserved.

Here's your command.
```

mv /home/home_backup/username /home
```

---

### Post by Darko Beta on 2007-03-07
> **Dr. Nick said:**
> You wont technically remove the directory in the middle, but a simple 

[B]sudo cp -R /home/home_backup/username /home/username

[/B]should get it copied back over.

OK, I see how this works.  I spent some time with man cp...  My partition was very tight, so I deleted the attempt at a new /home partition and resized the original partition.  Now I should be able to copy away.  ::crosses fingers and shuts down live disk::

---

### Post by Mr. C. on 2007-03-07
You DO NOT need to copy the files!

Just move the directory, as I indicated above.

MrC

---

### Post by Darko Beta on 2007-03-07
> **Mr. C. said:**
> You DO NOT need to copy the files!

Just move the directory, as I indicated above.

MrC

I caught that at the last minue MrC.  Thanks.  I did use the mv command, after reading the man mv page so I understand how to do this on my own in the future.  It worked as it should, and my files are now in the right place.

Now, though, I am getting a strange error message when I try to log in:

```
User's $Home/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $Home directory must be owned by user and not writeable by other users.
```

I click OK, and then the session ends before it can get started.  The error message is:

```
Could not set mode 0700 on private per-user gnome configuration directory 'home/username/.gnome2_private/': Operation not permitted.
```

Ugh.  Sounds like permissions problems...  Any suggestions on how to fix this?

---

### Post by Dr. Nick on 2007-03-07
> **Mr. C. said:**
> You DO NOT need to copy the files!

Just move the directory, as I indicated above.

MrC

Yeah, I forgot about this till after I posted. You can use my command above and subsiture cp with mv. The command Mr C. posted should work, may need ti use sudo though

---

### Post by Mr. C. on 2007-03-07
Yes, the problem occurred because you copied the files, which created new files, new ownership, and new permissions.  There is an option to retain ownership, permissions, and access times, but unless you have those original files, its too late for that.  If you do have the original files, just move the bad new directory out of the way and move the old one to the location you want.

It is not a good idea to blindly follow advice here - it is often the blind leading the blind ! :-)

You should own all files in your home directory:

$ chown -R yourusername:yourusername /home/yourusername

Permissions on your home directory can be as open or personal as you want.  You can be the only user to read, write, examine, or you can allow groups or others as you see fit.

If you are the only user, just make them 644 and 755 for directories (you can do everything, group and others can only read/examine).

find /home/yourusername -type d | xargs chmod 755
find /home/yourusername -type f | xargs chmod 644

This will set files and directories back to (most likely) how they were; what isn't perfect, can be changed as you see in those warning messages.

Once you have that completed, here's some Intro to Unix material (see the Coursework section):

[http://cis68a.mikecappella.com/](http://cis68a.mikecappella.com/)

Cheers,
MrC

---

### Post by Dr. Nick on 2007-03-07
I reread it and realized he was using a live cd, I imagine the fact that the live cd is a different owner/group then what he set up may have contributed to part of the problem with permissions somewhere along the way.

You are right though Mr. C, mv is  a better choice then cp, I just prefer cp when possible since the risk of losing files due to things like freezes and power outages is minimized

---

### Post by Darko Beta on 2007-03-07
IT WORKED!  Thanks very much for the help MrC and Dr. Nick.  I understand everything that happened here, except for all of the ownership rules--so I plan to read up on that next.  It is a relief to be back in Ubuntu.  

Note: I was using the live CD just to access the internet/forums only, not for anything else.  I booted into Windows a few times, too... meh.

---

### Post by Mr. C. on 2007-03-07
> **Dr. Nick said:**
> You are right though Mr. C, mv is  a better choice then cp, I just prefer cp when possible since the risk of losing files due to things like freezes and power outages is minimized

That's fine - let's just suggest to others to use the proper options to cp to act in "archive" mode, retaining timestamps, permissions, and ownership.

If safety is your goal, use tar - it is far faster to copy hierarchies.

```

tar -cf srcdir - | (cd destdir; tar -xvf  - )
```

MrC

---

### Post by Dr. Nick on 2007-03-07
Ok, wasnt sure if you tried to copy any files or create/remove partitions with the live cd or not. That can sometimes get you in a bit of trouble since it could change permissions I believe

---

### Post by Mr. C. on 2007-03-07
> **Darko Beta said:**
> IT WORKED!

Of course!  Would you expect other! :-)

Enjoy the learning,
MrC

---

