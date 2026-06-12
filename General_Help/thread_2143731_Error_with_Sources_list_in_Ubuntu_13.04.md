---
title: "Error with Sources list in Ubuntu 13.04"
date: 2013-05-09
forum: General Help
---

### Post by KarkenSyn on 2013-05-09
Soooo...
I was trying to install skype (which is now completed, so this is now irrelevant), but when I was adding the archive.canonical.com repository to install Skype, it apparently caused an error in the Sources.list file (/etc/apt/sources.list) that prevented me from using apt-get, Ubuntu Software Center, and the Software and Updates manager (system settings). I managed to fix this error so now I can use apt-get commands again, but now I still can't use Ubuntu Software Center or the Software and Updates manager (system settings) and I get the following error message every time I turn on my laptop:
"Opening the Cache (E:Opening /etc/apt/sources.list - ifstream::ifstream (13: Permission Denied), E:The list of sources could not be read., E:The package lists or status file could not be parsed or opened.) This usually means that your installed packages have unmet dependencies"

I am using Ubuntu 13.04 and if it's relevant, I recently removed some libraries using the Remove Orphaned Packages app.

I DON'T KNOW WHAT TO DO TO FIX THIS PLEASE HELP.

---

### Post by gnusci on 2013-05-09
Try with these commands:

$ sudo rm /var/lib/apt/lists/* -vf
$ sudo dpkg --clear-avail
$ sudo rm /var/lib/apt/lists/* --force
$ sudo dpkg --configure -a
$ sudo reboot

They worked for me in a similar situation, but I cannot promise the will work for you, but they are safe, if still you have problems after restart, run them again until everything work.

---

### Post by KarkenSyn on 2013-05-09
Tried 3 times. It didn't work. with both instances of the rm command, I get "cannot remove 'var/lib/apt/lists/partial', is a directory." Is that relevant?

---

### Post by plucky on 2013-05-10
> **KarkenSyn said:**
> Tried 3 times. It didn't work. with both instances of the rm command, I get "cannot remove 'var/lib/apt/lists/partial', is a directory." Is that relevant?

It is a directory,so those commands will not be able to remove it as they will only delete files.

Post output for ```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list
sudo apt-get update
```

Good Luck

---

### Post by ibjsb4 on 2013-05-10
This should work

```
sudo rm -r /var/lib/apt/lists/* 
sudo mkdir /var/lib/apt/lists/partial 
sudo apt-get update
```

---

### Post by KarkenSyn on 2013-05-10
> **plucky said:**
> It is a directory,so those commands will not be able to remove it as they will only delete files.

Post output for ```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list
sudo apt-get update
```

Good Luck
When I ran sudo apt-get update, I got the following message at the last line:
"E: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release: The following signatures were invalid: NODATA 1 NO DATA 2"
What does that mean?

---

### Post by KarkenSyn on 2013-05-10
> **ibjsb4 said:**
> This should work

```
sudo rm -r /var/lib/apt/lists/* 
sudo mkdir /var/lib/apt/lists/partial 
sudo apt-get update
```

When I tried apt-get update, I got the following error message:
"E: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release: The following signatures were invalid: NODATA 1 NODATA 2

---

### Post by matt_symes on 2013-05-10
Hi

```
"E: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release: The following signatures were invalid: NODATA 1 NODATA 2
```

That does not look right.

Open a terminal and copy and paste this into it

```
grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
```

Post the output back here by copying and pasting from the terminal (highlight text -> right click -> copy) and paste into you next post between code tag.

To use code tags, highlight the text in your post and hit the # button above where you type your reply.

You may have an invalid ppa entry.

Kind regards

---

### Post by alvin-norin on 2013-11-06
Hey, got the same problem.. But solved it! :) Type this in the terminal:) -->

sudo rm -rf /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists
sudo apt-get clean # Not sure if this will help or not, but it can't hurt
sudo apt-get update

---

