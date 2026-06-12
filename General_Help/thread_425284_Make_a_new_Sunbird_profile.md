---
title: "Make a new Sunbird profile?"
date: 2007-04-27
forum: General Help
---

### Post by martal on 2007-04-27
I installed Sunbird successfully using this thead:
[http://ubuntuforums.org/showthread.php?t=278206&highlight=install+sunbird](http://ubuntuforums.org/showthread.php?t=278206&highlight=install+sunbird)

It's in /opt. sunbird.sh runs the app.

How can I run from the command line to get the profile manager? In XP, add ' -P'. I can't find the right executable to run this against.

---

### Post by phact0rri on 2007-08-02
This is an old post, but when I was searching for the answer to this question, this was the first response I got on google, so I hope people don't mind me resurrecting a dead post.  If ya do I'm sorry.

There might be something I am missing to get to the profile manager in Sunbird, on the linux build but after trying "-p"  "-profile" and "-profilemanger" triggers none of them worked, so instead (since I knew it existed) I changed the profile.ini to have a second profile, there in to make it display the manager where I properly made a profile that would link to my shared.

what I did was the following.

in terminal

```
 sudo gedit ~/.mozilla/sunbird/profiles.ini
```

next in the profiles ini file add this to the bottom of the document

```

[Profile1]
Name=default
IsRelative=1
Path=media/nothing/here

```

Save.

as you can guess you can put anything there.  when you load up Sunbird, it'll flash up the profile manager.  you can clear out the "dupe" profile and create your own one, for the new profile.

To me I still think there's another way to bring it up, I just failed at finding out what it is.  so this'll work til there's a better answer.

---

