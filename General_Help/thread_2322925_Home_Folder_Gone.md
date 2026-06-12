---
title: "Home Folder Gone"
date: 2016-05-01
forum: General Help
---

### Post by gammies on 2016-05-01
So I was trying to delete my trash which wasn't deleting and I tried running a bunch of commands.  Woke up the next morning and my home folder was completely gone.  

   80  sudo rm -rf ~/.local/share/Trash
   81  rm -rf /media/Elements/.Trash-1000/
   82  srm -rf /media/Elements/.Trash-1000/
   83  sudo apt-get install secure-delete
   84  srm -rf /media/Elements/.Trash-1000/
   85  rm -rf ~/.local/share/Trash
   86  trash-empty
   87  sudo apt-get install trash-cli
   88  trash-empty
   89  cd ~/.local/share/Trash/
   90  sudo -s
   91  sudo rm -fr *
   92  sudo rm -rf ~/.local/share/Trash/files/*
   93  sudo rm -rf ~/.local/share/Trash/files/
   94  sudo rm -rf ~/.local/share/Trash/
   95  ls /
   96  history

---

### Post by SamInside on 2016-05-01
> **gammies said:**
> 
```

   91  sudo rm -fr *

```
Yes, this is where you did it. You may try some software that restore deleted files. But some of the files may have already been overwritten.

---

### Post by oldos2er on 2016-05-01
Word of warning for the future, there's no need to use 'sudo' in one's home folder, since your trash folder is owned by your user.

Hopefully you had backups.

---

### Post by Bucky Ball on 2016-05-01
Main thing: don't boot from that disk, boot a live session ('Try Ubuntu' from the install media). Testdisk may be able to retrieve the partition if it was a /home partition, photorec may be able to grab individual files. I think they're both on the SystemRescueCD, which is a bootable disk/USB with a lot of useful tools. 

We learn from our mistakes. Always keep backups, ask for help if you're unsure and never run commands without having some idea of what you're about to do (anything with 'sudo' in front of it or performed as root particularly). The command you ran is one of the most lethal there is, as you've discovered. We generally discourage it being posted on the forum, but in this case, required information from the user.

---

### Post by gammies on 2016-05-01
There wasn't anything of particular importance on there.  I should be more careful of who's advice I follow.  I am too lax about which lines I run.  The main problem is that I don't understand what they mean, so I should fix that.


Thanks guys!

---

### Post by Bucky Ball on 2016-05-02
> **gammies said:**
> The main problem is that I don't understand what they mean, so I should fix that.

If in doubt, just post a thread and ask. :)

---

### Post by CaptainMark on 2016-05-03
Any forum user worth his/her salt would never tell you to use "sudo rm -rf [anything]"  unless in very rare circumstances so as Bucky Ball says, next time, if in doubt, ask on here. For future reference anytime I want to recursively delete anything I always do this instead to list files about to be deleted. Run an ls, have a look whats in the directory, then run a find command to make sure you're about to delete the correct directories, then when you're ready just add the -delete flag to the find command ```
[08:07:20] mark@desktop ~ $ ls -R testdir1/testdir1/:
file1  testdir2  testdir3


testdir1/testdir2:
file2


testdir1/testdir3:
testdir4  testfile3


testdir1/testdir3/testdir4:
testfile4
[08:07:25] mark@desktop ~ $ find ./testdir1/ |wc -l
8
[08:07:38] mark@desktop ~ $ find ./testdir1/
./testdir1/
./testdir1/testdir3
./testdir1/testdir3/testdir4
./testdir1/testdir3/testdir4/testfile4
./testdir1/testdir3/testfile3
./testdir1/file1
./testdir1/testdir2
./testdir1/testdir2/file2
[08:07:46] mark@desktop ~ $ find ./testdir1/ -delete -print
./testdir1/testdir3/testdir4/testfile4
./testdir1/testdir3/testdir4
./testdir1/testdir3/testfile3
./testdir1/testdir3
./testdir1/file1
./testdir1/testdir2/file2
./testdir1/testdir2
./testdir1/

```This shows me what files are in the folder first, then how many files and directories would be deleted, then a list of exactly whats getting deleted, then deletes it. Pretty thorough.

---

### Post by Impavidus on 2016-05-03
I agree that "sudo rm -rf [some wildcard]" (<-- don't use that one) is an extremely blunt instrument that I would never use nor suggest to someone else. So don't interpret this post as suggesting that it might be safe, even under specific circumstances, but a little knowledge won't hurt.

Most root-owned files are managed by the package manager so mass deletions of root-owned files are rarely appropriate and -f is mainly used to suppress prompts for deleting write-protected files, which defies the purpose of write-protection. sudo circumvents the write-protection anyway. sudo rm allows deletion of files from write-protected directories, but I'd usually suggest a chmod first to remove the write-protection.

I note though that the dangerous command #91 would recursively delete all files and directories *from the current directory*, using root permissions, including write-protected files, *except the hidden files and directories directly contained in the current directory*. If executed from /, this would wipe (most of) the system (which is why this is such a dangerous command), if executed from the users home directory it would remove all documents, but keep the settings and trash (which are in hidden files or directories) and if executed from ~/.local/share/Trash/, it would do exactly as you intended. Note that * doesn't match on hidden files and directories. .* does match on hidden files and directories, but rm refuses to operate on . and .. (and /, unless overridden), so even that won't wipe your system. It has some safety features, you know.

All of this tells us that command #89 failed: you (OP) were not in the directory where you should have been. Maybe you had already succeeded in deleting the trash directory. It seems plausible to me that you were actually in $HOME, with $HOME now emptied but not deleted (the words in post #1 are slightly ambiguous in this sense). If the directory was indeed deleted, login would be impossible.

Of course, none of this means that rm shouldn't be considered a dangerous command. Recursive deletions should only be performed with extreme caution. And of course, none of this helps you in getting your files back. I hope you have backups.

Also, don't use sudo unless you know why you have to use it. You don't need it to remove your trash, unless some previous error put non-empty root-owned directories in your trash directory. You don't need sudo when you already have a root shell.

---

