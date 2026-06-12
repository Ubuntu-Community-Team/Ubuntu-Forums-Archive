---
title: "rsync specific folders"
date: 2013-01-02
forum: General Help
---

### Post by masterashley on 2013-01-02
Hello!

 First time poster. Could use some help wrapping my head around an rsync issue. I know rsync is not Ubuntu specific, but I thought I would start here since Ubuntu is what I am currently using as an OS. 

I only want to backup directories within a directory with a specific name. The directory can be located anywhere within the parent, I would also like to keep directory structure intact.

So say, 

rsync search for all directories in this "destination folder" with the name "mysearch" and backup its contents only and keep directory structure.

Can this be done? Thanks for looking

Cheers,
Ash

---

### Post by erind on 2013-01-02
> **masterashley said:**
> [...]
I only want to backup directories within a directory with a specific name. **The directory can be located** **anywhere within the parent, I would also like to keep directory structure intact.**

So say, 

rsync search for all directories in this "destination folder" with the name "mysearch" and backup its contents only and keep directory structure.

Can this be done? Thanks for looking

Cheers,
Ash

Rsync can read paths, lists (*--include-from=*, etc ...) or expand shell's wildcards, but it can't do searches in the sense that you're describing here. They're usually **find**'s domain.
So to search for given directories **anywhere** in the parent's directory tree, that contain "*mysearch*" term and keep the directory structure intact while copying, you can do something like:

```
cd /path/to/your_directory/

find . -name '*mysearch*' -type d -print0 | rsync -avr0 --files-from=- . user@remote:/destination/dir
```Note the* rsync's -r (--recursive)* option.
[http://linux.die.net/man/1/rsync](http://linux.die.net/man/1/rsync)

---

### Post by masterashley on 2013-01-11
Excellent!! Thanks for the input!

Much appreciated.

---

