---
title: "Limited SSH/WinSCP access"
date: 2007-10-04
forum: General Help
---

### Post by StooJ on 2007-10-04
I have an xubuntu fileserver and I connect to it with my laptop when I'm out & about using WinSCP (when I have to use Windows :( )

My dad saw me messing about with it & was impressed, he would like to be able to use WinSCP to upload files to my fileserver, we both work on the same projects so it would be very useful for him to be able to regularly pass on the most recent files.

However, at the moment WinSCP give me complete freedom throughout my xubuntu box. I don't really want my dad to have that.

I also want to script the transfer rather than rely on his endearing ineptitude, so I don't want a sensitive password stored in a flat text file (WinSCP Script)

Is there a way to set up user accounts so that he can only access a single folder? I think it uses SSH settings, but I'm not sure.

I'm relatively inexperience with linux of any kind, so I'm not sure where to look.

Many thanks

---

### Post by scruff on 2007-10-04
Just create your dad his own account on your machine. That will give him access to his own /home/dad directory. If you want to share something else with him, you could create a new group like, sshusers (or something) then issue a 'chgrp sshusers /this/directory', then make sure writes are allowed for group: chmod 775 /this/directory to give him access to that as well.

---

### Post by StooJ on 2007-10-04
> **scruff said:**
> Just create your dad his own account on your machine. That will give him access to his own /home/dad directory.

I think that'll do nicely, since I'm going to script the whole process anyway. However, just a quick question. Although he only has the rights to write to his own home directory, he can still see the entire filesystem.

Would I need to go through the whole installation and remove group read rights from every file & folder to prevent him seeing all that stuff? Or is there a way of emprisoning his account so that he can only navigate around his home directory and nothing more?

(as an aside, I think this is probably in the wrong forum. I'm sorry about that, admins)

---

### Post by scruff on 2007-10-04
No need to do all that. Here's a step by step example (anything preceded by a # is a command) :

Add your dad:
# useradd -m -g sshusers dad

Now his only group membership is to sshusers. 

Quick permissions tutorial. File permissions are set in bits like this:

1 = execute
2 = write
4 = read

So...

There are 3 permissions fields in a listing like this:
```

sean@sullyhome:~$ ls -l 
total 10570
drwx------ 10 sean users      360 2006-06-07 02:32 custom_stuff
drwx------  5 sean users      280 2007-09-19 20:59 Desktop
drwxr-xr-x  9 sean users     1136 2006-09-18 16:44 Documentation

```

The d at the beginning means directory - ignore that for now. The other 9 bits are permissions. First 3 = owner, 2nd 3 = group, 3rd 3 = everyone else. 

If you want to have read/write/and exe permissions you use 7 (4+2+1). If you want someone else to have only read and exe (needed to list dir), you use 5. As you can see, my Documentation directory is rwx by me, and xr by group, and xr by everyone else. To manually set that, use:

# chmod 755 Documentation

Got it?

If you create a folder, say "ssh_share" you can set the group and permissions like this:

```

mkdir ssh_share
chmod 770 ssh_share
chgrp sshusers ssh_share

```

Now you have a file with read/write/execute for both the owner (you) and anyone part of the sshusers group (your dad) can make use of it. Even though he can *see* other directories, he won't be able to access them unless they are set to the sshusers group.

A decent place to stick this might be directly under /home/.

---

### Post by StooJ on 2007-10-05
Aaaah, I get it now!

For some reason I hadn't thought the group attributes were for the group with ownership. Actually, that is a little obvious now... :D

Awesome wee tutorial, scruff. Thanks very much indeed.

Now I need to search the ubuntu documentation for how to change dad's user account so that he belongs to the sshgroup & nothing else.

Thanks again for the help

---

### Post by Endolith on 2008-05-06
> **scruff said:**
> No need to do all that. Here's a step by step example (anything preceded by a # is a command) :

Add your dad:
# useradd -m -g sshusers dad

Now his only group membership is to sshusers.

This seems like what I want, but it doesn't work in Hardy:

> useradd: unknown group sshusers


Also, doesn't this still give them access to the entire filesystem?  I just want them to have access to their own home directory, and I can link in other directories that I want them to have access to.  Is that a sane way to do things?

---

### Post by scruff on 2008-05-07
Not sure about the sshusers group. You can just as well create a new specific group for limiting access like this. man groupadd.

As to your second question, no - he wouldn't get access to the entire filesystem. Read up on permissions and filemodes a bit here:

[http://rute.2038bug.com/node17.html.gz](http://rute.2038bug.com/node17.html.gz)

The short of it is though, that he can access things OWNED by him, other things that are readable/writable/executable by group sshusers, or read/write/execute by **everyone** which should be very little.

---

### Post by hyper_ch on 2008-05-07
Install MySecureShell... create the user for your dad, set the UID equal to yours... limit that user in the MySecureShell config to just that one folder where you want to give him access...

---

