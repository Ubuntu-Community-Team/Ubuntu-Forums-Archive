---
title: "computertemp and Synaptic Package Manager"
date: 2007-05-21
forum: General Help
---

### Post by Robert Leithe on 2007-05-21
I'm having problems installing new packages. When I start Synaptic Package Manager I get this message:

[B]E: The package computertemp needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.[/B]

And when I clicked the Updates Available icon (at my upper right corner of the screen) I get this:

[B]Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package computertemp needs to be reinstalled, but I can't find an archive for it.'[/B]

The closest thing I found in the forum are these threads:
[http://ubuntuforums.org/showthread.php?t=445714&highlight=Internal+error+opening+cache](http://ubuntuforums.org/showthread.php?t=445714&highlight=Internal+error+opening+cache)
[http://ubuntuforums.org/showthread.php?t=438039&highlight=Internal+error+opening+cache](http://ubuntuforums.org/showthread.php?t=438039&highlight=Internal+error+opening+cache)
[http://ubuntuforums.org/showthread.php?t=398709](http://ubuntuforums.org/showthread.php?t=398709)

However, none of them really helped me out. The first one hits the spot, but there are no solution available.
The other to have the same problem, but with Virtual Box. Being fairly new to Linux I wouldn't want to try the solution on my computer without knowing it could be used.

Sincerely

EDIT: I'm having problems with overheating, and thus I installed computertemp recently. That's where this software comes from I guess.

---

### Post by DoctorMO on 2007-05-21
try removing it first, it sounds like an error in the repositories.

once removed, reinstall it; it might be best to do this from the command line:

```
sudo apt-get remove computertemp
```
```
sudo apt-cache search computertemp
```

then if it's still called computertemp

```
sudo apt-get install computertemp
```

---

### Post by infinito on 2007-05-21
computertemp is not on Ubuntu Feisty repos, it's only on Gutsy ones.
Install it downloading the .deb from here:
[http://prdownload.berlios.de/computertemp/computertemp_0.9.6.1-0ubuntu1_all.deb](http://prdownload.berlios.de/computertemp/computertemp_0.9.6.1-0ubuntu1_all.deb)

---

### Post by Robert Leithe on 2007-05-21
@DoctorMO
The output from the commands you suggested:
[B]robert@C-3PO:~$ sudo apt-get remove computertemp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package computertemp needs to be reinstalled, but I can't find an archive for it.
robert@C-3PO:~$ sudo apt-cache search computertemp
computertemp - 
robert@C-3PO:~$ sudo apt-get install computertemp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package computertemp needs to be reinstalled, but I can't find an archive for it.
robert@C-3PO:~$ [/B]

@infinito:
Upon downloading and "executing" the file you link to I receive this message:
[B]Could not open 'computertemp_0.9.6.1-0ubuntu1_all.deb'''

The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.[/B]

Before I tried this, I ran the two first steps from DoctorMO's explanation.
I also tried chmod 777 on the file after it failed, but receive the same error.

Robert

---

### Post by infinito on 2007-05-21
Try this:
sudo dpkg -i computertemp_0.9.6.1-0ubuntu1_all.deb

---

### Post by Robert Leithe on 2007-05-21
Here's the result:

[B]robert@C-3PO:~$ sudo dpkg -i computertemp_0.9.6.1-0ubuntu1_all.deb
Password:
dpkg: error processing computertemp_0.9.6.1-0ubuntu1_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 computertemp_0.9.6.1-0ubuntu1_all.deb
robert@C-3PO:~$[/B]

---

### Post by infinito on 2007-05-21
You should run that command on the dir you have downloaded the computertemp .deb.

Complete command should be:
```
$ wget http://download.berlios.de/computertemp/computertemp_0.9.6.1-0ubuntu1_all.deb
$ sudo dpkg -i computertemp_0.9.6.1-0ubuntu1_all.deb
```

---

### Post by Robert Leithe on 2007-05-21
Here's the output:

[B]robert@C-3PO:~/Downloads$ wget [http://download.berlios.de/computertemp/computertemp_0.9.6.1-0ubuntu1_all.deb](http://download.berlios.de/computertemp/computertemp_0.9.6.1-0ubuntu1_all.deb)
--21:06:55--  [http://download.berlios.de/computertemp/computertemp_0.9.6.1-0ubuntu1_all.deb](http://download.berlios.de/computertemp/computertemp_0.9.6.1-0ubuntu1_all.deb)
           => `computertemp_0.9.6.1-0ubuntu1_all.deb'
Resolving download.berlios.de... 195.37.77.141
Connecting to download.berlios.de|195.37.77.141|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 50,434 (49K) [application/x-download]

100%[====================================>] 50,434        27.17K/s             

21:06:58 (27.12 KB/s) - `computertemp_0.9.6.1-0ubuntu1_all.deb' saved [50434/50434]

robert@C-3PO:~/Downloads$ sudo dpkg -i computertemp_0.9.6.1-0ubuntu1_all.deb
Password:
(Reading database ... 
dpkg: serious warning: files list file for package `computertemp' missing, assuming package has no files currently installed.
106564 files and directories currently installed.)
Preparing to replace computertemp 0.9.6.1-0~getdeb1 (using computertemp_0.9.6.1-0ubuntu1_all.deb) ...
Unpacking replacement computertemp ...
Setting up computertemp (0.9.6.1-0ubuntu1) ...

robert@C-3PO:~/Downloads$[/B]

The problem is now solved! I can access Synaptic Package Manager normally, and the Software Update functions like clockwork!

Thank you for your help :)

Sincerely

---

### Post by infinito on 2007-05-21
You're welcome!

---

### Post by saintlostone on 2007-10-31
hey, I'm posting b/c I have issues with computertemp.  I am a total newb.  How do you access computertemp once you have used the synaptec package manager to install it?

Also, the packet manager didn't auto-install any dependencies like it has done for all the software I downloaded before computertemp.  Does this mean I already have the dependencies required or that I need to find them manually?

Ty (in advance) for all help   you ubuntu ppl are great!

---

### Post by jocku on 2008-02-26
> **saintlostone said:**
> hey, I'm posting b/c I have issues with computertemp.  I am a total newb.  How do you access computertemp once you have used the synaptec package manager to install it?

Also, the packet manager didn't auto-install any dependencies like it has done for all the software I downloaded before computertemp.  Does this mean I already have the dependencies required or that I need to find them manually?

Ty (in advance) for all help   you ubuntu ppl are great!

I had the same problem. The thing is that you have to add computertemp to your panel. You can right-click on your panel at the bottom, choose 'add to panel' and add 'computer temperature monitor'.

---

