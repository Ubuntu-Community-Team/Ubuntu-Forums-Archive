---
title: "Gnucash Root account is now visible"
date: 2007-12-27
forum: General Help
---

### Post by raid996 on 2007-12-27
Hello

I recently formatted my laptop, I had installed ubuntu 7.04 with gnome of course, and I used a lot gnucash for tracking my church finances. I had to format my hdisk, so I backed up all my data (home folder) with all my gnucash data.

After I formated I installed Xubuntu 7,10 wich is great for me cuz I use an old Ibook g4. Everything works great and faster. I just have one problem, after I opened my gnucash data I have this "root account" visible in my accounts tree. It really bothers me, because I somehow know I can't touch it, I would like just to make it somehow invisible. It has modified all my accounts like this:

Root Account:entries:sunday offerings

Whereas before I just had 

Entries:sunday offerings

Anyone can help me because I need to show this finances to my pastor and this root account thing is going to drive him crazy.

Thanks!:KS

---

### Post by rbmorse on 2007-12-28
I dunno what the link is about, either, but the fix for the Gnucash issue is to highlight the account you want (in this case entries:sunday offerings) in the account list, select edit > edit account and in the box on the lower right labelled "parent account" select either "new top level account" or other option as you desire then click on "ok."  

You have to do this for each account you want to put back the way it was. and then you can delete the now superfluous top level accounts created by the version switch.  

If the account in question is more than one level below the top level account, you still only need to edit the first account below top level account...the rest of the accounts in that tree will follow.

This is a lot more confusing to read than it is to do, but please feel free to ask if you have more questions, and please excuse the jerk, who in addition to being unhelpful didn't even understand the question.

---

### Post by 50words on 2007-12-28
You should only have to do this once, as the newest version seems to have addressed the problem. I actually think it had something to do with their porting GnuCash to Windows, as the problem appeared with the first Windows release, and disappeared after the first update to the Windows release. (I use GnuCash in both with the same account file.)

---

### Post by raid996 on 2007-12-29
Ok guys I solved the issue with your help. Ubuntu comunity ROCKS!!!!

:popcorn:HAPPY NEW YEAR AND THANK YOU SO MUCH

---

### Post by rbmorse on 2007-12-29
I love happy endings

---

