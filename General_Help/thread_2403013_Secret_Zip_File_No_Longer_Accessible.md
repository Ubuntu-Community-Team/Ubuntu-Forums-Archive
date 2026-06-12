---
title: "Secret Zip File No Longer Accessible"
date: 2018-10-06
forum: General Help
---

### Post by captaingraviton on 2018-10-06
Howdy Friends,

My laptop was running Ubuntu 16.04. It had a hidden folder on the desktop labeled *".SFolder"*, inside it was a passwrod protected zip file called *"**workstuff** -- batch01.zip"*. Yesterday I did an update via the Software Updater which ran smoothly then suggested I upgrade the distribution to Ubuntu 18.04. "Yes please" thought I, and, after a bit of trouble I won't go into, the upgrade was complete and I am now using Bionic Badger (which I like a lot!). HOWEVER, that zip file will not extract. I open Nautilus, double-click the file, the Archive Manager/File Roller opens and shows the contents of the zip file, I hit *"Extract"* and input the password, but I get the message "*An error occurred while extracting files"*.

So, thinking I'm clever (I'm not) I open Nautillus as administrator and try extracting the file in the same way again. This time, just double-clicking the file sends an error which reads *"Could not open "**workstuff** -- batch01.zip" The specified location is not mounted".* Well that's weird isn't it? 
I have since changed *".SFolder"* to just *"SFolder"* but the problem is still the same. What should I do next?

---

### Post by TheFu on 2018-10-06
3 ideas come to mind.
a) did you change the language or keyboard layout?
b) can you restore from a backup made before the 18.04 choice was made?  Always make a full, know-you-can-restore backup before any major system update/upgrade.
c) Can you open & unlock the zip from the shell?

---

### Post by captaingraviton on 2018-10-06
Hi TheFu,

a) did you change the language or keyboard layout?
No, I haven't done that.

b) can you restore from a backup made before the 18.04 choice was made? 
Well the good news is that I DO have a backup of the file, so it's not that serious a problem, I just wonder if it's a sign of something else that might need sorting in the future?

c) Can you open & unlock the zip from the shell?
I'll google how to do that as I don't really know how. 
(Also, how do I do that?)

---

### Post by Holger_Gehrke on 2018-10-06
> **captaingraviton said:**
> 
c) Can you open & unlock the zip from the shell?
I'll google how to do that as I don't really know how. 
(Also, how do I do that?)

Open a terminal (ctrl-alt-t or however else you want to do it ...) then change to the directory and extract the file:
```

cd ~/Desktop/SFolder
unzip -x 'workstuff -- batch01.zip'

```You could also use "unzip -xP password 'workstuff -- batch01.zip"' to give the password to unzip on the command line where you can see it, BUT that would put the password into your shell history. To avoid that you could put a space in front *of the command.*

Holger

---

### Post by captaingraviton on 2018-10-06
Here's a quick explanaitionof what I just did:

I googled how to unzip in shell (Oh? How easy)

```
unzip '*workstuff** -- batch01.zip'*
```

*EDIT: I also tried your suggestion Holger with the -x, but the output was the same.*

Which didn't work, but it spat out an error for each text file inside the archive:

```
Skipping: *workstuff** -- batch01.zip need PK compat. v5.1 (can do v4.6)*
```

So that's odd seeing as I made the archive in Ubuntu 16.04? No worries, I'll just google about how to solve that problem. I found the information at [this link]("https://ubuntuforums.org/showthread.php?t=1416364") helpful.

So then I do this:

```
Stu@Laptop:~/Desktop/SFolder$ 7z e ''*workstuff** -- batch01.zip'*
```

..and after I input the password it worked!
Hopefully this problem is just a one-off. Thanks for your help, you put me on the right track!

---

### Post by TheFu on 2018-10-06
BTW, having two dashes in a filename means you have to use special name parsing.  If someone didnt get their code perfect, a mistake will be made.  This is a shell file expansion deal which makes the shell very powerful in the right hands.

Tip:  Dont use spaces or funny punctuation in directory or file names.  1 dash, fine.  2 dashes together, not a good choice.

You may have been able to do an** unzip w*zip** and that might have worked.

The double-dashes are often interpreted to mean something special.  From the bash manpage:```

       --        A -- signals the end of options and disables  further  option
                 processing.   Any arguments after the -- are treated as file&#8208;
                 names and arguments.  An argument of - is equivalent to --.
```

---

### Post by captaingraviton on 2018-10-06
I think you might well be right there TheFu. From now on I'll be naming my archives more carefully.

Thank you!

---

### Post by TheFu on 2018-10-06
In theory, it shouldnt matter.  In theory.

---

