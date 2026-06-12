---
title: "Can someone help me how I ended up deleting all the files from my /home/zaid folder?"
date: 2022-08-29
forum: General Help
---

### Post by xaydkibriya on 2022-08-29
Hello,

There are two things:

1. I was trying to delete a few files (anydeskwarning.txt, anydeskwarning1.txt) from my home directory (/home/zaid#).

I couldn't recall the exact command, I remember it had something do to with * (wildcard), so I tried a couple of commands and then all of sudden everything is gone.

I could not understand where I went wrong. I managed to make an output of the commands I entered.

Can someone please look at it and tell me where did I go wrong? Because I am not sure how I ended up deleting the home directory.

2. Then, I tried backing up files via PhotoRec before powering off the machine, but when choosing the disk, I could see around 8 disks in the options but couldn't find the appropriate one, so I went with the whole 1TB option and it did recover some files but there were all in .java and txt files mostly and then my disk was full so the recovery had stopped. Although I want my files back, I know it's next to impossible to get them back, at least for me. So, I guess I should not have any hopes. 

Pictures attached

attaching terminal output:

```
root@ubuntu:/# cd /home/zaid/
root@ubuntu:/home/zaid# ls
 anydeskerror.txt   anydeskwarning1.txt   anydeskwarning.txt   Apps   Desktop   Documents   Downloads   mu_code   Music   pics   Pictures   Public   snap   Templates   Videos  'VirtualBox VMs'
root@ubuntu:/home/zaid# rm *anydeskwarning
rm: cannot remove '*anydeskwarning': No such file or directory
root@ubuntu:/home/zaid# rm -v *anydeskwarning
rm: cannot remove '*anydeskwarning': No such file or directory
root@ubuntu:/home/zaid# rm -R *anydeskwarning
rm: cannot remove '*anydeskwarning': No such file or directory
root@ubuntu:/home/zaid# rm -R * anydeskwarning
rm: cannot remove 'anydeskwarning': No such file or directory
root@ubuntu:/home/zaid# rm --h
Usage: rm [OPTION]... [FILE]...
Remove (unlink) the FILE(s).

  -f, --force           ignore nonexistent files and arguments, never prompt
  -i                    prompt before every removal
  -I                    prompt once before removing more than three files, or
                          when removing recursively; less intrusive than -i,
                          while still giving protection against most mistakes
      --interactive[=WHEN]  prompt according to WHEN: never, once (-I), or
                          always (-i); without WHEN, prompt always
      --one-file-system  when removing a hierarchy recursively, skip any
                          directory that is on a file system different from
                          that of the corresponding command line argument
      --no-preserve-root  do not treat '/' specially
      --preserve-root[=all]  do not remove '/' (default);
                              with 'all', reject any command line argument
                              on a separate device from its parent
  -r, -R, --recursive   remove directories and their contents recursively
  -d, --dir             remove empty directories
  -v, --verbose         explain what is being done
      --help     display this help and exit
      --version  output version information and exit

By default, rm does not remove directories.  Use the --recursive (-r or -R)
option to remove each listed directory, too, along with all of its contents.

To remove a file whose name starts with a '-', for example '-foo',
use one of these commands:
  rm -- -foo

  rm ./-foo

Note that if you use rm to remove a file, it might be possible to recover
some of its contents, given sufficient expertise and/or time.  For greater
assurance that the contents are truly unrecoverable, consider using shred.

GNU coreutils online help: <https://www.gnu.org/software/coreutils/>
Full documentation <https://www.gnu.org/software/coreutils/rm>
or available locally via: info '(coreutils) rm invocation'
root@ubuntu:/home/zaid# ls
root@ubuntu:/home/zaid# ls
root@ubuntu:/home/zaid# dir
root@ubuntu:/home/zaid# ls
```

---

### Post by &amp;KyT$0P# on 2022-08-29
> **xaydkibriya said:**
> Can someone please look at it and tell me where did I go wrong? Because I am not sure how I ended up deleting the home directory.

It was this one -
```
root@ubuntu:/home/zaid# rm -R * anydeskwarning
```
That recursively deletes A) all non-hidden files and folders in the current directory (*), and B) the file or folder named exactly "anydeskwarning" in the current directory.

---

### Post by Impavidus on 2022-08-29
> **xaydkibriya said:**
> 
```

root@ubuntu:/home/zaid# rm *anydeskwarning
rm: cannot remove '*anydeskwarning': No such file or directory
root@ubuntu:/home/zaid# rm -v *anydeskwarning
rm: cannot remove '*anydeskwarning': No such file or directory
root@ubuntu:/home/zaid# rm -R *anydeskwarning
rm: cannot remove '*anydeskwarning': No such file or directory

```
In those commands, the shell will match *anydeskwarning to every filename ending in anydeskwarning, not starting with . and in the current directory. As no such files exist (all have some more characters following), this matching fails and the shell leaves the argument as given by you, including the * character. This file doesn't exist, so rm complains.
> ```
root@ubuntu:/home/zaid# rm -R * anydeskwarning
rm: cannot remove 'anydeskwarning': No such file or directory

```
In that command, the shell matches * to the name of every file and directory in the current directory, except those with a name starting with a dot. Because there's a space between the * and the name after it, the shell sees them as separate arguments. rm then removes every file and directory, including contents, except those starting with a dot, and then attempts to remove the file or directory anydeskwarning, which doesn't exist, so it complains.

What you should have used, is:```
rm anydeskwarning*
```

BTW, to remove some files from your own home directory, you don't need root permissions. I hope you're not in the habit of using a root shell when you don't need it. It's another disaster waiting to happen.

Edit:
I've never used photorec, but I can tell you that those loop devices aren't real storage. The real storage is the /dev/nvme0n1 at the bottom. To do some recovery, you have to boot on a live disk, not mount the drive you want the files recovered from, then write the recovered files to a separate drive. Never write anything to a drive you want to recover files from.

---

### Post by xaydkibriya on 2022-08-30
Thank you all for your help. I now see where I messed up.

I started using Linux back in Jan 2022 and this is the first time I had done something like that. I got habitual of using root 99% of the times but I realise I need to change that habit before I mess up even worse.

Thank you again for your quick responses.

---

### Post by TheFu on 2022-08-30
> **xaydkibriya said:**
> Thank you all for your help. I now see where I messed up.

I started using Linux back in Jan 2022 and this is the first time I had done something like that. I got habitual of using root 99% of the times but I realise I need to change that habit before I mess up even worse.

Thank you again for your quick responses.

Ubuntu is designed NOT to use root directly.  Best to learn that, but you can still shoot yourself in the head with sudo.  I've done similar stuff like this multiple times.  That's why automatic, daily, versioned, backups are necessary.  Adding an extra space to an 'rm' command accidentally doesn't result in a terrible day, just a little inconvenience as I restore the files from backup.

```
rm -r a*
```
vs
```
rm -r a *
```

one little space and it is a bad day.

---

### Post by Impavidus on 2022-08-31
> **xaydkibriya said:**
> I got habitual of using root 99% of the times but I realise I need to change that habit before I mess up even worse.
Chances are that there are already root owned files spread all over your home directory. A recursive chown would fix that:```
sudo chown -R $USER:$USER $HOME
```

---

