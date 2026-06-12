---
title: "Tools to find damaged files (data corruption)?"
date: 2021-03-21
forum: General Help
---

### Post by Sidoney on 2021-03-21
On my PC i found files which are 25-30 years old and damaged: Some have length zero, some are too small, e. g. a postscript file with only 256 byte, and some have trash inside, e. g. C source file (*.c) with a second half that is filled with binary bytes, where code in ANSI  characters was.
I try to prevent such data corruption, by testing each drive with badblocks, the RAM with Memtest etc. but that is not enough.
So i want to check the files, which i have made, at least once a month, to have a chance to restore the damaged files from the last monthly backup.
But i could not find a tool which can check recursively for file corruption.
Is there really no tool to find file corruption?

---

### Post by TheFu on 2021-03-21
**par2**, but the files must be stored with sufficient par2 recovery blocks to be useful. Nothing after the fact, sorry.  [https://blog.jdpfu.com/2011/06/12/optical-data-recovery-technique-with-ddrescue-and-par2](https://blog.jdpfu.com/2011/06/12/optical-data-recovery-technique-with-ddrescue-and-par2)

You can use '**find**' to locate zero length files or files below or above specific sizes.
[https://blog.jdpfu.com/2011/08/29/finding-large-files-on-a-linux-unix-machine](https://blog.jdpfu.com/2011/08/29/finding-large-files-on-a-linux-unix-machine)

Bitrot is real. Only reading and restoring the files every year or two can ensure the data can be read, long term.
ZFS has data integrity features. Those are better with ECC RAM.

---

### Post by DuckHook on 2021-03-21
Well, it's not surprising that 25-30 yr old files that haven't been checked in decades turn out to be corrupt. I wonder what media were used to store them. Were they on floppy disks or old IDE drives? Drive technology 30 years ago was not very robust. And if they have not been touched for 30 years, then even the best rust&#8209;based storage is liable to suffer from bit rot.

I can think of two ways that you can try to detect such corruption, but it only applies to files that are currently good and that you want to maintain going forward. I'm afraid I don't have any general solutions to recursively check already existing ancient files.

[LIST=1]
[*]Going forward, you can generate a simple checksum for each file. By checking your files against this checksum before backing it up, you can see if it has changed in the interim.
[*]ZFS has ongoing file integrity checking built into it. That's one of its primary benefits. I don't know if other advanced files systems like BTRFS or XFS have similar capability. I do know that EXT does not.
[/LIST]
Ninja'd by TheFu. Story of my life. :P

---

### Post by DuckHook on 2021-03-21
Thread moved to *General Help* as the more appropriate subforum.

---

### Post by Sidoney on 2021-03-28
Thanks for the answers. I just found the notification mail in the spam folder.

I  have moved the old files several times, each time i built a new PC and  than copied them to the new PC, from HDD to HDD. In my newest PC the files are  are on a SSD.
One problem is that i have more than one million files in my home directory.  A ```
find . -type f | wc -l
```reports 1.081.397  files, and some are changed every day, e. g. browser cache files. Most  of the oldest files, from the 1990s, were not changed by me in this  century.
So a simple strategy like checking hash values every day are  not possible, because that would report several hundred false positive  damaged files every day.

Therefore i need file consistency checks, which do check if a file is really what it should be.
One  example is a postscript file, with suffix ps and size 256 Bytes, which  is too small for a valid postscript file. So all postscript files should  be checked for a file size of at least 1 kB and the file type, checked  by the magic number with "file", which should report the file type  "Postscript document".
These two checks are the minimum checks which i need.
Other  checks are checking if the content is valid, e. g. if a C file (*.c) contains  only characters which allowed by ANSI-C. I have one C file which has  more than 100 random bytes at the end.

---

### Post by DuckHook on 2021-03-29
There's no point to checking cache files. They are unimportant and exist only to facilitate faster loading speed, often at the expense of accuracy and stability. That's why they are called cache files. I never bother to back mine up and will even occasionally nuke the cache to eliminate flaky behaviour. Ignoring the cache will take away almost all of those false positives. By "ignoring cache", I mean exempting them from any hashing routine.

If you are in the habit of not looking at files for decades, then that is where a hashing strategy shines. Such files don't ever change, so should pass a hash check as a matter of course.

Like TheFu, I know of no app or platform that does what you want. Note that you are not looking for "consistency checks". Hashing and parity, as per TheFu's par2 app, is what provides such consistency checks. What you are asking for is some sort of Artificial Iintelligence ability to retroactively parse through old files and make almost human level judgments about what is valid and what is not.

I know of nothing in the Linux world that does what you are looking for.

---

### Post by Impavidus on 2021-03-29
I don't think 256 bytes is too small for a valid postscript file. It's a bit small for a sensible postscript file though. The smallest sensible postscript file I can find in my homedir is 336 bytes:```
$ cat sierpinski.ps 
%!PS
/x{index}def/r{roll}def/d{dup dup}def/a{add 2 div}def
/s{2 copy sub 0.1 lt{6 -1 r moveto 4 -1 r lineto exch lineto closepath fill}
{5 x d 7 x a exch 6 x a 3 x d 8 x a 3 1 r 7 x a exch s
4 x d 8 x a 3 1 r 6 x a 4 x d 8 x a 3 1 r 6 x a s
2 x a 6 1 r 1 x a 6 3 r 5 x a 6 1 r 4 x a 6 1 r s}ifelse}def
360 360 734 288 504 72 s showpage
```

To do what you want you'll need a script that, for each file, first determines filetype. Then it feeds the file to a tool that's made to handle that filetype. Image files to an image converter, C code to a C compiler, etc. Discard any output, but look at the exit status of the tool. It it reports some error, the file may be corrupt. But don't expect this to be 100% reliable.

---

