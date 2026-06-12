---
title: "How to install sdcc on ubuntu"
date: 2017-05-29
forum: General Help
---

### Post by abhi143 on 2017-05-29
Hello everyone 
I am looking help on software installation. I have installed ubuntu operating system. I am totally beginner. actually I am from electronics side and I want to install sdcc compiler on ubuntu 
I have downloaded sdcc file. it is download with extension  .tarbz2.  than I opened tarminal and create folder compiler.  after that I  double clicked on that file  name  and save in compiler folder. now my file is extract successfully. I have attached some screen shot please see the attachment   and please help me to install sdcc software 

thanks

---

### Post by oldos2er on 2017-05-29
Why not install it from the repositories? ```
sudo apt update; sudo apt install sdcc
```

---

### Post by yancek on 2017-05-29
Usually when you have a "tar" package and download it and extract it, you will have a README or install file with instructions.  Have you checked that?  I think it would be much easier to install from repositories as suggested.

---

### Post by abhi143 on 2017-05-29
> **oldos2er said:**
> Why not install it from the repositories? ```
sudo apt update; sudo apt install sdcc
```

I did googe search for repositories and I found this link [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) I have seen some link for repositories. I have doubt, I am not clear how to install repositories by using tarminal or ubuntu software store . so I think first I have to download repositories from ubuntu software store and than I have to configure using command. am I correct ? 

while reading  I found synaptic so  I have installed "Synaptic package manager" . will it help to install sdcc

---

### Post by deadflowr on 2017-05-29
> I did googe search for repositories and I found this link [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) I have seen some link for repositories. I have doubt, I am not clear how to install repositories by using tarminal or ubuntu software store . so I think first I have to download repositories from ubuntu software store and than I have to configure using command. am I correct ? 

The repository is already included and ready to roll.
follow the commands oldos2er gave.

> while reading I found synaptic so I have installed "Synaptic package manager" . will it help to install sdcc

yep, that works as well.

---

### Post by cariboo on 2017-05-29
oldos2er gave you the instructions that you need. The first part of the command updates the repositories:

```
sudo apt update
```

and the second part of the command:

```
sudo apt install sdcc
```

installs the sdcc package.

---

### Post by abhi143 on 2017-05-29
I have used that command. I get message "unable to lock administration directory" I have attached picture please look at this image there is response that I am getting. and tell me what I have to do next.

---

### Post by deadflowr on 2017-05-29
It's two separate commands and so both require sudo each time.
You ran the update command with sudo, but not the install command.
Run them both with sudo.

---

### Post by abhi143 on 2017-05-29
please look at attachment. and tell me how to sure that sdcc has been installed successfully

---

### Post by deadflowr on 2017-05-29
The attached image shows it's already installed.
If it failed it would have shown you errors and a reason why it failed.

So success!

---

### Post by abhi143 on 2017-05-29
Thank to all of you for helping me. now when I typed sdcc and enter it show message that is in attached image. what is meaning of that message

---

### Post by deadflowr on 2017-05-29
The image shows the help page that lists what various commands you need to use to get the program to work.
You'll need to learn how to use the program now.
Hopefully you can glean something more useful than what I can tell you from here:
[http://sdcc.sourceforge.net/]("http://sdcc.sourceforge.net/")

---

