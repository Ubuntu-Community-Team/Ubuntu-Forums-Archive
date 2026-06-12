---
title: "Executable text files"
date: 2007-04-12
forum: General Help
---

### Post by ax4413 on 2007-04-12
I have made a executable text file to solve a problem I have had, however every time i click on the file i am asked whether i want to: run in terminal; display; cancel or run. All i want to do is run it. is there any way to circumnavigate this request dialog? Have i chosen the right file type i.e a executable text file or should i have made a script file or some thing else? If so how would i go about such a thing? I am relatively new to Linux so please be gentle..

haha

steve

---

### Post by mac.ryan on 2007-04-12
What do you mean by "executable text file"? Do you mean a file containing a number of commands to be executed in series, as if they were typed from a shell?

if yes, then you can create a launcher (right click anywhere in the window) and filling the command field with:

```
bash <NameOfYourFile>
```

This worked for me.

---

### Post by ax4413 on 2007-04-12
Nice one man. I created a launcher and pointed it at the text file that i had previously created and everything works like a dream. The text file still needs to have "Allow executing file as a program" ticked in the permissions tab. That is what i meant by an executable text file.

Regardless thanks a lot mac.ryan

cheers

---

