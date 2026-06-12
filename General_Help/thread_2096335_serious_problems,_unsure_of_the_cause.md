---
title: "serious problems, unsure of the cause"
date: 2012-12-19
forum: General Help
---

### Post by daniel.cotter on 2012-12-19
Ubuntu 12.04:

Today when I logged in, I found a "Do Not Enter" symbol on the taskbar with the following message when clicked:

```
An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.  
The Error message was: 'Error: Opening the cache (E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/
archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened)'.
This usually means that your installed packages have unmet dependencies
```Below those words are links to Show updates, Install all Updates and Check for Updates.  Clicking Show Updates, it opens a dialog box saying: ```
Could not initialize the package information.
An unresolvable problem occurred while initializing the package information.

Please report this bug against the "update-manager" package and include the following error message: (then it repeats the same message seen in parenthesis in  the error noted above)
```Clicking on Install all updates, from that same error dialog, I get an error message from backend_helper.py, saying:```

Failed to load the package list.  This is a serious problem. Try again later. If this problem appears again, please report an error to the developers,  Details reveal the same error message again as noted in the first box
```Clicking Check for Updates produces a dialog box containing this error:
```
Invalid Problem Report
Could not determine the package or source package name
```Trying to open synaptic, to see if a recent update (yesterday) may be the cause, the same or very similar error is given and it crashes.

I updated the linux header files presented by the update manager yesterday, but restarted afterward with no immediate occurrence of this error.

Probably also related is that I cannot open the Software Center, it just crashes.

Any suggestions where to start poking around?

Thanks

---

### Post by Bashing-om on 2012-12-19
daniel.cotter; Hi !

Before the poking around stage, I suggest you clean the system up. Here is oldfred's methology: From the terminal and in order given:
#houseclean
```
 sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean
```#refresh
```
 sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
All that does is update it again.
```After all that is done, see what errors are generated (none ?)
```
sudo apt-get update
sudo apt-get upgrade

```[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by daniel.cotter on 2012-12-19
Just looked into this and found your reply  (thank you)

Here is the output of the first command:

```
daniel@daniel-Pangolin:~$ sudo apt-get autoclean
[sudo] password for daniel: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
daniel@daniel-Pangolin:~$
```

---

### Post by daniel.cotter on 2012-12-19
When all these cleanup utilities were failing, I searched the Internet  for other answers, and found a very simple solution that has already  been worked out:

[http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-error-when-trying-to-do-an-update](http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-error-when-trying-to-do-an-update).

So thank you for reading this, and thanks a bunch,  Bashing-om, for your suggestions.

Daniel

---

### Post by Bashing-om on 2012-12-19
Hey, not a problem, We are all in this together !

Please mark this thread as solved:
a) aides others seeking a solution -
b)saves us helpers time NOT looking at a resolved situation.

[INDENT][INDENT]happy ubuntu'n < == BDQ

[/INDENT][/INDENT]

---

