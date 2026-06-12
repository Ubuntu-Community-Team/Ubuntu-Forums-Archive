---
title: "Add sudo access for specific command"
date: 2012-11-27
forum: General Help
---

### Post by NertSkull on 2012-11-27
I know how to add a command to the sudoers file so it doesn't need a password.  Can this be done with a specific command on a file.

I want to allow someone to change ownership "sudo chown -R /path/to/directory" of a directory, but ONLY that directory.

So I don't really want to allow all of chown to be accessible.  But only to chown a specific directory.

So can I do something like this in visudo?

```
username ALL=NOPASSWD: /bin/chown -R $USER:$USER /path/to/directory
```

Is that doable?  I'm getting an error when I do it.  Is there a way?

---

### Post by NertSkull on 2012-11-27
Ok I'm close.  You have to first set an alias in the sudoers file, and then allow that alias to be run.  And you have to comment out the colon.  Also, for me, the alias had to be all in caps. So this is what I now have in my sudoers.

```
Cmnd_Alias FIX_ALIAS=/bin/chown -R nertskul\:nertskull /path/to/directory

nertskull ALL=NOPASSWD:FIX_ALIAS
```

If I do that, I can then run this and everything works fine.
```
sudo chown -R nertskul:nertskul /path/to/directory
```

So, my question now is: is there a way to keep the environment variables safely.  I know at the top it says it resets them (??).  But basically I want this instead

```
Cmnd_Alias FIX_ALIAS=/bin/chown -R $USER\:$USER /path/to/directory
```

But the $USER isn't recognized.  I only have two users here, so I could set up to alias commands.  But I feel there should be a better way, but without totally compromising security.

Any thoughts?

---

### Post by StinkySQL on 2012-11-27
I've been working on a security limitation conundrum myself. The approach I've taken is to create a group. I add the user to that group, and then change the group ownership and rights to the directory specifically. 
I don't have to sudo them at all this way - which makes me feel safer. I also expect it to be a lot less administrative work in the future because I'll just add and remove users from the group.

SS

---

### Post by NertSkull on 2012-11-28
Yeah, I initially wanted to do something like that.  Unfortunately, the program that uses my directory changes the owner, group and permissions to the current user each time it is run.  So then when the 2nd user wants to run it, they can't because the directory is now owned by the 1st user.

So normally I think that would probably be the way to do it, but in this case it doesn't seem to work.

---

### Post by rubylaser on 2012-11-28
The easiest way to fix this would be to modify your program to chown the directory when it's done running, or to set it to run as a specific user/group so that permissions are consistent.  If that's not possible...

A couple questions:
1. Does your program run at a specific time via cron? If so, you could easily just chown the directory after it runs.
2. If is not run at a specific time, you could use inotify coupled with a shell script to chown the directory every time a change is detected..

---

### Post by LewisTM on 2012-11-28
You could solve that problem with Access Control Lists, which grant user/group permissions independent of ownership. You need to be the owner or root to change ACLs.

This command would grant both users read-write and execute (for programs and dirs) permissions to your tree:
```
setfacl -R -m <user1>:rwX,<user2>:rwX </path/to/directory>
```
Package eiciel offers a GUI for managing ACLs, although it won't perform any recursive operation.

Cheers!

---

### Post by JKyleOKC on 2012-11-28
> **NertSkull said:**
> And you have to comment out the colon.The backslash doesn't "comment out" anything; it's called an "escape" character in that it hides the following character from being interpreted on the command's first pass through the shell processor, saving it to be seen on the next pass.

The "$" character, like the colon, has special meaning to the shell processor and that may be why your attempt to use environment variables here failed. While I've not tried this, perhaps escaping both "$" characters will make things work as you want, like this:```
Cmnd_Alias FIX_ALIAS=/bin/chown -R \$USER\:\$USER /path/to/directory
```Let us know if this does the trick!

---

### Post by NertSkull on 2012-11-28
Thanks everyone, I've got some good things to try tonight.

JKyleOKC: Good to know the proper terminology, thank you.

I tried also escaping the $ sign as well, and that didn't work.  

rubylaser: It doesn't run by cron.  But I'm going to look into the inotify suggestion, that seems promising.

LewisTM: I also will look into this.  I do have owner permissions.  So maybe this would be the easiest.  I didn't know you could apply permissions to single directories.

Thanks everyone, those are good places to try.  I'll let you know what happens when I get home tonight to try it.

---

### Post by rubylaser on 2012-11-28
I would use LewisTM's suggestion.  That should work well and is very easy to implement.

---

