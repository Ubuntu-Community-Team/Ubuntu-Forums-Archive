---
title: "Recursive folder deletion network shares"
date: 2022-01-01
forum: General Help
---

### Post by labbetuss on 2022-01-01
Hi.
My newly bought NAS had creation of .thumbs folders enabled by default, which causes every folder on my NAS that contains media files to get .thumbs folders. I have diasbled the feature, but I'm stuck with all the .thumbs folders. 
I could use some help with a command that I can use to delete every .thumbs folder in every subfolder of a share.

---

### Post by KBar on 2022-01-01
```
find /path/to/directory -type d -name '.thumbs' -exec rm -rf '{}' +
```

You're going to have to specify the name of the directory to search for. For example, if those subdirectories are scattered all over directory B which is located in /A, you would invoke **find** like this:
```
find /A/B -type d -name '.thumbs' -exec rm -rf '{}' +
```

To first get a list of matched file names before removing them, run this:

```
find /path/to/directory -type d -name '.thumbs' | less
```

[HR][/HR]**find**(1)

---

### Post by TheFu on 2022-01-01
Be very careful using 'find'.  Often, it will 'find' things you didn't intend and with the command above, it will be very bad.  How do I know?  I've done it myself doing something very similar and wiped all of /bin/ when I was looking for .cache directories.

I'd do it in 3 steps.
Step 1: Create a list of directories.
$ find /path/to/directory -type d -name '.thumbs'  > /tmp/thumb-dirs

Step 2: manually check the file /tmp/thumb-dirs to ensure no extra directories were found. If some extras are/were found, either fix the 'find' command to be more restrictive or remove those lines from the file and continue below.

Step 3: Either add -delete to the end of the find command (this will only delete empty directories and is safer), or edit the /tmp/thumb-dirs to add a rmdir before each line and run it.

rm -rf is dangerous for noobs and experts alike. We need to be extremely cautious using it. Double-check what will actually be removed. Triple-check if a script is doing it.

---

### Post by KBar on 2022-01-01
Good suggestions, TheFu. I actually agree with you and always prefer to use find's own _-delete_ action myself. I don't know why I chose _-exec_. Probably out of memory, because many scripts that I've encountered use _-exec rm -rf_.

For **rm** _-rf_ in general, make it a habit to check the target path first (e.g. with **ls**).

---

### Post by labbetuss on 2022-01-01
Thanks for helpful inputs. I dont have a problem with using rm -rf. There are absolutely no folders on my NAS with the naming .thumbs that I want to keep. I also have several copies of all the files on other NAS boxes as well(I am in the process of copying old files to a new NAS). I have a text file which contains information about every share and its size down to bytes. So I can easily do a comparison after doing the deletion with find and rm -rf. If "find" for some reason deletes more than anticipated, I can always copy the files over from an older NAS. Again, thanks.

---

### Post by KBar on 2022-01-01
I see. I also want to talk about two more things: one, _-delete_ does not spawn an extra process for removal like any _-exec_ action does (to run the external command); and two, the plus sign (+) instructs find to act upon on multiple files at once as opposed to ending a command with a semicolon, which runs the command for each file one at a time. As you can see, both _-delete_ and + are more efficient.

This is actually your first post, which I didn't notice, and I'm very sorry for being impolite. Welcome to the forum and Happy New Year!

---

### Post by TheFu on 2022-01-01
> **labbetuss said:**
> Thanks for helpful inputs. I dont have a problem with using rm -rf. There are absolutely no folders on my NAS with the naming .thumbs that I want to keep. I also have several copies of all the files on other NAS boxes as well(I am in the process of copying old files to a new NAS). I have a text file which contains information about every share and its size down to bytes. So I can easily do a comparison after doing the deletion with find and rm -rf. If "find" for some reason deletes more than anticipated, I can always copy the files over from an older NAS. Again, thanks.

I suspect you will discover that different file systems will report different file sizes. Hard to compare files when they are slightly different.

Also, ".thumbs" is a file globbing input where the '.' means ANY character, so it is possible that more than intended will be found.  I've been through similar stuff over my decades as a Unix/Linux admin.

Recreating a list of all the files and directories on any system is trivial. For just the names, 
```
$ find / | tee /tmp/all-files
```
or 
```
$ find / -ls | tee /tmp/all-files
```
gets lots of detailed information, including inode numbers. Sometimes having the inodes is handy.  Before disks were cheap, I'd use optical media for storage.  An **ls -lR** in a file that mapped to the disc number made for a quick DB and **egrep** would quickly find a file across hundreds of discs.

---

### Post by KBar on 2022-01-01
> **TheFu said:**
> Also, ".thumbs" is a file globbing input where the '.' means ANY character, so it is possible that more than intended will be found.  I've been through similar stuff over my decades as a Unix/Linux admin.

While it is true that the _-name_ test uses shell pattern (globbing, wildcards) for file names, that meaning of the period '.' is used only in regular expressions. Unless _-regex_ is specified, _-name_ should always match using traditional shell globbing. So the pattern '.thumbs' in this case  should not cause any surprises and the period doesn't bear a special meaning outside of denoting a hidden file name.

---

### Post by TheFu on 2022-01-01
> **kbar said:**
> While it is true that the _-name_ test uses shell pattern (globbing, wildcards) for file names, that meaning of the period '.' is used only in regular expressions. Unless _-regex_ is specified, _-name_ should always match using traditional shell globbing. So the pattern '.thumbs' in this case  should not cause any surprises and the period doesn't bear a special meaning outside of denoting a hidden file name.

I stand/sit corrected. I still recall the panic of seeing /bin/ deleted all those years ago.  It was a very bad day at work due to my simple 'find' cleanup script.
The machine was less than a week old, but thankfully, I'd made an OS image to tape the day before.  But I'd never restored an image ... and had to go buy a book to lookup the command(s).  The company was an MS-Windows-only shop. I was hired for cross platform development experience, but I wasn't an admin at the time ... yet.

BTW:
```

$ mkdir .thumbs
$ touch .thumbs/t

$ find . -name ".thumbs" -delete
find: cannot delete ‘./.thumbs’: Directory not empty

$ rm .thumbs/t 

$ find . -name ".thumbs" -delete

```
working as expected.

---

### Post by labbetuss on 2022-01-01
Thanks again kbar, can I ask why you put "'{}' +" at the end after -rf?

---

### Post by TheFu on 2022-01-01
> **labbetuss said:**
> Thanks again kbar, can I ask why you put "'{}' +" at the end after -rf?

{} is the normal way to tell 'find' to insert each result into an exec command one at a time.  The delimiter after {} is needed so find can tell the difference between the filename and the end of a command, I think.  Check the manpage for 'find' for the official answer, but really - please don't use -exec rm -rf {} in any 'find' command. There are better options, like the -delete.

I typically do something like this ...
```
$ find . -type d -name \*thumb\*  -exec du -sh {}   \;
```
Perhaps quoting is safer, but I'm just as happy using \*thumb\* as "*thumb*".

Unix file systems allow any valid character to be used in filenames. Since directories are also "files", they can have any character too, unlike some other OSes. Being able to handle all those different names regardless of the odd characters used can be hard, but needs to be supported.

---

### Post by KBar on 2022-01-02
> **labbetuss said:**
> Thanks again kbar, can I ask why you put "'{}' +" at the end after -rf?

Now you see that find's syntax is quite complicated and that's why avoiding *rm -rf* is a good idea. You seldom get everything right the first time with find.

'{}' is expanded to a list of matching file names. It needs to be escaped or quoted to protect it from the shell. With _-exec_, which essentially calls up an external command, you need to explicitly state where your find expression ends. One way is to do it with an escaped semicolon, i.e. \;. It's okay to use it if the number of files that needs processing isn't large. The other way is to end a command with a plus sign when there are multiple files, which is more efficient and the plus sign doesn't have to be quoted or escaped. Here's the simplified explanation of their difference (someone correct me if I got it wrong):

```
$ find . -name 'file*' -exec rm rf '{}' \;
```
Will invoke **rm** as many times as there are matches. It is similar to how you'd do it yourself from the shell, removing files one by one:
```
$ rm -rf file1
$ rm -rf file2
$ rm -rf file3
$ # so on and so forth
```

While with a plus sign:
```
$ find . -name 'file*' -exec rm rf '{}' +
```
the external **rm** command is only run once to operate on all the matches at once, which is equivalent to giving multiple file names as separate arguments to **rm**:
```
$ rm -rf file1 file2 file3 file4 file5 file6
```

---

### Post by labbetuss on 2022-01-02
Thanks kbar, your suggestions worked like a charm! You just saved me a ton of work :-) :-)

---

### Post by KBar on 2022-01-02
My pleasure.

---

### Post by TheFu on 2022-01-02
Another method is to feed the 'find' output into xargs.  There is a limit as to how long any inputs can be to a command - I don't know the defaults off the top of my head, but in the 1990s, 256 characters was a common limit.

Anyway, if all the resulting files are sent to a command that cannot handle it, that's when xargs is very handy.  It also passes all the files into the program, but it has options to control the chunk sizes, so perhaps only 100 files at a time can be passed on.  There are also options for both find and xargs to use null separated argument. When filenames are allowed to have challenging characters, the default separator of white space isn't too useful.

```
$ find . -type d -name .gthumbs -print0 | xargs --null --max-args=100 rmdir
```

But the 
[/code]$ find . -type d -name .gthumbs -delete[/code]
method is faster, more efficient.

---

