---
title: "rsync question. Can I move files only once?"
date: 2015-12-05
forum: General Help
---

### Post by nzdreamer55 on 2015-12-05
Hello everyone,


I am new to linux but have a VPS that runs ubuntu and a raspberry pi with ubuntumate. Right now I get files put on to my VPS that I need to move to my raspberry pi. I pay for the data that I transfer from my VPS so I want to keep this to a little as possible. I have been able to use rsync to do this. The problem is if I move my local files/change them the next time I run rsync all the files will down load again.


Is there a way to keep a list that rsync can use and not download those files?

---

### Post by SeijiSensei on 2015-12-06
With "rsync -a" only files that have changed should be transmitted.  However you can control the list of files to include with the "--include-from" switch:
```
rsync -av . /path/to/destination --include-from=/path/to/include-list
```
The list can contain "globs" like this:
```

/home/*/mail

```
which would sync only the "mail" subfolder in each home directory.

There is also an equivalent  "--exclude-from " switch as well.

---

### Post by nzdreamer55 on 2015-12-06
I see what you are doing, but I think you might have missed what I need to do.  I don't want to keep 2 folders synced, I want to move files from my VPS.  They will be renamed and moved from the [dest] folder.  They will no longer be in the [dest] folder so when rsync runs, won't it just think that the files are not in the [dest] folder and copy them down again?  If rsync could store the names of the files it moves in a txt file and use this to compare against instead of a path then it would work.

Is there a way to do this?  Is there a way to use a time stamp to say only move files that are 420 minutes old and we could then I could run a cron with it every 4 hours?

---

### Post by SeijiSensei on 2015-12-06
If you run rsync with the "v" option, it will write the list of transferred files to sysout.  You could capture that and create the file you need.

Frankly, I'd find another provider.  For $10/month, you can rent a VM at [Linode]("http://www.linode.com/") with essentially unlimited bandwidth.

---

### Post by nzdreamer55 on 2015-12-06
> **SeijiSensei said:**
> If you run rsync with the "v" option, it will write the list of transferred files to sysout.  You could capture that and create the file you need.

Frankly, I'd find another provider.  For $10/month, you can rent a VM at [Linode]("http://www.linode.com/") with essentially unlimited bandwidth.

THANK YOU so much.  This is the best answer I have found.  That is awesome.  Now I need to learn how to handle sysout to file creation.  Maybe another provider, but it also this solution of creating a list means that I don't have to keep 2 copies of the same data in 2 places.  I get the data that is new down to my local machine automatically and then I can move it and not worry that rsync will redownload it again.

---

### Post by SeijiSensei on 2015-12-06
> **nzdreamer55 said:**
> Now I need to learn how to handle sysout to file creation.

```
rsync -av source destination > /path/to/some/file
```

There will be some additional cruft to remove from the file.  You can use grep for this:

```
rsync -av source destination | grep -v ^sending | grep -v ^sent | grep -v ^total > /path/to/some/file
```

This will cause errors if you have a file named "sending.something" or "sent.something" or "total.something."  However a file named "datatotals.txt" will not matching "^total" since the carat represents the beginning of the line.

---

### Post by nzdreamer55 on 2015-12-07
OMG.  Thank you for going beyond answering my original question.  So I now understand how to move the output to something else using the > symbol. So with the grep command does it mean select all the text of a line that DOES NOT start with "sending", "sent", or "total"?  I Think you are doing this to make it easier for rsync to read the file later on.  Is that also correct?  Could I do something like grep -v ^sent_Number_bytes  received?  Is there a way to put in a symbol that represents a symbol or use regex expressions?  Do I need to put "" around white space structure or use _ in place of white space?  Will grep .txt^ select lines that end in the extension .txt?

And Finally,  Is there a way to split the output so that it goes to the screen and to the file?

---

### Post by SeijiSensei on 2015-12-07
> **nzdreamer55 said:**
> OMG.  Thank you for going beyond answering my original question.  So I now understand how to move the output to something else using the > symbol. So with the grep command does it mean select all the text of a line that DOES NOT start with "sending", "sent", or "total"?

Yes, the "-v" switch to grep returns all the lines that don't match the following regular expression.

> I Think you are doing this to make it easier for rsync to read the file later on.

Yes.  I used the greps to remove all the lines that are not file names.

> Is there a way to put in a symbol that represents a symbol or use regex expressions?  Do I need to put "" around white space structure or use _ in place of white space?  Will grep .txt^ select lines that end in the extension .txt?

grep is the original regular expression utility.  If the string has embedded spaces, just enclose it in single quotes:

```
grep 'some string' 
```

The end-of-line character is the dollar sign.  So to select all lines that end in ".txt" you'd use

```
grep \.txt$
```

I used the backslash as an "escape" character.  It tells grep to treat the period literally rather than as its usual role in regular expression of being a single-character wildcard.

The extensive [manual page for grep]("http://linux.die.net/man/1/grep") presents a lot of detail about regular expressions.

> And Finally,  Is there a way to split the output so that it goes to the screen and to the file?

I don't know of any.  I just use "more filename" or an editoro to view the file after it is written.

---

### Post by nzdreamer55 on 2015-12-12
Thanks.  Just though of something else.  if I run this several times, do it replace the file or dose it append the file with the next run output?
```
rsync -av source destination > /path/to/some/file
```

Something tell me that to append maybe I need to use

```
>>
```

Is that correct?

---

### Post by SeijiSensei on 2015-12-13
I chose not to use ">>" because I didn't know whether each run was self-contained or not. If you want a complete list of all files then you should use ">>" to append to the file.

After the file is created you can use
```
sort < /path/to/filelist | uniq > /path/to/newlist
```
to sort the file list alphabetically and remove any duplicates.

---

### Post by nzdreamer55 on 2015-12-17
So I was thinking what if I tried to just keep the lines that I want rather than keep all the lines except ones

```
[COLOR=#000000][FONT=Ubuntu Mono]rsync -av source destination | grep -v ^sending | grep -v ^sent | grep -v ^total > /path/to/some/file[/FONT][/COLOR]
```

This is what I was working with and it worked.  I got a lot of output.

I tried

```
[COLOR=#000000][FONT=Ubuntu Mono]rsync -av source destination | grep \.txt$ > /path/to/some/file[/FONT][/COLOR]
```

And it worked but if I include another grep then it does not work.

```
[COLOR=#000000][FONT=Ubuntu Mono]rsync -av source destination | grep \.txt$ | grep \.doc$ > /path/to/some/file[/FONT][/COLOR]
```

Is it putting the greps together like an AND statement?  Why does it work when I get all lines except those starting with sending, sent, total, but not when I am looking for all lines that have .txt or .doc at the end?

---

### Post by SeijiSensei on 2015-12-17
Because it works like an AND.  The first grep filters out all lines that end in .txt and passes them to the next filter. Obviously none of those will end in .doc.  The filters with "-v" return lines that do not match the pattern.

You can use this syntax instead:
```
| egrep '\.txt$|\.doc$'
```
which uses "[extended]("http://linux.die.net/man/1/grep")" grep and treats the "|" as an OR.  Put the patterns in single quotes so the shell won't interpret the vertical bar as the pipe character.

---

### Post by nzdreamer55 on 2015-12-17
Thank you a thousand times.  That works really well.  Now I need to make rsync use this file to compare against what is on my server and only move those things that are different.  Is there a way to tell rsync to look at this file rather than compare to target directory?

Also if I want to specify a number could I do something like this

```
egrep '\.r[0-9][0-9]$'
```

That way this would match ".r00", ".r05","r69",etc.

---

### Post by SeijiSensei on 2015-12-18
Use the --include-from switch in rsync.  That tells it to read the list from a file.

For your second question, yes.  You can also use
```
'\.r[0-9]{2}$'
```
to match exactly two numbers.

---

