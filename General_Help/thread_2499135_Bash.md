---
title: "Bash"
date: 2024-07-14
forum: General Help
---

### Post by snudgeo on 2024-07-14
I am new to linux, but am persevering as best I can. I am up and running with Ubuntu 22.04 and all of the basic programmes I need and have installed various software with hardly any problems. However, I am now trying to install TOR, which I downloaded from the official Tor project site. I am using terminal, by following instructions on a website which seems to know its stuff.
Unfortunately, when I have typed the necessary command, I get the word 'bash' appearing as the first word on the next line and my installation does not proceed. I have no idea what bash is and I have never experienced this before.

Would someone kindly explain what I should do to effect my install.

Thanks

---

### Post by vanadium on 2024-07-14
What is the "necessary command"? If you expect help, be helpful to those who may want to help and at least point to the precise procedure you try to follow, and precisely indicate after which "necessary  command" you get the output "bash". At least then, we may be able to see what is wrong, or explain what happens.

---

### Post by ajgreeny on 2024-07-14
And what was that "website that seems to know its stuff"?

Tell us exactly what commands you have used so far or we are just guessing!

---

### Post by The Cog on 2024-07-14
FYI, bash is a command interpreter, roughly equivalent to Windows cmd or powershell.
It would be good if you can copy/paste both the command you are typing and the response into a post here. 
Use the advanced edit mode and use the # button at the top to put code tags round the copied text to retain indentation, spaces etc.

---

### Post by morovan on 2024-07-14
What are you trying to install? Becuase Tor is a project, not a software.
What problem are you trying to solve by installing it?

---

### Post by currentshaft on 2024-07-14
> **snudgeo said:**
> I am new to linux, but am persevering as best I can. I am up and running with Ubuntu 22.04 and all of the basic programmes I need and have installed various software with hardly any problems. However, I am now trying to install TOR, which I downloaded from the official Tor project site. I am using terminal, by following instructions on a website which seems to know its stuff.
Unfortunately, when I have typed the necessary command, I get the word 'bash' appearing as the first word on the next line and my installation does not proceed. I have no idea what bash is and I have never experienced this before.

Would someone kindly explain what I should do to effect my install.

Thanks

Copy and paste what you see here. How else would anyone possibly know what you're talking about?

---

### Post by snudgeo on 2024-07-20
I am following instructions in this video: [https://www.youtube.com/watch?v=wxOk7gYt_dY](https://www.youtube.com/watch?v=wxOk7gYt_dY)
The download is OK and presently in my downloads folder. However, when I try to execute the command cd downloads/  this appears  bash: cd: downloads/: No such file or directory
I can't get any further than that. The instructions in the vid are simple and clear enough, even for me, but what to do now?

---

### Post by deadflowr on 2024-07-20
Should be Downloads with a capital D.

---

### Post by dragonfly41 on 2024-07-20
In terminal (say Qterminal or any other bash terminal) type

```
~/Downloads
```

or (same thing, your home)

```
/HOME/Downloads
```

---

### Post by yancek on 2024-07-20
>   presently in my downloads folder. However, when I try to execute the command cd downloads

I haven't looked at the video yet but I would tend not to trust something like a youtube video for something like installing TOR.  Did you not go to the TOR site and follow the simple instructions there.  The instructions appear to be using some version of Ubuntu.

[https://tb-manual.torproject.org/installation/](https://tb-manual.torproject.org/installation/)

 If you are already 'in' your Downloads folder why would you need to cd  (change directory) to downloads?  As pointed out, in these circumstances  case sensitivity applies so if yo type in downloads and the correct  directory name is Downloads you would expect to get the error you got.

If you have no idea what bash is you need to do a lot of reading/research.

Edit:  I just watched most of the video and it does correctly show Downloads and not downloads so you need to understand some basics or you will continue to create problems for yourself.  You might download the pdf from the Ubuntu site below or bookmark the line as it is the Ubuntu Desktop User Guide and should be very useful for someone new.

 [https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by snudgeo on 2024-07-21
Thank you to all who contributed here. It was the D in downloads and I kick myself several times for making such a stupid mistake. My installation was straight forward. Thanks again.

---

### Post by currentshaft on 2024-07-21
The flatpak is much easier to use and maintain if you struggle with command line: [https://flathub.org/apps/org.torproject.torbrowser-launcher](https://flathub.org/apps/org.torproject.torbrowser-launcher)

---

