---
title: "How to exclude files/folders when using chmod"
date: 2014-10-15
forum: General Help
---

### Post by Deuce1912 on 2014-10-15
Hello all,

I am trying to chmod a directory in my server and exclude specific files/folders.  I have tried --exclude, however, that doesn't seem to work.  I've searched the internet and saw many commands and different ways to do it, but it didn't make sense to me.  I was wondering if anyone here with a little know how would be able to enlighten me in the matter.

I'm trying to exclude file1 from my ftp directory.  

```
chmod -777 -R /ftp (minus file1)
```

How would I go about this?

Thanks in advance,

-Deuce1912

---

### Post by TheFu on 2014-10-16
Using 777 is almost always a terrible, terrible, terrible, terrible x1000 idea.  There is almost always a better set of permissions to be used.  For example, disable read, but leave execute and write access for public FTP update areas.  That way people can upload, but not know what is there.

Plus FTP is sooooooo 1980s.  [sftp is almost always a better choice]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp") unless the intent is to share the entire OS, files, everything on the box. 

Ok - with that all said, there are a few times when ftp **is** the best answer, so I would do it this way:
```
chmod -R 777 /ftp
chmod 444 /ftp/path-to-that/file-that-you-want-different-permissions-for
```

BTW - we don't have to use the octal codes for permissions.  symbolics are easier to remember and use.
```
chmod -R ug+rwxs,o+wx,o-r /ftp
```

and don't forget about groups for use with sftp.

---

### Post by Deuce1912 on 2014-10-16
> **TheFu said:**
> Using 777 is almost always a terrible, terrible, terrible, terrible x1000 idea.  There is almost always a better set of permissions to be used.  For example, disable read, but leave execute and write access for public FTP update areas.  That way people can upload, but not know what is there.

Plus FTP is sooooooo 1980s.  [sftp is almost always a better choice]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp") unless the intent is to share the entire OS, files, everything on the box. 

Ok - with that all said, there are a few times when ftp **is** the best answer, so I would do it this way:
```
chmod -R 777 /ftp
chmod 444 /ftp/path-to-that/file-that-you-want-different-permissions-for
```

BTW - we don't have to use the octal codes for permissions.  symbolics are easier to remember and use.
```
chmod -R ug+rwxs,o+wx,o-r /ftp
```

and don't forget about groups for use with sftp.

I should have been more clear, I am using sftp, the directory goes /sftp/ftp/files.  Basically what your saying is chmod the entire directory I'm trying to change and then do a second chmod to that specific file to keep it what I want it to be?  

Thanks,

-Deuce1912

---

### Post by TheFu on 2014-10-16
With sftp - then definitely DO NOT USE 777!
Put all the accounts you want to write to a specific directory into the same group, make the group "sticky" on the directory with "w" access and either allow or do not allow "r" depending on the purpose of the upload area.

Yes - sometimes running more than 1 chmod is the easiest solution.  If there is more than 1 file or a pattern, I might use a **find** command instead for part of the chmod .... just depends.  Best to do the directories first most of the time.  Don't forget about the symbolics - they have many more options like the capitals which retain permissions if they are/were already set, but don't change if they weren't (or something like that). RTFM carefully for more details.

---

### Post by HermanAB on 2014-10-17
To give a tip about the original question, you can use 'find' with the 'exec' option to be more specific about whatever a command should act on.

---

### Post by col48 on 2014-10-17
Just an idea, if you are nervous about the effect of what you might do (eg if it could expose private files to public view/hack)

1. Create a full fresh copy of the folders you want to change
2. Do all the chmod changes to the fresh copy (perhaps using a bash script so as to be certain of the exact commands)
3. See what effect you have had on the fresh copy

Then either make the changes to the real thing or go back to stage 1.

---

