---
title: "Is my ISO image good ?????"
date: 2015-12-24
forum: General Help
---

### Post by bobby23 on 2015-12-24
Okay...so,I'm trying to "verify" that the ISO image that I've downloaded is okay.I'm using instructions on how to do  this that i got  from the Ubuntu site.But,when I try to type in the commands in the windows terminal such as ( cd download_directory) I'm getting an error stating "the system cannot find the path specified"...I am NOT REAL familiar with working with "command terminals".I used Xubuntu for about 3 years.But,i was never all that familiar with the command terminal.
     When I type in the commansds that I get form the Ubuntu site (such as... into a windows terminal I get "the system cannot find the path specified".....WHAT am I doing wrong ??? I am SERIOUSLY  tired of using windows systems !!! PARTICULARLY when I KNOW that LINUX systems are so much better ! PLEASE HELP !!! WHY is Win 7 not accepting the terminal commands that I have been told to enter to check the integrity of the ISO that I have downloaded ???? I think I'm going to cry !

---

### Post by howefield on 2015-12-24
In the absence of anything meaningful in your post apart from the fact that you are about to cry, try this link.

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows)

---

### Post by sammiev on 2015-12-24
Hi bobbie23,

Usually I would use these commands.

in terminal type:

```
cd Downloads

dir
```

( that will give you the ISO file name which you can copy the name from: ie md5sum xenial-desktop-amd64.is )

```
md5sum xenial-desktop-amd64.iso
```

Remember that "xenial-desktop-amd64.iso" is just an example, so replace it with the iso file name you downloaded.

---

### Post by oldos2er on 2015-12-24
It sounds as if you're typing Linux terminal commands into a Windows command prompt. Try this instead: [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows)

---

### Post by coldraven on 2015-12-25
> **oldos2er said:**
> It sounds as if you're typing Linux terminal commands into a Windows command prompt. Try this instead: [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows)

+1

---

### Post by tea for one on 2015-12-25
> **bobby23 said:**
>  WHY is Win 7 not accepting the terminal commands that I have been told to enter to check the integrity of the ISO that I have downloaded ???? I think I'm going to cry !

There is a Windows utility which uses a GUI if you are having a problem with terminal commands:-

[http://www.nullriver.com/products/winmd5sum](http://www.nullriver.com/products/winmd5sum)

Hopefully, it will help.

Whoops, I've just opened the links in earlier posts and duplicated the info..............

---

### Post by bobby23 on 2015-12-29
Wow...howefield (And,everyone else who replied)! I'm so sorry ! I totally forgot about this post ! I should have received an email about it.Guess I'm gonna have to check those email settings.

Yes.That is what it sounds like to me,too.Thanks for the advice,my friend.Replied wrong...this comment was for [**[COLOR=#C61919][B]oldos2er**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=338320")

---

### Post by grahammechanical on 2015-12-29
As an aside. I have done many installs of Ubuntu & its flavours. I sometimes do test installs of the development version. I have never checked the md5sum of any ISO image that I have downloaded. I have never needed to.

My method is to download the ISO image. Burn it to DVD or USB memory stick. And if it works. It works. If it does not work, then is the time to start thinking about why it doesn't work.

Regards.

---

### Post by bobby23 on 2015-12-29
> **oldos2er said:**
> It sounds as if you're typing Linux terminal commands into a Windows command prompt. Try this instead: [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows)

Thank you,my friends for your help.This has done the trick.Now...how do you mark this thread as "solved" or if I remember correctly,we don't have to do that in the Ubuntu forums ?

---

### Post by Vladlenin5000 on 2015-12-29
Use the thread tools in the first post.

---

### Post by bobby23 on 2015-12-29
> **Vladlenin5000 said:**
> Use the thread tools in the first post.

Thank you,Vlad.

---

