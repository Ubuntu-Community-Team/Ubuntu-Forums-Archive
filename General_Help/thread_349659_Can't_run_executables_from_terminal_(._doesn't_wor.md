---
title: "Can't run executables from terminal (./ doesn't work)"
date: 2007-01-30
forum: General Help
---

### Post by funnyperson1 on 2007-01-30
Ok this is a very odd problem I am having right now.  Off a fresh install of Ubuntu 6.10 x64, I am not able to run any executables from the terminal.

For example I downloaded the Folding at Home client and Prime 95 for linux, but for example here is what happens when I type in ./fah5:

asohangh@bigblue:~/Folding$ ./fah5 
bash: ./fah5: No such file or directory

fah5 is clearly in that directory, and I had already run chmod +x fah5

For some reason it seems like bash is interpreting ./fah5 as if it were a directory instead of it being the command to execute fah5.

Any ideas on why this is happening to me?

Btw, I am running a fresh install that has been updated, and it is running off a reiserfs partition.

---

### Post by taurus on 2007-01-30
What's the output of this command from a terminal?

```
ls -la ~/Folding
```

---

### Post by tux123 on 2007-01-30
Maybe you have mounted the partition with the noexec flag or with some other option like "user" or "users" which are also implying the noexec flag if you don't override it explicitly. So please check your fstab.

Regards
Christoph

---

### Post by dbott67 on 2007-01-30
Assuming the file is in the current directory and set to executable, you can try executing it using the following command:
```
sh ./fah5
```

-Dave

---

### Post by funnyperson1 on 2007-01-30
@taurus, here is the output from that
asohangh@bigblue:~/Folding$ ls -la ~/Folding
total 697
drwxr-xr-x  2 asohangh asohangh    168 2007-01-30 15:05 .
drwxr-xr-x 18 asohangh asohangh   1056 2007-01-30 15:52 ..
-rwxr-xr-x  1 asohangh asohangh 249556 2007-01-15 01:22 fah5
-rwxr-xr-x  1 asohangh asohangh 250964 2007-01-30 14:58 FAH504-Linux.exe
-rw-r--r--  1 asohangh asohangh 138226 2007-01-30 15:05 FAH_SMP_Linux.tgz
-rwx------  1 asohangh asohangh  68492 2006-11-21 11:12 mpiexec
asohangh@bigblue:~/Folding$ 

Both FAH504-Linux.exe and fah5 give the same results.

@tux123

Here is the line in my fstab regarding the root partition (where my home directory is)

UUID=e971b0ac-594b-4c10-a312-9bd428728f54 /               reiserfs notail          0       1


@dbott67

Here is what happens when I try to use sh ./fah5 or sh fah5

asohangh@bigblue:~/Folding$ sh ./fah5 
./fah5: 1: Syntax error: "(" unexpected

Thanks for the help guys!

---

### Post by taurus on 2007-01-30
```
file FAH504-Linux.exe
more fah5
```

---

### Post by funnyperson1 on 2007-01-30
Here is what I get after typing those commands:

asohangh@bigblue:~/Folding$ file FAH504-Linux.exe 
FAH504-Linux.exe: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.0.0, dynamically linked (uses shared libs), for GNU/Linux 2.0.0, stripped
asohangh@bigblue:~/Folding$ more fah5

******** fah5: Not a text file ********

asohangh@bigblue:~/Folding$

---

### Post by taurus on 2007-01-30
```

./FAH504-Linux.exe 

```

---

### Post by funnyperson1 on 2007-01-30
asohangh@bigblue:~$ cd Folding/
asohangh@bigblue:~/Folding$ file FAH504-Linux.exe 
FAH504-Linux.exe: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.0.0, dynamically linked (uses shared libs), for GNU/Linux 2.0.0, stripped
asohangh@bigblue:~/Folding$ more fah5

******** fah5: Not a text file ********

asohangh@bigblue:~/Folding$ ./FAH504-Linux.exe 
bash: ./FAH504-Linux.exe: No such file or directory
asohangh@bigblue:~/Folding$

---

### Post by funnyperson1 on 2007-01-31
Bump...any more ideas?

---

### Post by dbott67 on 2007-01-31
Just a wild guess here:

I notice on this page that there is a client for 32-bit linux & 64-bit linux.  The 64-bit version is beta 5.91, while the 32-bit version is 5.04 (same as what you posted above).
[http://folding.stanford.edu/download.html](http://folding.stanford.edu/download.html)

Can you try downloading the 64-bit version?

Disregard this post if I don't know what the heck I'm talking about.

-Dave

---

### Post by funnyperson1 on 2007-01-31
The 64 bit SMP version is fah5, and the 32 bit is FAH504Linux, both have the same issue, as does prime95's linux executable, and another executable that I need for school work that I apt-got.

I really believe this is something wrong with my Ubuntu install/cd I'm going to reboot and do the media check in a second.

---

### Post by funnyperson1 on 2007-02-01
Check was successful, all checksums matched.

Anyone have any other ideas, this is such an odd problem.

---

### Post by kpatz on 2007-02-01
How about $HOME/fah?  Does that work?

Obviously you can run binaries in directories in your path, otherwise things like ls wouldn't work.

Strange... maybe something's weird with your home directory (the "." entry missing or something).  If you copy the file to another location, can you run it from there?

If you type "ls -la ." what do you get?

---

### Post by dbott67 on 2007-02-01
[COLOR="Red"]THIS IS NOT THE SOLUTION.  SEE NEXT POST FOR ANSWER.[/COLOR]

[COLOR="Silver"]I'm wondering if this is one of those dash vs. bash problems that happens to 6.10 users.  Issue the following command in a terminal to display current shell:
```
echo $SHELL
```

*(borrowed & modified from **abmorissun**)*

After a clean install of Ubuntu 6.1, you'll have a Terminal application that uses **/bin/dash** by default instead of **bash** (which the FAH script may be expecting). I had this problem when I was trying to install the ATI proprietary binaries.

There are a few hacks out there, but this one seems less drastic:

In Terminal, click **Edit > Current Profile...**

On the "**Title and Command**" tab, under the "**Command**" section, select "**Run a custom command instead of my shell**".

Enter **/bin/bash** beside "Custom command:"

Close the dialog and restart your Terminal and try installing again.

-Dave

PS - Some further info regarding shells:

To see a list of all installed shells:
```
dbott@thedrake:~$ cat /etc/shells
# /etc/shells: valid login shells
/bin/ash
/bin/bash
/bin/csh
/bin/sh
/usr/bin/es
/usr/bin/ksh
/bin/ksh
/usr/bin/rc
/usr/bin/tcsh
/bin/tcsh
/usr/bin/zsh
/bin/sash
/bin/zsh
/usr/bin/esh
/bin/rbash
/usr/bin/screen

```

To change your shell for your login, use **chsh**:
```
dbott@thedrake:~$ chsh
Password:
Changing the login shell for dbott
Enter the new value, or press ENTER for the default
        Login Shell [/bin/bash]:

```[/COLOR]

---

### Post by dbott67 on 2007-02-01
Well, how's this for irony?  I was googling for "folding at home dash bash linux" and got this hit:
[http://ubuntuforums.org/archive/index.php/t-314483.html](http://ubuntuforums.org/archive/index.php/t-314483.html)

Heck, I was evening trying to help the guy (I don't remember doing it though!).  Anyhow, here's what he did to fix it:

> [B][I][COLOR="Blue"]dbott67
December 11th, 2006, 01:08 PM[/COLOR][/I][/B]
What command are you typing in?

Generally, you need to precede the command with ./

CD to your folding directory and type in:
./FAH504-Linux.exe

If that's what your already doing, then perhaps it may be related to the bash vs. dash issue that others have faced when running scripts that expect to see bash (I believe the developers have switched to dash instead of bash). I know it caused me grief when trying to install the ATI drivers.

This is the bash/dash hack:
Depending how recently updated your Edgy installation is, you may run into problems with the installer complaining about syntax errors. A recent Edgy update changed the shell sh from bash to dash. You will have to do some extra work on the command line by temporarily making the sh command redirect to bash instead.
1. Backup current shell & switch to bash:
sudo mv /bin/sh /bin/sh.bak
sudo ln -s /bin/bash /bin/sh
2. Run script:
./FAH504-Linux.exe
3. Restore dash as shell:
sudo mv /bin/sh.bak /bin/sh

or you can just try pre-pending the script with 'bash':
bash ./FAH504-Linux.exe

-Dave
> [COLOR="Blue"][B][I]Tintazul
December 11th, 2006, 06:24 PM[/I][/B][/COLOR]

Thanks, Dave! Your solution didn't solve the problem, but after much fussing and trying and searching the net, [COLOR="Red"]here's the answer - since my architecture is 64-bit, I have to install the 32-bit compatibility library ia32-libs[/COLOR]. It's now working fine! The solution was found on this thread of the Folding Community forum: 64 Bit Linux Needs 32 bit compatibility libraries? [YES] ([http://forum.folding-community.org/viewtopic.php?t=17223](http://forum.folding-community.org/viewtopic.php?t=17223))

The deanhopkins guy who started this thread had the same architecture upgrade, but I don't have MSN to let him know of the solution. He might have figured it out by now.

:D Thank you very much! You've helped someone who's not only fairly new to Linux, but also a virgin in terms of x64 architecture.

---

### Post by funnyperson1 on 2007-02-01
dbott you rock!  I am actually really surprised that this didn't come by default with Ubuntu x64.  But I got the ia32libs installed and now these 32 bit executables work fine,

Thank you to everybody for their help!

---

### Post by dbott67 on 2007-02-01
Glad it worked!

Now, if only my memory would work! :)

-Dave

---

