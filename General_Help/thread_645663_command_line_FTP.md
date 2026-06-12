---
title: "command line FTP"
date: 2007-12-20
forum: General Help
---

### Post by petay on 2007-12-20
Hi

I am trying to get the ls command within command line FTP to return something more useful for me.

i have a folder on the ftp with 3000 files on there, all with no extention. i then process the file, then add an extention to the file so that it is clear it is finished with. the files come off the server once they reach 28 days of age and they need to stop where they are for tracing purposes. Therefore i need ls to find everything without a dot in it. so in this list

on1.old
on2.old
on3
on4

i only want ls to return

on3
on4

i have spent all day looking on google and tried just about everything i can think of.

best google could find was 'ls *~*.*(.)' but that returns nothing

anyone know how to do this???

thanks

Pete

---

### Post by stylishpants on 2007-12-20
This will do what you want in bash:

```


# List all files with no . in their name
ls -d !(*.*)

# Another way
ls | perl -ne 'print unless /\./'


```

I have no idea if these commands will work from within your ftp client.  They might work if run from the ! command that shells out from ftp.

---

### Post by petay on 2007-12-21
im actually running it from within a program i am making. It uses a component for the ftp comunications structured thus,

ftp.read(destinationList,searchPattern);

if i can find a wildcard search or something that will get me what i need it should improve my program no end!!!

@stylishpants - thanks for the ideas, but the server does not like them :(

ftp> ls -d !(*.*)
Error opening local file !(*.*).
> !(*.*):Invalid argument

ftp> ls | perl -ne 'print unless /\./'
Usage: ls remote directory local file.
ftp>


maybe FTP can not do this???

Pete

---

### Post by oscarsfriend on 2007-12-21
Well the man page for ftp seems to say that ls is very basic and (possibly) only supports the -l option and no wildcards.  However the man page for sftp says its ls command is much more advanced and supports wildcards and various options.  Also sftp has the advantage of being secure enough to use in the wild.

---

### Post by stylishpants on 2007-12-21
> **petay said:**
> im actually running it from within a program i am making. It uses a component for the ftp comunications structured thus,

ftp.read(destinationList,searchPattern);

if i can find a wildcard search or something that will get me what i need it should improve my program no end!!!

@stylishpants - thanks for the ideas, but the server does not like them :(

ftp> ls -d !(*.*)
Error opening local file !(*.*).
> !(*.*):Invalid argument

ftp> ls | perl -ne 'print unless /\./'
Usage: ls remote directory local file.
ftp>


maybe FTP can not do this???

Pete

Oh, there is absolutely no possibility that ftp itself can do this.  In your example output you are using ftp's built-in "ls" command, which is very basic.  It does not support any of the advanced file substitution operators that bash does, not even most of the basic ones.

You should be trying to  talk to a bash shell directly, through your ftp client's ! command.

Try it like this:
```

ftp> !ls -d !(*.*)

```

Another way:
```

ftp> !bash
bash> ls -d !(*.*)
file1 file2 file3 dir1 dir2
bash> exit
ftp>

```

I don't have an ftp server available, so I can't actually test these with the 'ftp' program.  However, I did test them with lftp.  The first one didn't work, but the second one did.

It's worth using a more powerful client like lftp or ncftp anyway, even apart from this problem.  They provide many nice little features (like tab completion and bookmarks) that you will wonder how you ever lived without if you're a frequent ftp user.

oscarsfriend: sftp is great, but it cannot use the ftp network protocol.  It only uses the ssh protocol under the hood, so it cannot connect to an ftp server.  lftp supports both.

---

