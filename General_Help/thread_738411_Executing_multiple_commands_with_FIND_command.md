---
title: "Executing multiple commands with FIND command"
date: 2008-03-28
forum: General Help
---

### Post by shaggy999 on 2008-03-28
Let me explain what I'm doing. I am converting a bunch of audio books that were originally stored in FLAC format to Ogg-Vorbis. There's a lot of files so I use the following command to find all the flac files:

```
find . -iname *.flac
```

This grabs all my flac files. I then want to execute two commands on each file:
1) convert from flac to ogg
2) Remove the original flac file but ONLY if conversion was successful

If I was performing this command on an individual file I could easily do this:

```
flac2vorbis file && rm file
```

So I look into the find command's features and see that it has a -exec function. So then I came up with this:

```
find . -iname *.flac -exec flac2vorbis {} && rm {} \;
```

Unfortunately, bash intercepts the && and splits the commands into two at that point. So I put a backslash before each & to pass it through to the find command. But that doesn't work because && is a bash-related command and the -exec option is being executed directly. So instead && and rm are passed as attributes to the flac2vorbis command as filenames.

My current solution is this:

```
find . -iname *.flac -exec flac2vorbis {} \; -exec rm -v {} \;
```

However, I don't have any reason to believe that the second command is conditionally executed. My concern is that if flac2vorbis fails (or I hit ctrl-c because I have to shutdown the laptop) that the rm command will execute when I'm not ready to execute. The reason why I have concern for this is because it appears that when I hit ctrl-c while this command is in operation it doesn't kill the entire find command, it just kills the most recent exec command and then moves onto the next file.

I know I could just write two identical find commands and execute one after the other is finished processing, but I want to do it all in one command because linux is cool that way. :) The other problem with that is that if I hit ctrl-c and then re-run the command later it will re-process the flac files I've already converted if I don't delete them immediately after conversion.

Anybody have any ideas?

---

### Post by lloyd_b on 2008-03-28
Maybe this:
```
find . -iname *.flac -exec sh -c "flac2vorbis {} && rm {}" \;
```

The "sh -c" causes the invocation of a sub-shell, which should correctly handle the "&&" for you.

Lloyd B.

---

