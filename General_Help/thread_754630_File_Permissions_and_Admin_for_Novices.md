---
title: "File Permissions and Admin for Novices"
date: 2008-04-14
forum: General Help
---

### Post by Doughy on 2008-04-14
Does anyone have a suggestion for how to make file permissions, owners, groups, and other admin operations easy for novice users that can't use the command prompt?

First of all, if an admin user wants to manage another user's account, how can they do so with a GUI without going to the command line?  The only way that I can see this working easily is if the admin user does a "sudo nautilus" to pull open the GUI in admin mode.  It seems like there should be a very simple and easy way for admins to unlock other peoples directories and the files to which they are not owners.  Even though the command line is easy, the minute I tell someone "go to the command prompt and type..." they immediately start judging linux as being cryptic and user unfriendly.  I am trying to find a solution to some of these basic issues so that people won't be turned off.

Does Ubuntu 8.04 have anything that addresses this issue?  Seems like Nautilus needs an "unlock" button or something, but I didn't see one when I tried the 8.04 beta from the liveCD.

---

### Post by aysiu on 2008-04-14
The command should be ```
gksudo nautilus
``` not *sudo nautilus*, but I don't see what the point of this is. The whole point of having separate user accounts is that they're separate. If someone is "administering" other people's accounts, she should have at least enough know-how to create a launcher or keyboard shortcut for *gksudo nautilus*

---

### Post by sekinto on 2008-04-14
First of all, you should always use "gksudo" instead of "sudo" for GUI applications. So you would want to use "gksudo nautilus". You could always tell them how to create a startup script that they can put on their desktop. It would just be a simple one liner.

---

### Post by ayoli on 2008-04-14
For graphical apps, prefer gksudo instead of sudo. IMO, the best gui way to admin files is 
```
gksudo nautilus
```
and to edit file as admin :
```
gksudo gedit
```
It can also help to have these commands set as launchers (eg on the panel)

---

### Post by warp99 on 2008-04-14
Actually it should be 'gksudo nautilus' and you can run it from the run command dialog or make a desktop file with the command string or place the file it in the menu with the string. 

As for using the command line and turning "people off' that's a personal problem since many operations with the command line are much faster and more efficient then using a GUI. I like to get thing done, not wade through endless dialog boxes asking me to "Cancel or Allow?

---

### Post by ayoli on 2008-04-14
> **aysiu said:**
> The whole point of having separate user accounts is that they're separate. If someone is "administering" other people's accounts, she should have at least enough know-how to create a launcher or keyboard shortcut for *gksudo nautilus*
Fully agree on these 2 points.

---

### Post by Doughy on 2008-04-14
You guys aren't understanding the essence of my question. Let me use my sister as an example.

She is a mother of 3 kids, all of who she wants to set up with accounts on her computer.  Sometimes she wants to be able to share files with other users, or be able to access their files. She is a smart person, but is intimidated a little by the command prompt, and it's a major barrier that keeps her from feeling at home in Ubuntu.

Now, you guys can say that someone who manages another account should "at least know how to do some simple things on the command line."  Fact of the matter is, there are people out there who will always be intimidated by the command prompt. We are talking about families and basic users here, not business IT admins.

I'm sold on linux and I will use it for everything I do, but as I try to convert non-techie type people to it, certain things need to be addressed appropriately.  This is one of them.  Telling them to buck up isn't the answer.

---

### Post by sekinto on 2008-04-14
We said you can make a simple "gksudo nautilus" launcher so all you have to do is click it and type in your password in a nice little password dialog box. From there you can use nautilus to change the permissions of files, move them, copy them, et cetera.

---

### Post by Doughy on 2008-04-14
> **sekinto said:**
> We said you can make a simple "gksudo nautilus" launcher so all you have to do is click it and type in your password in a nice little password dialog box. From there you can use nautilus to change the permissions of files, move them, copy them, et cetera.

That's still somewhat cryptic to novice users though.  The first thing they will be thinking is "what is gksudo? and why do I have to type some phrase that I don't understand to be able to get to my kids files?"  First time ubuntu users should be able to do something like this without having to consult with someone who knows what they are doing.

---

### Post by sekinto on 2008-04-14
Okay, I really don't know how to make this any more understandable.

1) Right click desktop and click "create launcher".
2) Type in a name, anytihng will do, "Computer", "Filesystem", anything that makes sense to the user.
3) In the command field type "gksudo nautilus /home".
4) Select a different icon if they want to use one.
5) Now they will never have to worry about it again, they just have to click the icon on their desktop... doesn't seem cryptic to me. You could probably even make the launcher file for them and send it to them if they couldn't understand those simple instructions.

---

### Post by ayoli on 2008-04-14
> **Doughy said:**
> You guys aren't understanding the essence of my question. Let me use my sister as an example.

She is a mother of 3 kids, all of who she wants to set up with accounts on her computer.  Sometimes she wants to be able to share files with other users, or be able to access their files. She is a smart person, but is intimidated a little by the command prompt, and it's a major barrier that keeps her from feeling at home in Ubuntu.

Now, you guys can say that someone who manages another account should "at least know how to do some simple things on the command line."  Fact of the matter is, there are people out there who will always be intimidated by the command prompt. We are talking about families and basic users here, not business IT admins.

I'm sold on linux and I will use it for everything I do, but as I try to convert non-techie type people to it, certain things need to be addressed appropriately.  This is one of them.  Telling them to buck up isn't the answer.

Suggesting that people who admin a system should have a minimum knowledge is because someone with root privilege can do wrong and irreversible actions.
Btw, all admin things can be done with the GUI prefixing the name of the app to launch with gksudo in the run dialog (Alt+F2) or with a launcher/shortcut (which is easy to create with the GUI on the panel or in the menu).

---

### Post by Doughy on 2008-04-14
> **sekinto said:**
> Okay, I really don't know how to make this any more understandable.

1) Right click desktop and click "create launcher".
2) Type in a name, anytihng will do, "Computer", "Filesystem", anything that makes sense to the user.
3) In the command field type "gksudo nautilus /home".
4) Select a different icon if they want to use one.
5) Now they will never have to worry about it again, they just have to click the icon on their desktop... doesn't seem cryptic to me. You could probably even make the launcher file for them and send it to them if they couldn't understand those simple instructions.

I know how to make a launcher file.

OK, so a new user that has no previous linux experience, and doesn't have any friends who can help them, wants to install ubuntu for their family.  All they know is that they are sick of the windows mess and they want to give linux a try.  They start playing with it, and start having trouble sharing their photos/files with each other.  How are they ever going to know how to type "gksudo nautilus /home" in a launcher file to do what they want to do?  People should be able to figure this kind of stuff out on their own, yet we're asking them to know a command "gksudo nautilus" even though they have never been on a linux machine in their life.

---

### Post by warp99 on 2008-04-14
> **Doughy said:**
> 
She is a mother of 3 kids, all of who she wants to set up with accounts on her computer.  Sometimes she wants to be able to share files with other users, or be able to access their files..

She can add the other user groups to her group settings, then change the permissions on the ~/.desktop folders of the other users to 'rwxrw', now she has access to their shares and files all of the time.

If she wants to share files with others she can setup a /share directory with the proper permissions and place the files there. You don't want others to access your share if you're the admin.

All of this can be done with the GUI admin tools and with 'gksudo nautilus'. There is no need to go to the command prompt.

---

### Post by aysiu on 2008-04-14
> **Doughy said:**
> 
OK, so a new user that has no previous linux experience, and doesn't have any friends who can help them, wants to install ubuntu for their family. I wouldn't advise a new user who has no Linux experience to install it herself unless she is particularly tech-savvy. After all, you don't expect users with no Windows experience to install Windows themselves (what a nightmare that would be!).

That said, I think the original question is a bit different from what your later examples point to, which is a genuine deficiency in Ubuntu. If you want, you can vote for this Brainstorm idea:
[idea #3916: Easy file sharing between local users](http://brainstorm.ubuntu.com/idea/3916/)

---

### Post by Doughy on 2008-04-14
> **aysiu said:**
> I wouldn't advise a new user who has no Linux experience to install it herself unless she is particularly tech-savvy. After all, you don't expect users with no Windows experience to install Windows themselves (what a nightmare that would be!).

OK, that's a technicality.  Let's say someone orders a computer with Ubuntu pre-installed from Dell then.

---

### Post by ayoli on 2008-04-14
> **Doughy said:**
> I know how to make a launcher file.

OK, so a new user that has no previous linux experience, and doesn't have any friends who can help them, wants to install ubuntu for their family.  All they know is that they are sick of the windows mess and they want to give linux a try.  They start playing with it, and start having trouble sharing their photos/files with each other.  How are they ever going to know how to type "gksudo nautilus /home" in a launcher file to do what they want to do?  People should be able to figure this kind of stuff out on their own, yet we're asking them to know a command "gksudo nautilus" even though they have never been on a linux machine in their life.

Debian installer had a nice option in the past (dunno if it still exists).
It was asking you something like : "do you want your system wide or not" where wide meant all users belong to same group and can manage other users file.
Though, people who start with linux need to read some doc or have someone that can explain the basics.

---

### Post by sekinto on 2008-04-14
Usually the person you described could come to these forums, where we could probably give them the answer in under five minutes. But maybe you could ask the nautilus devs if they could add a feature were if an admin clicks on someone else's home directory that it would ask them once if they want permissions to access this folder from now on. If they say yes they type in a password and they are good to go.

---

### Post by sekinto on 2008-04-14
> **Doughy said:**
> OK, that's a technicality.  Let's say someone orders a computer with Ubuntu pre-installed from Dell then.


Dell customer support? Ubuntu forums? Google?

---

### Post by warp99 on 2008-04-14
> **sekinto said:**
> Dell customer support? Ubuntu forums? Google?

Buy a book?

[http://www.amazon.com/Official-Ubuntu-Book-2nd/dp/0132354136/ref=pd_sim_b_img_4](http://www.amazon.com/Official-Ubuntu-Book-2nd/dp/0132354136/ref=pd_sim_b_img_4)

They still use them in schools for teaching, right?

---

### Post by Doughy on 2008-04-14
> **warp99 said:**
> Buy a book?

[http://www.amazon.com/Official-Ubuntu-Book-2nd/dp/0132354136/ref=pd_sim_b_img_4](http://www.amazon.com/Official-Ubuntu-Book-2nd/dp/0132354136/ref=pd_sim_b_img_4)

They still use them in schools for teaching, right?

I'm sorry but no one should have to buy a book to figure out how to share files or admin their kids files.

The whole point of this is that a user should be able to figure this out on their own.  It's a simple enough task to not need customer support, books, or even the forum.

---

### Post by aysiu on 2008-04-14
So vote for the Brainstorm idea I linked to earlier.

---

### Post by sekinto on 2008-04-14
How about included documentation, that is free and available locally.
And you say nobody should have to read anything, but look at the top ten bestsellers at my local computer store:

#1:  Microsoft Windows Vista Plain & Simple
#2:  Windows Vista For Dummies, Special DVD Bundle
#3: Mac OS X Leopard: The Missing Manual
#4:  Mac OS X 10.X Leopard Visual QuickStart Guide
#5:  Teach Yourself VISUALLY Mac OS X Leopard
>>>>>#6: Upgrading & Repairing PCs, 18th Edition
>>>#7:  Office 2007 For Dummies
#8:  Easy Mac OS X Leopard
#9:  Microsoft Windows Vista Step by Step
#10: Windows Vista For Dummies Quick Reference

Nine of them are guides to using operating systems or software for them, eight for operating systems specifically.

I agree that things should be easy, but sometimes you have to read. You wouldn't try fixing a car before reading/learning about it, would you? You wouldn't operate a car without taking lessons first, amiright?

---

