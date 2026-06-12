---
title: "unable to execute /usr/bin/apt-get: Argument list too long"
date: 2018-11-05
forum: General Help
---

### Post by hashxix on 2018-11-05
Hello,

  I am trying to install a list of software with the following command:
  ```
sudo apt-get install $(cat installed_software.txt)

```  But I receive an error message:
  ```
sudo: unable to execute /usr/bin/apt-get: Argument list too long

```  Can anyone help me solve this problem? Thanks!

  (Oh, and I have also tried:

  ```
xargs -rxa installed_software.txt -- sudo apt-get install --

```  With no success). 

     

What should I do?

---

### Post by TheFu on 2018-11-05
Break up the file.   **Argument list too long** is the error.  You can't feed hundreds of packages into a single shell command line.

You might want to look at **dpkg --set-selections** or **apt-mark** instead.  I use those in my backup/restore process.  The manpages are great.  With dpkg, you'll still need to use a tool like aptitude to actually do the installs after they've been added to the list to be installed internally in the APT db.

---

### Post by hashxix on 2018-11-05
Thanks, gonna read the man entries for those commands you've mentioned. 

None of the ways I've tried so far worked... Such as the ones mentioned above and the ones below:

sudo apt-get install < installed_software.txt

and 

sudo su
apt-get install $(cat installed_software.txt)

---

### Post by hashxix on 2018-11-05
When I try running as root, the follow message appears:

E: Unsupported file /proc given on commandline
E: Unsupported file /proc given on commandline
E: Unsupported file /dev/ given on commandline
E: Unsupported file /usr/share/dict given on commandline
E: Unsupported file /usr/share/dict given on commandline

I don't get it. Gonna try the options you just mentioned.

---

### Post by hashxix on 2018-11-05
Breaking it down solved the 'too many arguments' problem, so I will mark this as solved. But I think there is a problem with my .txt package backup, I simply can't do it. Thanks anyway!

---

### Post by TheFu on 2018-11-05
I use **apt-mark** to get a list of manually installed packages before every backup and storage that in a place that gets backed up daily.  Previously, I used **dpkg --get-selections**, but that was getting all the packages, not just the manually installed ones.

There is a limit as to how many characters can be entered on a command line.  I think it is 4Kb, but it depends on the shell you use.  That's why the $(cat whatever) wasn't going to work.  It gets expanded and looks like a really long list on the shell input for apt-get.  If you split the file up (use the "split" command or there are many other text processing methods), then you could feed them in a group at a time.

The easiest answer is a global search and replace in the text file that puts **sudo apt-get -y install** in front of every line.  Be certain to replace all spaces with \n first, so each package is on a separate line.  That's 1 command in vim.

Or just learn to use apt-mark and aptitude.  There are lots of examples. Google finds them.

---

