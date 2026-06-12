---
title: "How to restrict chown chmod"
date: 2017-03-30
forum: General Help
---

### Post by yeshan on 2017-03-30
Hi all,

We have restricted to a specific user (named roberto for the example) the use of chown/chmod to some directories with the sudoers file like this :

roberto   ALL=(ALL)       NOPASSWD:/bin/chown * /**directory1**/*,/bin/chmod * /**directory2**/*

When the user roberto tries to chown a file located in /tmp the user is prompted and the command fails which is the normal behaviour.
But recently, roberto tried the following :

sudo chown admroberto:admroberto /directory1/dev/common/temp/test.txt /tmp/test_chmod.txt

And both files in **/directory1/dev/common/temp/test.txt** and **/tmp/** have been modified which should not have been granted.

Is there a way to prevent roberto to chown somewhere else than directory1 and directory2 ?

Any help would be greatly appreciated because roberto changed all the owners and groups starting from /...

Thanx in advance

---

### Post by SeijiSensei on 2017-03-30
If admroberto has admin privileges and can use sudo, he or she can do anything anywhere.

If you don't grant roberto or admroberto any admin privileges, they can only change ownerships of files in their home directories and files they own in /tmp.  If you don't trust this user to do the right thing, then don't grant them sudo privileges at all.  Check that these usernames do not belong to the sudo group with:
```
groups roberto admroberto
```
If they have sudo rights, delete their account names from the sudo line in /etc/group 
```
sudo:x:27:roberto
```
and remove any entries for them in /etc/sudoers.

Root privileges are powerful and dangerous.  Don't grant them to anyone who doesn't need them regardless of how much they may claim that they do.

---

