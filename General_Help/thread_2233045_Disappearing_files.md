---
title: "Disappearing files"
date: 2014-07-05
forum: General Help
---

### Post by lemonoid on 2014-07-05
Hey all, I'm running a live session to try to fix my brother's computer, I am not at all new to Ubuntu, but this rar file with the program I need to use is giving me trouble. I had to update the Software server to universe to even get unrar-free to install. so then I have this .rar file in ./Downloads and in the terminal, the program keeps saying that it extracted, and all is ok, but the contents of the rar file are not showing up, its just still the rar file. I had to rename it because it had a -S at the beginning of file name, and unrar kept thinking i was passing -S as an option, so right now it is Spnrte6.rar and I've tried 
unrar x ./Spnrte6.rar -p
(which didn't even ask me for the password)
unrar e ./Downloads/Spnrte6.rar ./Documents (from the home dir)

...has anyone ever had this problem with unrar? or possibly know what's going on here.....thanks in advance

---

### Post by capscrew on 2014-07-06
> **lemonoid said:**
> Hey all, I'm running a live session to try to fix my brother's computer, I am not at all new to Ubuntu, but this rar file with the program I need to use is giving me trouble. I had to update the Software server to universe to even get unrar-free to install. so then I have this .rar file in ./Downloads and in the terminal, the program keeps saying that it extracted, and all is ok, but the contents of the rar file are not showing up, its just still the rar file. I had to rename it because it had a -S at the beginning of file name, and unrar kept thinking i was passing -S as an option, so right now it is Spnrte6.rar and I've tried 
unrar x ./Spnrte6.rar -p
(which didn't even ask me for the password)
unrar e ./Downloads/Spnrte6.rar ./Documents (from the home dir)

...has anyone ever had this problem with unrar? or possibly know what's going on here.....thanks in advance

I don't think you are using unrar correctly.  If I was going to use unrar on an archive in the current working directory I would use this```
unrar e Spnrte6.rar 
```...I'm not sure why you used the command as you have.

The second command also.  Why are you adding a . (dot) at the front of the path to the archive?  When stating a path it is either absolute (starting with /) or relative to where you are.  From the home directory,  The directory Downloads would be: Downloads so the path to the file would be: Downloads/Spnrte6.rar.  No . (dot) at the beginning.  

The path to a file and the that path that the OS uses to find an executable are similar but not used in the same manner.  The . (dot) user with a executable says: look for an executable starting in the current working directory.  This is because the default executable path does not include the current working directory.

---

### Post by claracc on 2014-07-06
I think the syntax is not correct, in case first command, you have written:

```
unrar x ./Spnrte6.rar -p
```

I assume you are in directory where Spnrte6.rar file is, I would write:

```
unrar x -p password Spntrte6.rar
```, see :[http://superuser.com/questions/413678/unrar-password-protected-file-on-ubuntu](http://superuser.com/questions/413678/unrar-password-protected-file-on-ubuntu)

In case second command, you have written:
```
unrar e ./Downloads/Spnrte6.rar ./Documents
```

But I would write the entire path, i.e:

```
unrar e /home/your_user_name/Downloads/Spnrte6.rar  /home/your_user_name/Documents/
```, see: [https://wiki.archlinux.org/index.php/RAR#General_syntax_2](https://wiki.archlinux.org/index.php/RAR#General_syntax_2)

---

