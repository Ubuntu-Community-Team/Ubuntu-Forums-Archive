---
title: "Restricting root (sudo/gksudo)?"
date: 2007-01-11
forum: General Help
---

### Post by urukrama on 2007-01-11
Is there a way to limit the files root (or any user with administrative rights through sudo/gksudo) can access?

Here is the problem: I have computer that I share with others. Almost all of us have administrative rights, but this also means we can always access each other's files very easily. If I just do a "gksudo nautilus/thunar" I can easily access and edit the files of my housemates.

Is there a way to block this -- giving us all administrative privileges, but blocking certain files and folders from root unless logged in as the owner of those files or folders?

I did a search on these forums, but couldn't find anything.

---

### Post by xopher on 2007-01-11
> **urukrama said:**
> Is there a way to limit the files root (or any user with administrative rights through sudo/gksudo) can access?

Here is the problem: I have computer that I share with others. Almost all of us have administrative rights, but this also means we can always access each other's files very easily. If I just do a "gksudo nautilus/thunar" I can easily access and edit the files of my housemates.

Is there a way to block this -- giving us all administrative privileges, but blocking certain files and folders from root unless logged in as the owner of those files or folders?

I did a search on these forums, but couldn't find anything.

Well root/superuser access gives you access to to anything on that whole computer. And the permissions for root can't be changed AFAIK. But you could restrict the users access to eg. just installing applications and updating etc.

---

### Post by Jussi Kukkonen on 2007-01-11
That's not how root/sudo works unfortunately...  You can only limit the programs a user can sudo, not the files he will be able to open (that's quite logical when you think about it).So the real problem is that you all have full admin rights.

I see two solutions:
1. don't give full sudo rights to people (the corporate approach) -- if someone needs to mount arbitrary things, give hime "sudo mount"-permissions, nothing else.
2. start encrypting your data. This is the only way to actually be sure, as even your non-root room mates could just boot in to single user mode and read your stuff. This is a valid suggestion for actual confidential information, but not really for e.g. hiding browsing history or normal emails.

---

### Post by urukrama on 2007-01-12
Yeah, I was afraid it would be like this. A pity... :(

---

### Post by urukrama on 2007-01-24
Sorry to dig this up again, but I'm still interested in it, and don't want to admit it isn't possible. :rolleyes: 

What about what is suggested in another [post]("http://ubuntuforums.org/showpost.php?p=1325182&postcount=12")?

> What about what I suggested? You could have someone set the root password so you wouldn't know it. Then, if possible, edit the sudoers file to disallow sudo users access to the content filter configuration.

(The thread is about something else, internet filtering, but these posts touch on what I want to acchieve)

Would that work? I don't know how or where to edit my sudoers files, but could I do it like that, so that we all can install/remove applications, mount drives and media, etc, but still not view each others's /home directory?

---

