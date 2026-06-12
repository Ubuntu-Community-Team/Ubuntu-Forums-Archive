---
title: "I can't import my thunderbird account!"
date: 2005-10-17
forum: General Help
---

### Post by fxgogo on 2005-10-17
I was running Vector Linux 5 and have just replaced it with ubuntu. I installed Thunderbird and followed the instructions to import my old thunderbird account into the new thunderbird. But when I start thunderbird and select the newly imported account from the profile manager, it says it can't open it because it is being used elsewhere. My username is the same and there is nothing else running. Am I doing something wrong, or is there a bug?

Thanks

---

### Post by ecobuntu on 2005-10-17
You want to add an account not import an account.  Try that.  I am assuming that you remove Vector and install Ubuntu in it's place, i.e. you didn't upgrade from Vector to Ubunt.  If that's the case then you need to add an account and don't import anything.

---

### Post by fxgogo on 2005-10-18
Yeah I replaced the vector OS completely. I just left my /home directory alone, which is on a seperate partition.

When I say import, I think I used the wrong language. My method for doing this is as follows:

[LIST]I open the profiles.ini file that sits in the .thunderbird directory in my home directory.[/LIST]
[LIST]I then manually add another profile as the mozilla site suggests here:[http://www.mozilla.org/support/thunderbird/profile#move](http://www.mozilla.org/support/thunderbird/profile#move)[/LIST]
[LIST]I save the file and then start thunderbird.[/LIST]

It is the the fact that it is saying it is being used by another program and can't open, that puzzles me. I thought this was a windows thing, that programs hold a file till the program quits.

---

### Post by fxgogo on 2005-10-19
Right, I got it solved. For some reason all the files and directories in my mail directory were write protected. I chmod'ed them all and Thunderbird fired up perfectly.

---

### Post by Rovenhot on 2005-10-19
I've seen many applications that do that.  Often when I'm messing with an app's files, it launches to say the file is read-only, which is the converse of your situation.  The message is incomplete.  It should say, "*** is read-only or is being used by another app."

---

