---
title: "Who is the &quot;owner&quot; of files?"
date: 2020-01-18
forum: General Help
---

### Post by lwalper on 2020-01-18
Who is the "owner" of files? I posted elsewhere that I was having trouble uninstalling a program. That's history (been resolved). But, in the process I tried to delete some files/folders and was kindly informed that I did not have permission to delete because I was not the "owner" of the file/folder. If I am the admin and are the one who installed the file/folder why am I not the owner? I tried using chmod to change file ownership, but never did figure out who the original owner was so that I could change the ownership from "xxx" to "me".

---

### Post by CatKiller on 2020-01-18
The owner of the file is the owner of the file. You can see which user that is with *ls -l* or the file attributes in your file browser.

Changing ownership of files willy-nilly is generally the wrong solution, regardless of what the problem is.

---

### Post by lwalper on 2020-01-18
> **CatKiller said:**
> The owner of the file is the owner of the file. You can see which user that is with *ls -l* or the file attributes in your file browser.

Changing ownership of files willy-nilly is generally the wrong solution, regardless of what the problem is.

OK, Thanks! Willy-nilly -- understood.

So, when I enter:
 ~ $ ls -l
total 36
drwxr-xr-x 2 leslie leslie 4096 Jan 17 10:34 Desktop
drwxr-xr-x 2 leslie leslie 4096 Jan 15 22:35 Documents
drwxr-xr-x 2 leslie leslie 4096 Jan 17 09:09 Downloads
drwxr-xr-x 2 leslie leslie 4096 Jan 15 22:35 Music
drwxr-xr-x 2 leslie leslie 4096 Jan 15 22:35 Pictures
drwxr-xr-x 2 leslie leslie 4096 Jan 15 22:35 Public
drwxr-xr-x 2 leslie leslie 4096 Jan 15 22:35 Templates
drwxr-xr-x 2 leslie leslie 4096 Jan 15 22:35 Videos
drwxrwxr-x 3 leslie leslie 4096 Jan 16 19:48 VirtualBox VMs

I guess that means I am the owner -- so I should be able to delete stuff? (whether it's wise to do so or not is not the question).

And when I do "cd Downloads" I can navigate to the Downloads folder. However, when I "cd VirtualBox VMs" I get the error --
bash: cd: VirtualBox: No such file or directory

The folder shows in the file structure. Is that a hidden folder that I'm not supposed to be able to get to? Or is there an invisible keystroke between VirtualBox and VMs that is not readily apparent?

---

### Post by yetimon_64 on 2020-01-18
> **lwalper said:**
> Who is the "owner" of files?...
In your home folder, you are the owner. Outside your home folder, that is in the filesystem for the OS, there are several system accounts which can "own" the files and folders; most commonly "root".

> **lwalper said:**
> If I am the admin and are the one who installed the file/folder why am I not the owner?
If you are in your home folder and a file/folder is owned by root the most likely explanation is you have been using sudo incorrectly. If you are referring to anything outside of your home folder then the situation is you ARE NOT the owner, a system account owns the file/folder. This set up is one of the main reasons Linux is so hard for viruses/malware to affect, very effective separation of root and user accounts.

 > **lwalper said:**
> ... I tried using **chmod to change file ownership**, but never did figure out who the original owner was so that I could change the ownership from "xxx" to "me".
"**chmod**" **is used to change permissions**, the command you need to change the file ownership is "chown", you tried with the wrong command there.

You are the "user", that is your account is a normal user. If your account is the first installed it is added to the sudoers file to give you the ability to become "admin" (also known as "root") to alter system files owned by the various system users including root.

The first link in my signature line "Rootsudo Documentation" may be worth a read for you. It documents the use of the sudo command in Ubuntu.

Also this next link may help you to understand a bit more about ownership and permissions.
[[COLOR=#0000ff]https://www.thegeekdiary.com/understanding-basic-file-permissions-and-ownership-in-linux/[/COLOR]]("https://www.thegeekdiary.com/understanding-basic-file-permissions-and-ownership-in-linux/")

Be EXTREMELY careful changing ownership or permissions on files/folders _*outside of your home folder*_, that is on anything owned by root or system account owned files/folders; doing so can render your OS unworkable if you don't know exactly what you are doing.

> And when I do "cd Downloads" I can navigate to the Downloads folder. However, when I "cd VirtualBox VMs" I get the error --
bash: cd: VirtualBox: No such file or directory[s]VirtualBox VMs is directly in your home folder not in Downloads.[/s] **Edit:** I have read that wrong. Try enclosing VirtualBox VMs in quotation marks like "VirtualBox VMs", the terminal does NOT like any spaces in file or folder names. Any spaces in terminal need to be "escaped" with a backslash **OR** by enclosing in quote marks.

---

### Post by lwalper on 2020-01-18
> **yetimon_64 said:**
> . . .  if you don't know exactly what you are doing.

That's me!!

> [s]VirtualBox VMs is directly in your home folder not in Downloads.[/s] **Edit:** I have read that wrong. Try enclosing VirtualBox VMs in quotation marks like "VirtualBox VMs", the terminal does NOT like any spaces in file or folder names. Any spaces in terminal need to be "escaped" with a backslash **OR** by enclosing in quote marks.

Thanks. that " " works. I wondered about the spaces.

---

### Post by yetimon_64 on 2020-01-18
> **lwalper said:**
> ...
Thanks. that " " works. I wondered about the spaces.
You're welcome.

From early on in Linux when typing a file/folder name I got into the practice of using the dash symbol "-" instead of the spacebar. It feels very strange doing so initially but is a great help when a file/folder name is used in any scripting or in the terminal; spaces can sure cause headaches with scripting if you're not very vigilante with the quotation marks.

---

### Post by CatKiller on 2020-01-18
> **lwalper said:**
> And when I do "cd Downloads" I can navigate to the Downloads folder. However, when I "cd VirtualBox VMs" I get the error --
bash: cd: VirtualBox: No such file or directory


You already know it's important to get the case right, and you've learned that you can enclose names within "", but another thing that's extremely helpful is using Tab-completion. Type the first couple of letters, cd Vi in this case, and press Tab and the shell will complete the rest as much as it can. 

As an aside; in this case the shell would complete it to "VirtualBox\ VMs" which shows you that \ is the "escape" character; that space will be treated as just part of the string rather than a way to separate arguments.

---

### Post by yetimon_64 on 2020-01-18
> **CatKiller said:**
> ... but another thing that's extremely helpful is using Tab-completion. Type the first couple of letters, cd Vi in this case, and press Tab and the shell will complete the rest as much as it can...

+1, That is extremely useful in terminal.

---

### Post by lwalper on 2020-01-18
> **yetimon_64 said:**
> +1, That is extremely useful in terminal.

Ditto!! Thanks bunches.

---

### Post by TheFu on 2020-01-18
Every popular OS in the world, except 1 follows the Unix permissions model.  If you avoid learning it today, you will have hours, days, weeks, months, years of frustration.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
Learning it now is not a waste of time.  Spend 20 minutes working through that explainer.  Then create 3 new userids, 2 new groups, open 3 terminals and cd into /tmp/something .... then mix and match every possible combination of permission, group, owner that you can think of.  Spend 45 minutes doing this.  About 10 min in, some profound understanding should start to "click".  By 20 minutes in, all the major patterns should be clear.
Don't forget to mix directory settings along with file settings.
Don't forget to notice which users can and cannot edit/create/delete files in each directory.

In about an hour, you should be more knowledgeable than 95% of other users and little stuff like what you're dealing with no will never be any issue again.

chown
chmod
touch some-file-name

+100 on tab-completion.  Tab completion means never misspelling a filename again.  Ever, regardless of spaces, funky characters or not.  Of course, it is best NOT to create files or directories with spaces, since that is a natural file/directory name delimiter in scripting.  Spaces aren't the only characters to be avoided.  Bash has some powerful ways to accomplish things by using certain characters.  Any of those really should be avoided for your sanity.

Just for fun, run these commands:
```
cd /tmp
touch '-delete-me'
```

Now, try to delete that file using only terminal commands.  I'll wait.

---

### Post by yetimon_64 on 2020-01-19
> **TheFu said:**
> ...
Just for fun, run these commands:
```
cd /tmp
touch '-delete-me'
```

Now, try to delete that file using only terminal commands.  I'll wait.

> ```
yetiman:~ $  cd /tmp
yetiman:/tmp $  touch '-delete-me'
touch: invalid date format ‘elete-me’
```

Unfortunately I can't even "touch" that filename here, it is being treated as a date format.

I have been caught with downloaded images starting with a dash "-" and yes I tried to delete them in terminal. What a "pain" ! I got rid of them finally but it sure took a while to work out.

Regards, yeti.

---

### Post by corradoventu on 2020-01-19
you must enter cd 'VirtualBox VMs' because the folder name contain a blank so you must enter the name between quotes

---

### Post by TheFu on 2020-01-19
> **corradoventu said:**
> you must enter cd 'VirtualBox VMs' because the folder name contain a blank so you must enter the name between quotes

or .... ```
cd VirtualBox\ VMs
```
or just use tab-completion and don't worry about it.
```
cd ~/Vi{tab}

```which will find the files/directories in the userid's HOME that begin with "Vi" and fill in the rest.  On most systems, "Vi" will be unique, so it will find it and fill in the complete name.

*tab-completion* is one of those things that make bash/fish/zsh/tcsh .... so much more useful than other shells like sh, cmd.exe, command.com ... etc.  In general, if you are typing more than 2-3 characters at a time, then you are doing it wrong.

---

