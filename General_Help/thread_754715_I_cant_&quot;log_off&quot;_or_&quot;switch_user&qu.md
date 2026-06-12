---
title: "I cant &quot;log off&quot; or &quot;switch user&quot; :("
date: 2008-04-14
forum: General Help
---

### Post by harrybazeegar on 2008-04-14
Hi all
I am running Ubuntu Fiesty.
Whenever I tr to log off my session or just switch to another user my screen goes black and blank, and my computer freezes over.

so
1. is there any way to fix this?
2. or, is there any command line way of doing this? I dont mind command line at all....
3. how do I identify what is wrong? what logs do I look into?]

cheers

---

### Post by GCoffee on 2008-04-14
When did you install fiesty? If it was a while ago try upgrading to 7.10 Gutsy Gibbon. I'm not sure if there is a upgrade feature in fiesty but if there is use run application and put in this command: *update-manager --devel-release* I think that is it. It should open the update manager and at the top of the window there should be release upgrade or something of the sort. 

To open run application I think it is either Alt+f2 or f2. Sorry. I can't check my ubuntu PC is in for upgrade.

---

### Post by harrybazeegar on 2008-04-14
well my upgrade is another intersting story...
when I try to upgrade, the update manager downloads all the files, starts doing some stuff,
and suddenly breaks down in the middle of the process.
I just dont know why... I posted the problem to Launchbag, but to no avail :(

so is there any command line way of logging off? or switching the user??

---

### Post by Junglizer on 2008-04-14
```
logout
```
```
su - <user>
```
or if you just want root ```
su -
```
or if you want root permissions with your current user ```
su
```

(su for Switch User)

---

### Post by harrybazeegar on 2008-04-14
oops.. sorry for the confusion:
I meant a command line way of logging off my X session ( my GUI session )

or a command line way to switch the user on my GUI, not the command line.


Alternatively, can I start a GUI session on one the other what-do-you-call-ems ( ctrl+alt+f1 ) ?? may be use startx or some??

---

