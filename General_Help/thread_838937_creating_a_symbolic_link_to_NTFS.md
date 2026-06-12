---
title: "creating a symbolic link to NTFS?"
date: 2008-06-24
forum: General Help
---

### Post by Ck.asdf on 2008-06-24
Hello, I dual boot Windows XP and Ubuntu 8.04
I just recently found out about "junctions" in Windows, which are symbolic links in Linux, which allows me to pretty much name folders what I want, organize them as I'd like, etc, as long as the original folder is pointing to the new folder.

I started with this when I got tired of "Documents and Settings" and decided to see if I could get XP to act like Vista (which acts like Unix), so that I could use "Users" instead of that big long folder name.  I found a site that explained junctions, and have played around with them a bit.

I have it so that my WinXP user profile is located on a separate "Storage" partition, while the symbolic link points to that directory.



My question is, when in Ubuntu, can I create a symbolic link to the NTFS partition, so all the data I save will end up on it instead of the Ubuntu partition, so that I can reinstall with ease, if necessary?

My plan would be whenever something wants to save to "/home/ck" it would store it to "/mnt/storage/profiles/ubuntu/ck" or something similar.

---

### Post by diaa on 2008-06-24
Yes, that's possible and I'm already using a symbolic link to a NTFS drive to share my pidgin settings between Windows and Linux
You can make a symbolic link using your desktop environment(details are environment-specific) or from the command-line using the following command
```
ln -s source destination
```
note that for folders the destination folder shouldn't exist otherwise you'll get the symbolic link inside the destination folder.

---

### Post by Ck.asdf on 2008-06-24
Thanks for the quick reply ... not sure it worked though.

EDIT:
Never mind, I realized my mistake; it works now! :)

---

### Post by diaa on 2008-06-24
sorry for this, a bad typo, I fixed it :)

---

### Post by molotov00 on 2008-06-24
Just make sure your NTFS partition is mounted at startup (i.e. in /etc/fstab). Otherwise apps will try to write to /home/ck and the link destination won't exist, yet.

I also think it's funny that Windows JUST implemented junctions. I didn't know that's what they were called or that they existed until I read your post. It's one of the features that -- when I first learned about them many years ago -- I always thought should exist in Windows.

---

### Post by Ck.asdf on 2008-06-24
> make sure your NTFS partition is mounted at startup
Yep, I went and found out how to do that after I asked ... I've done it before, but I can never remember the file (fstab) or the process, but Google's there for me. That's one problem I know is readily available for answer.

> I also think it's funny that Windows JUST implemented junctions.
Apparently, it's been around in some form or another since Windows 2000, but as you mentioned, I've never heard of the term "junction" (in this context) until tonight.

I knew it exists in Vista, though, because if you look at the file structure, it shows in the root of C:\ both "Users" and "Documents and Settings" and the latter folder looks kinda funny, to say it's a symbolic link or junction.  That is there so if people try to install a program that thinks it's using XP's file structure, it will successfully find the right place.

I kept in my mind the fact that there was a pointer in Vista, and today while in XP, I thought, "you know, I'd like to have my file structure look like Vista's" so I did a search, and found a site that shows how to use the junction program, and so I added a pointer called "Users" to point toward the other.

After experimenting for a while, I realized the potential ... have one user profile for linux AND windows, in one location that won't be formatted in the event of an OS reinstall, and that would make life so much easier!  the only thing to do after reinstall would be to re-create those links, and everything would work again. ^_^



Oh, and if you're interested in using Junctions in Windows XP, check out this site:
[http://derekslager.com/blog/posts/2007/03/emulating-vistas-user-directory-structure-on-xp.ashx](http://derekslager.com/blog/posts/2007/03/emulating-vistas-user-directory-structure-on-xp.ashx)
This is what I mentioned above.

A word of warning, though, junctions may behave unexpectedly in Windows XP, so read the warnings on this wiki:
[http://en.wikipedia.org/wiki/NTFS_junction_point#Windows_XP_Professional](http://en.wikipedia.org/wiki/NTFS_junction_point#Windows_XP_Professional)

It may be best to experiment with useless data to figure it out before putting your personal important stuff to the test.

---

### Post by Wisp558 on 2008-11-16
Wait... Where would you set up this neutral user-space, with the user data from both operating systems? Your storage partition?

Also, I really like the sound of what you're saying, but could you detail in a tad more noob-friendly process. I really would like to set something like that up...

Sorry for Reviving a dead topic...
~Wisp

---

### Post by sokera on 2008-12-22
Hey guys,

I didn't want to open new topic that pretty much asks for the same.

I have a music folder in my XP installation and I want to create a symbolic link to ** home/myUser/Music ** folder so that I don't have to copy everything.

The thing is that even if I type ** sudo ln -sf source destination ** the shortcut can't find the folder to the XP specified.

I can access my XP installation going to ** /windows **.

Does anyone have any idea why is that?

Thanks!

---

### Post by sokera on 2008-12-22
Nevermind. It worked. I have no idea why it worked now and not before since I did the same thing (I only added the verbose function).

---

