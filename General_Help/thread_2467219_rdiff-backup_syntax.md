---
title: "rdiff-backup syntax"
date: 2021-09-19
forum: General Help
---

### Post by Old Jimma on 2021-09-19
Hello Ubuntuers:

I've had a few failures with using rdiff-backup... and so, I'm asking for some clarification on this forum. Thanks.

What I seem to have learned form my investigation are that
[LIST]
[*]it is a good idea to exclude everything first (That's TheFu' suggestion),
[*]then identify the other things you want included (That's TheFu's suggestion).
[*]
[/LIST]

These ideas 
[LIST]
[*]seem to originated from TheFu, 
[*]seem quite reasonable, and 
[*]provides a conceptually simple way forward in implementing rdiff-backup, 
[*]given that its manpage has 538 lines of text, and that starting point is not suggested elsewhere.
[*]
[/LIST]


I've read the 
[LIST]
[*]the man-page,
[*]other documentation on rdiff-backup at [https://rdiff-backup.net/]("https://rdiff-backup.net/"), and
[*]rdiff-backuup discussion group chats, including what's on the forums.
[*]
[/LIST]


What's not clear to me is  
[LIST]
[*]how to tell rdiff-backp where the "include-globbing-filelist" file is located, 
[*]how to properly specify the ownership characterisitcs of the "include-globbing-filelist" file.
[*]
[/LIST]

There are other issues:

My "include-globbing-filelist" looks like this:

> 
/home/mortal/Desktop
/home/mortal/Documents
/home/mortal/Music
/home/mortal/Pictures
/home/mortal/Videos
/home/mortal/Trash


I've seen examples of "include-globbing-filelist" that have unexplained notations (like a "+" and "-") that precede each entry. Material I've read indicate that entries in the "include-globbing-filelist" can include stuff you want (maybe lines with a preceding"+") and stuff you don't want (maybe lines with a preceding "-")... but this is not made explicit.


The manpage, discussions, documentation do not clarify things that may be important issues: there are chats where this is a main topic of concern.

So, I'd like to ask how to do that.

Here is my rdiff-backup command:

> 
rdiff-backup --exclude-special-files --include-globbing-filelist **/path-to-include-list/include-list**         [email]personname1@host1.foo[/email]::/home/rattooth    /mnt/personname2



Here are my questions:
[LIST]
[*] since the entries in my "include-globbing-filelist" include only the stuff I want, should each line be preceded with a "+"?
[*]is an explicit specification of the include list location like the one I've specified acceptable for rdiff-backup?
[*]what permissions for the "include-globbing-filelist" file should be specified in a chmod command so that rdiff can and will read it? E.g, should root be the owner? Or, should I be the owner? How should the access for that file be modified with a chmod command?
[*]
[/LIST]


Thank you,
Old Jimma

---

### Post by CharlesA on 2021-09-20
I don't know the answer to your question about the glopping-filelist, but the last time I used rdiff-backup was in 2013 or 2014.

This was what I used:
```
/usr/bin/rdiff-backup --print-statistics --terminal-verbosity 5 --exclude /mnt/array/Steam --exclude /mnt/array/lost+found --exclude /mnt/array/proxmox /mnt/array/ /mnt/fullbackup/rdiff
```

/mnt/array is the source and /mnt/fullbackup/rdiff is the destination. You can also use user@hostname:/path/to/dest for remote destinations.

It looks like globbing only applies to includes with special characters in the name such was "*" based on what I see here: [http://rdiff-backup.nongnu.org/examples.html](http://rdiff-backup.nongnu.org/examples.html). based on that, I do not believe you need to use globbing with your folder list nor do you need to add the +.

> 
[LIST]
[*]rdiff-backup can also accept a list of files to be backed up. If the file include-list contains these two lines:
[/LIST]

```
    /var
    /usr/bin/gzip
```

Then this command:

    ```
rdiff-backup --include-filelist include-list --exclude '**' / /backup
```

would only back up the files /var, /usr, /usr/bin, and /usr/bin/gzip, but not /var/log or /usr/bin/gunzip. Note that this differs from the --include option, since --include /var would also match /var/log.

[LIST]
[*]The same file list can both include and exclude files. If we create a file called include-list that contains these lines:
[/LIST]

```
    **txt
    - /usr/local/games
    /usr/local
    - /usr
    - /backup
    - /proc
```

Then the following command will do exactly the same thing as the complicated example two above.

    ```
rdiff-backup --include-globbing-filelist include-list / /backup
```

Above we have used --include-globbing-filelist instead of --include-filelist so that the lines would be interpreted as if they were specified on the command line. Otherwise, for instance, **txt would be considered the name of a file, not a globbing string.


---

### Post by Old Jimma on 2021-09-20
Thanks, CharlesA:

I'll give these things a try.


BTW, I read the manpage! And it seems to answer all my questions.

Specifically, lines 454-462 address all  of my issues. They say this:
> 
      For example, if the file "list.txt" contains the lines:

              /usr/local
              - /usr/local/doc
              /usr/local/bin
              + /var
              - /var

       then "**[COLOR="#FF0000"]--include-filelist list.txt[/COLOR]**" would include /usr, /usr/local, and /usr/local/bin.  


What this means is that if you list the files and/or directories in a file called **list.txt** and that file is in the directory called **/path**, you should either
[LIST]
[*]issue a "**cd /path**" before issuing the rdiff-backup command that uses "**--include-filelist file.lst**" , or
[*]specify it this way: "**--include-filelist /path/file.lst**" as a part of the rdiff-backup command.
[*]
[/LIST]

Further, the manpage seems to imply that each line in the file.lst file should be preceded by either a "+" or "-" to indicate whether a file/folder is to be included or not, respectively. ALso, if neither "+" nor "-" is indicted.. the "+" i(ie, includsion) s implied.

I'll test this out. If it works... as evidenced by doing and rdiff-backup and then restoring stuff successflly, I'll report things here, indicate what works, then close this post.

Old Jimmy From the Old Country

---

