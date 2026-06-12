---
title: "HELP PLEASE.... - I can not login on my Ubuntu 15.04"
date: 2015-06-14
forum: General Help
---

### Post by Mads_Unneberg on 2015-06-14
My Adm.Password is refused on the login of my Ubuntu 15.04 because I were drunk and I did something that I should not have done.
I am not totally fresh but I am still struggling with terminals and commands. AND I have a way about me that refuses not being in control.
I know this means problem dealing with a computer and its software but I am SO tying to cope with it all.
ANYWAY, I finally got a system going for me with Ubuntu 15.04 after working with Linux for a year now and just minutes after I gratulated my self for astonishment......
This has all doing with the keyboard and its im-config. 
As I said I was drunk but I still have a vision of me changing something in one of the text documents to the keyboards default setting and this I did through the INPUT METHOD CONFIGURATION program and its USER CONFIGURATION. I have also tried switching to the previous source with its shortcut and I have tried to change my password through the GRUBs rescue *Not rescue BUT ????* mode.
The answer I got from the ?rescue?  mode -       passwd- Authentication token manipulation ERROR     and       passwd- password unchanged.
I think I have read enough now to deal with the problem but I CANT GET IN.
SO HOW TO CHANGE MY ADMINISTRATE PASSWORD ????????
Regards
Mads Unneberg.

---

### Post by steeldriver on 2015-06-14
Hello and welcome to the forums

The "authentication token manipulation error" usually results when you miss the step of remounting the filesystem with read-write permission

Follow [these instructions]("http://www.psychocats.net/ubuntu/resetpassword") CAREFULLY, especially where it says

> 
 In recent versions of Ubuntu, the filesystem is mounted as read-only, so  you need to enter the follow command to get it to remount as  read-write, which will allow you to make changes: 


HOWEVER if you have messed with im-config, resetting your password may not be the solution.

---

### Post by Mads_Unneberg on 2015-06-14
First THANK`s to  STEELDRIVER. 
And you were absolutely right! The password issue did not fix any thing.  
I worked with the problem until 9 o`clock last night. - THEN HAD ENOUGH.... Formatted the disk and are back her with a brand new upset.
- So I`am ending this thread.
Regards
M.

---

