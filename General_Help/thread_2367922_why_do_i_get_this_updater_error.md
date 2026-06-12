---
title: "why do i get this updater error?"
date: 2017-08-04
forum: General Help
---

### Post by ronjjjg8885 on 2017-08-04
Image replaced.

---

### Post by Bashing-om on 2017-08-04
ronjjjg8885; Hello;

The error may have several causes .
A likely thought at this time is that google-chrome has not updated .
Verify what the error is ;
Post back - between code tags - the output of terminal command:
```

sudo apt update

```

[INDENT][INDENT]see what tale gets told
[/INDENT][/INDENT]

---

### Post by lisati on 2017-08-04
What version and flavour of Ubuntu are you using?

---

### Post by BenginM on 2017-08-05
Well , are you sure the machine is connected to the internet.. are there third-party PPAs enabled in your /etc/apt/sources.list !

---

### Post by ronjjjg8885 on 2017-08-05
> **Bashing-om said:**
> ronjjjg8885; Hello;

The error may have several causes .
A likely thought at this time is that google-chrome has not updated .
Verify what the error is ;
Post back - between code tags - the output of terminal command:
```

sudo apt update

```[INDENT][INDENT]see what tale gets told
[/INDENT]
[/INDENT]


```
Ign:1 http://il.archive.ubuntu.com/ubuntu xenial InReleaseIgn:2 http://il.archive.ubuntu.com/ubuntu xenial-updates InRelease
Ign:3 http://il.archive.ubuntu.com/ubuntu xenial-backports InRelease
Err:4 http://il.archive.ubuntu.com/ubuntu xenial Release                       
  503  Service Unavailable
Err:5 http://il.archive.ubuntu.com/ubuntu xenial-updates Release               
  503  Service Unavailable
Err:6 http://il.archive.ubuntu.com/ubuntu xenial-backports Release             
  503  Service Unavailable
Hit:7 http://security.ubuntu.com/ubuntu xenial-security InRelease        
Hit:8 http://ppa.launchpad.net/eugenesan/ppa/ubuntu xenial InRelease
Hit:9 http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu xenial InRelease
Hit:10 http://ppa.launchpad.net/unit193/encryption/ubuntu xenial InRelease
Reading package lists... Done                      
E: The repository 'http://il.archive.ubuntu.com/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://il.archive.ubuntu.com/ubuntu xenial-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://il.archive.ubuntu.com/ubuntu xenial-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.



```

16.04 lts

---

### Post by vasa1 on 2017-08-05
Try with the main server (US) instead of IL.

---

### Post by BenginM on 2017-08-05
What is the contents of cat /etc/apt/sources.list .. and cat /etc/resolv.conf ! are you connected with IPv6?

---

### Post by ronjjjg8885 on 2017-08-05
it works thank you
ill mark that solved

i switched to the main servers and that what made it working

edit:
i can't find how to make the thread flagged as solved

---

### Post by ronjjjg8885 on 2017-08-05
> **BenginM said:**
> are you connected with IPv6?


i think so

---

### Post by vasa1 on 2017-08-05
> **ronjjjg8885 said:**
> ...
i can't find how to make the thread flagged as solved

Here: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by alexpag on 2017-08-05
Same problem here with ubuntu mate 16.04.3 I cannot update no matter which server I use. My internet connection works fine.

All packages are up to date.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release:

Any thoughts?

---

### Post by vasa1 on 2017-08-05
> **alexpag said:**
> I [COLOR=#000000] do not have permission to access this page. [/COLOR]

Sorry, my bad! Run```
wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | sudo apt-key add -

```and you should be fine.

---

### Post by alexpag on 2017-08-05
Thank you very much it worked!:)

---

### Post by ronjjjg8885 on 2017-08-12
by the way.
the updater worked for a week but now there is a similar message even while connecting to the main server.

did you solved it with alexpag?

---

### Post by vasa1 on 2017-08-12
> **ronjjjg8885 said:**
> by the way.
the updater worked for a week but now there is a similar message even while connecting to the main server.

did you solved it with alexpag?

"Similar message" isn't enough! Please provide the exact message you get with *sudo apt-get update*.

---

### Post by ronjjjg8885 on 2017-08-13
```
sudo apt-get update[sudo] password for ron: 
Hit:1 http://ppa.launchpad.net/eugenesan/ppa/ubuntu xenial InRelease
Hit:2 http://archive.ubuntu.com/ubuntu xenial InRelease                  
Hit:3 http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu xenial InRelease
Hit:5 http://ppa.launchpad.net/unit193/encryption/ubuntu xenial InRelease
Err:1 http://ppa.launchpad.net/eugenesan/ppa/ubuntu xenial InRelease
  Could not execute 'apt-key' to verify signature (is gnupg installed?)
Err:2 http://archive.ubuntu.com/ubuntu xenial InRelease
  Could not execute 'apt-key' to verify signature (is gnupg installed?)
Get:4 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Err:3 http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu xenial InRelease
  Could not execute 'apt-key' to verify signature (is gnupg installed?)
Err:5 http://ppa.launchpad.net/unit193/encryption/ubuntu xenial InRelease
  Could not execute 'apt-key' to verify signature (is gnupg installed?)
Get:6 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Err:4 http://archive.ubuntu.com/ubuntu xenial-updates InRelease
  Could not execute 'apt-key' to verify signature (is gnupg installed?)
Get:7 http://archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Err:6 http://archive.ubuntu.com/ubuntu xenial-backports InRelease
  Could not execute 'apt-key' to verify signature (is gnupg installed?)
Err:7 http://archive.ubuntu.com/ubuntu xenial-security InRelease
  Could not execute 'apt-key' to verify signature (is gnupg installed?)
Fetched 306 kB in 1s (238 kB/s)
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://ppa.launchpad.net/eugenesan/ppa/ubuntu xenial InRelease: Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com/ubuntu xenial InRelease: Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu xenial InRelease: Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://ppa.launchpad.net/unit193/encryption/ubuntu xenial InRelease: Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com/ubuntu xenial-updates InRelease: Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com/ubuntu xenial-backports InRelease: Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com/ubuntu xenial-security InRelease: Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-security/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/eugenesan/ppa/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://ppa.launchpad.net/unit193/encryption/ubuntu/dists/xenial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Some index files failed to download. They have been ignored, or old ones used instead.



```

here it is
thanks

---

### Post by vasa1 on 2017-08-13
Obvious question: do you have *gnupg* installed?

What does the output of ```
apt policy gnupg
```show?

And what does the output of```
apt-key list
```show?

---

### Post by ronjjjg8885 on 2017-08-13
```
apt policy gunpgN: Unable to locate package gunpg



```

---

### Post by vasa1 on 2017-08-13
Sorry! gnupg not gunpgN! Please try both commands. I added one more.

---

### Post by ronjjjg8885 on 2017-08-13
```
apt policy gnupg.gnupg:
  Installed: 1.4.20-1ubuntu3.1
  Candidate: 1.4.20-1ubuntu3.1
  Version table:
 *** 1.4.20-1ubuntu3.1 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1.4.20-1ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages



```

```
apt-key listSegmentation fault (core dumped)



```

the last command opened an error window too. but i could not copy this message.

---

### Post by vasa1 on 2017-08-13
I get the same output as you did for *apt policy gnupg* but *apt-key list* works for me. I don't know what to suggest now. Sorry!

---

### Post by ronjjjg8885 on 2017-08-13
thanks anyway

---

### Post by Bashing-om on 2017-08-13
ronjjjg8885; Hey;

What results from terminal command:
```

sudo apt-key update

```
Can you capture error messages to give us a hint where the failure occurs ?

Replace the corrupted files ?

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by ronjjjg8885 on 2017-08-13
the problem with my ubuntu broadened so i opened a new thread for solving it.

---

