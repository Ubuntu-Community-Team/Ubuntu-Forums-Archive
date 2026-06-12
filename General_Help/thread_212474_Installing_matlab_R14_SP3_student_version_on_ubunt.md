---
title: "Installing matlab R14 SP3 student version on ubuntu 6.06"
date: 2006-07-09
forum: General Help
---

### Post by binney on 2006-07-09
I just spent all day figuring this out, and i didn't see any solution in the forums, so here goes:

When I install matlab on ubuntu 6.06 i run into a couple problems:
[LIST=1]
[*]Can't execute installation file directly from my cdrom (this problem has been addressed in several other threads on this forum.)

**Solution:** You can unmount and remount the drive with the correct permissions, but i had problems with this so i just copied the files to my hard drive.

[*]After installation, when the "activation" script should run automatically, the installer just closes. when i try to run matlab by typing "matlab" at the command prompt i get the following error:

> awk: program limit exceeded: sprintf buffer size=1020
        FILENAME="-" FNR=36 NR=36
Unrecognized option: -root
Could not create the Java virtual machine.

**Solution:** Ubunutu comes with "mawk" which has a compiled buffer size of 1020. This is too small for whatever matlab is trying to do. I used synaptic to install the "gawk" package.  I didn't uninstall mawk because it has other dependencies, but matlab must have used gawk the next time i ran it because it started without a hitch, and led me through activation process. Once that was done i ran matlab again and it started up with no problems. Hooray.
[/LIST]

---

### Post by Canuck on 2006-09-23
Hello,

I got around that by coying and pasting the contents of the CD into a temp file and executing the intall from there.

Canuck

---

### Post by 7he on 2006-10-03
Hi!!

when I tried to install from the cdrom, I got the following problem:

```

sudo /media/cdrom/install_unix.sh
sudo: unable to execute /media/cdrom/install_unix.sh: Permission denied

```

so I copied the files on my HDD

```

sudo /home/ant/Desktop/matlabtemp/install_unix.sh
-------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /home/ant/Desktop/matlabtemp/unix/update/install/main.sh: line 162: /home/ant/Desktop/matlabtemp/unix/update/bin/glnx86/xsetup: Permission denied

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . . .


```

Does someone have an idea?
Info: I have XGL and Beryl isntalled
Thanks!
7he

---

### Post by 7he on 2006-10-03
I tried the following...

```
cd /home/ant/Desktop/matlabtemp/
ant@antoine:~/Desktop/matlabtemp$ sudo install* -t
sudo: install_unix.sh: command not found
ant@antoine:~/Desktop/matlabtemp$

```

But....

7he

---

### Post by 7he on 2006-10-03
Allright!
The problem is resolved, here is what I did:

Copy all files into a temp fir on my HDD.
Changing permissions of:

install_unix.sh
/unix/install
/unix/bin/
/unix/update/install/main.sh
/unix/update/bin/glnx86/xsetup

I clicked on properties --> permissions --> read write execute

Then I simply executed install_unix.sh


Enjoy!!!

---

### Post by mechengineer on 2008-03-23
> **binney said:**
> [list]
[*]After installation, when the "activation" script should run automatically, the installer just closes. when i try to run matlab by typing "matlab" at the command prompt i get the following error:



**Solution:** Ubunutu comes with "mawk" which has a compiled buffer size of 1020. This is too small for whatever matlab is trying to do. I used synaptic to install the "gawk" package.  I didn't uninstall mawk because it has other dependencies, but matlab must have used gawk the next time i ran it because it started without a hitch, and led me through activation process. Once that was done i ran matlab again and it started up with no problems. Hooray.
[/LIST]

This is fantastic!  I spent hours pulling out my hair trying to figure out just what the problem was.  To be honest, I was mere minutes from saying "screw Ubuntu" all together and installing the Windows version of Matlab instead.  Thanks a million :)

---

