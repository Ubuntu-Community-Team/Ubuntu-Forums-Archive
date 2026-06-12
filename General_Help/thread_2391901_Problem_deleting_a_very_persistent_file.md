---
title: "Problem deleting a very persistent file"
date: 2018-05-14
forum: General Help
---

### Post by gaussia on 2018-05-14
Hello, I am having problems deleting a file.
[SIZE=3]
**Background**[/SIZE]
If I write lsb_release I get this output
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:    xenial

I originally had a matlab script that went over a set of folders with experimental data. It copied the stuff which I was interested in to new folders. I tried deleting the file system created to rerun the script (it generated some extra folders which I didn't need and only made things messy). One of the folders contained a file "test.mat" which refuses to be deleted. The file is on an external drive and I can look at it in my windows virtual machine (windows 10). It says that it is an "Microsoft Acces Table Shortcut) type of file.

[SIZE=3]**I have tried:**[/SIZE]
**In the virtual machine:**
[SIZE=3][/SIZE]- Deleting the file. It seems to disappear, however when I move out of the folder and back it is still there.
- Moving the file to somewhere else. I get a message that I need permission from the computer admin to do so.

[B]In ubuntu:
[/B]- Deleting it from the filesystem UI. I get a message saying " “test.mat” can't be put in the Rubbish Bin. Delete it permanently instead? ". There is an option to show more details telling me "Error moving file to wastebasket: No such file or directory". If I click delete I get a new message 
" There was an error getting information about “test.mat”." ".
- Deleting from terminal using "rm test.mat". I get a response "rm: cannot remove 'test.mat': No such file or directory"
- Deleting using "rm -f test.mat". Nothing happens. The file is still there.
- Deleting using "rm -rf test.mat". Nothing happens. The file is still there.
- Deleting using "sudo rm -test.mat". I get a response "rm: cannot remove 'test.mat': No such file or directory"
- Deleting file and folder from terminal using "rm -r Data". I get a response "rm: cannot remove 'Data/test.mat': No such file or directory"

At this stage I have no idea. I have tried looking online but found no hint or "better" delete function than I have already tried. Would be very thankful for help.

---

### Post by SeijiSensei on 2018-05-14
Seems unlikely, but maybe the file is marked "immutable?"  

```
lsattr /path/to/test.mat
```

Do you see an "i" in the list of characteristics in the first column of output?  If so, you'll need to turn off the immutable switch first before you can delete the file.  Even the root user cannot delete an immutable file.

```
sudo chattr -i /path/to/test.mat
```

This isn't something you would have done by accident since it requires root ("sudo") privileges to change attributes.  Maybe it's a Matlab "feature?"

---

### Post by gaussia on 2018-05-14
Does not seem to work. I try the commands and get responses:

"lsattr: No such file or directory while trying to stat /Data/test.mat"
"chattr: No such file or directory while trying to stat test.mat"

The file is there though. Clearly displayed with e.g. ls.

Also: When I try opening it using matlab I get this error message:
Error using load
Unable to read file '.../Data/test.mat'. No such
file or directory.

---

### Post by SeijiSensei on 2018-05-15
Are you sure it's "/Data/" and not "/data/"?  Is /Data off the root directory, or below some other?

What does the command "locate test.mat" return?

---

