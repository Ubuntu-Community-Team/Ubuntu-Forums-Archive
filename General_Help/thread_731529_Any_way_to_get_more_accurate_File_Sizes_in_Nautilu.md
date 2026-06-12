---
title: "Any way to get more accurate File Sizes in Nautilus or Thunar??"
date: 2008-03-21
forum: General Help
---

### Post by OzzyFrank on 2008-03-21
OK, let's say I'm trying to squeeze in as much as I can on a DVD... in Windows Explorer it will at least tell me when I have gotten to 4.38Gb (which is actually the maximum a "4.7Gb" disc can take). Even then I could be a tad over, but there are ways to see if I have gone over 4486Mb (the safe size in megabytes - the max is really 4488Mb but not all discs can fit that extra 2Mb).

In Ubuntu, with both Nautilus and Thunar, I am told the same folder is 4.4Gb. So first off I'd like to know why this is so, as even burning programs in Ubuntu will agree with the Windows way of looking at things. Secondly, how can I view a total in megabytes, as this is really the most accurate way of ascertaining how close to a full DVD a folder really is. Thanks in advance!is an executable text file

---

### Post by hyperair on 2008-03-22
I'd actually use an actual burning program for that, say Brasero or K3B. Nautilus isn't really meant for burning even if it does provide that functionality.

---

### Post by Distro Jockey on 2008-03-22
```
du /path/to/root/folder/ofstufftoburn
```
The last line will list the total in bytes of all files beneath the folder specified.
You can also use:  du -h

---

### Post by OzzyFrank on 2008-03-22
> **hyperair said:**
> I'd actually use an actual burning program for that, say Brasero or K3B. Nautilus isn't really meant for burning even if it does provide that functionality.

Hi, and thanks... but I think you misunderstood the question. I also use burning programs to do the job, but rely on my file manager to give me an accurate total of the contents of the folder (the folder being the one I shove everything into not just to keep all parts of the project together, but to let me know when I have enough for a DVD).

Thanks Distro Jockey for the du command. Is there one for megabytes as opposed to bytes? 4486Mb is easier to remember than the equivalent in bytes, hehe. Thanks guys.

PS: I like this command... just open a terminal in the folder you're in and enter **du**, or **du -h** for it in Gb. I read the help and correct me if I am totally wrong (and please do), but seems -m gives me megabytes?? Is 3163 the amount of Mb in 3.1Gb? For the benefit of others, I will give the options etc for du:

Usage: du [OPTION]... [FILE]...
  or: du [OPTION]... --files0-from=F
Summarise disk usage of each FILE, recursively for directories.

Mandatory arguments to long options are mandatory for short options too.
  -a, --all write counts for all files, not just directories
      --apparent-size print apparent sizes, rather than disc usage; although
                          the apparent size is usually smaller, it may be
                          larger due to holes in (`sparse') files, internal
                          fragmentation, indirect blocks, and the like
  -B, --block-size=SIZE use SIZE-byte blocks
  -b, --bytes equivalent to `--apparent-size --block-size=1'
  -c, --total produce a grand total
  -D, --dereference-args dereference FILEs that are symbolic links
      --files0-from=F summarise disk usage of the NUL-terminated file
                          names specified in file F
  -H like --si, but also evokes a warning; will soon
                          change to be equivalent to --dereference-args (-D)
  -h, --human-readable print sizes in human readable format (e.g., 1K 234M 2G)
      --si like -h, but use powers of 1000 not 1024
  -k like --block-size=1K
  -l, --count-links count sizes many times if hard linked
  -m like --block-size=1M
  -L, --dereference dereference all symbolic links
  -P, --no-dereference don't follow any symbolic links (this is the default)
  -0, --null end each output line with 0 byte rather than newline
  -S, --separate-dirs do not include size of subdirectories
  -s, --summarise display only a total for each argument
  -x, --one-file-system skip directories on different file systems
  -X FILE, --exclude-from=FILE Exclude files that match any pattern in FILE.
      --exclude=PATTERN Exclude files that match PATTERN.
      --max-depth=N print the total for a directory (or file, with --all)
                          only if it is N or fewer levels below the command
                          line argument; --max-depth=0 is the same as
                          --summarize
      --time show time of the last modification of any file in the
                          directory, or any of its subdirectories
      --time=WORD show time as WORD instead of modification time:
                          atime, access, use, ctime or status
      --time-style=STYLE show times using style STYLE:
                          full-iso, long-iso, iso, +FORMAT
                          FORMAT is interpreted like `date'
      --help display this help and exit
      --version output version information and exit

SIZE may be (or may be an integer optionally followed by) one of following:
kB 1000, K 1024, MB 1000*1000, M 1024*1024, and so on for G, T, P, E, Z, Y.

Report bugs to <bug-coreutils@gnu.org>.

---

### Post by hyperair on 2008-03-22
Well I usually don't shove them into one folder, but instead put them together into a project of K3B, then save it. Then I can pick it up again and continue working on it when I have time.

---

### Post by OzzyFrank on 2008-03-22
> **hyperair said:**
> Well I usually don't shove them into one folder, but instead put them together into a project of K3B, then save it. Then I can pick it up again and continue working on it when I have time.

The reason I do that is, more often than not, when the stuff is burned to a DVD, I will delete it off my hard drive. It makes that part of it a lot easier when it's all in 1 folder. I do this especially with distro .isos I download.

I edited my last post to include the options and usage of the du command, so check it out if you're interested. This is quite handy. The option to display bytes is the answer to someone else's question, so will have to post it there too. Cheers

---

### Post by Distro Jockey on 2008-03-22
Actually, looking at it again, **du** gives me Kb's. **du -b**  gives bytes. Can't see a way to turn GB into MB though.

---

### Post by lswest on 2008-03-22
um, judging by the info in the post ```
du -m
``` should show it to you in megabytes.

---

### Post by danwood76 on 2008-03-22
'du -h' gives you GB
'du -hm' gives you MB.
'du -hk' KB

Hope it helps you.

---

### Post by Lord Illidan on 2008-03-22
```
man du
```

---

### Post by OzzyFrank on 2008-03-22
Yeah, **du -m** gave me the same output as **du -hm**. I assume this is real megabytes too (ie based on 1024 not 1000, which it seems would be a **-MB** option for the latter). Wow, this command is pretty versatile. Thanks again DJ for bringing this to our attention!

---

