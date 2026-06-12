---
title: "dsh for multiple commands with passwords"
date: 2016-04-30
forum: General Help
---

### Post by cmcanulty on 2016-04-30
I have been reading about dsh and it seems as though I could automate several tasks across multiple servers using it.
 I have an alias script for each server to run update by typing ud and to run dist upgrade by typing dug
 What I would like to do is open one server and type
```
 dsh -a ud 
```
To update all servers remotely and have the password pre entered as it is on the local bash.rc files  This would only be run internally on a local network so security isn't an issue (I think) but after that I am not having any luck even without the alias using the regular 
```
dsh -a sudo apt-get update
```
 I have the /etc/dsh/machines.list file set up with each server in the form of librarian@192.168.1.*** 
So I need some help on this using the aliases would be nice but not essential. I need to do about 12 computers with these commands. Do I need dsh installed on all or only the one I am working from? What is wrong with the commands I am typing I would sure like the passwords (all the same) pre-entered. Thank you.

---

