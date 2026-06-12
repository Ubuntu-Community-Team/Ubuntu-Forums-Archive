---
title: "Can't apt-get update"
date: 2014-12-04
forum: General Help
---

### Post by aaron-lowry on 2014-12-04
I get an error when I run the sudo apt-get update command.

E: Type 'c&#65533;&#65533;4&#65533;CN,&#65533;~&#65533;=j&#65533;&#65533;&#1706;&#65533;&#65533;&#65533;&#65533;&#65533;&z&#65533;&#65533;&#65533;&#65533;5&#65533;&#65533;&#275;&#65533;hx@' is not known on line 1 in source list /etc/apt/sources.list.d/google-chrome.list
E: The list of sources could not be read.

any idea how I can fix this?

---

### Post by Yougo on 2014-12-04
there appears to be some odd text in that source file, which apt can't work with. did you by chance alter that file recently?

can you attach the file to a post (advanced reply, paperclip button), or post the first 5 lines of text from that file here?

open the file as root:
```

sudo gedit /etc/apt/sources.list.d/google-chrome.list

```

copy the lines, paste them in a post, and close the file without saving.

---

### Post by Impavidus on 2014-12-04
+1 to the first part. Your sources.list is corrupt. Did you change it in a word processor? They tend to use complex binary formats instead of plain text, which could cause such a problem.

As to the second part, if you're just posting the contents of the file and not editing it yet, there's no need to open it as root. Just```
gedit /etc/apt/sources.list.d/google-chrome.list
``` will work and open the file read-only. We advise against using **sudo gedit** anyway, as this sometimes has nasty side effects, like making it impossible to log in using the GUI. If you're going to edit any of these system config files, it's easiest to use either **gksu** or its successor **pkexec** instead of sudo when using gedit, or use one of the teminal based text editors. Also make a backup of the original before editing these files.

But I don't think there is much hope fixing this file. You may be able to delete it. Reinstalling chrome from the .deb you got from google should create a fresh google-chrome.list file.

---

### Post by aaron-lowry on 2014-12-04
Couldn't upload the file becuase it says that it is an invalid file.

Here are the first few lines of the file.

&#997;"\99\C4v\A2\AA\EF<\A8Y\F54ø8\F5D\FA\94R\E9\C2&#612;\E0*\E8\8Fo\A9\FB\FF\853j\9A\BE\CDgK2\83\F0n\88\D4\FEe$P%-@!
    E\BA\85&#904;m5G\CB}\BE\9A\EDk\\F9\B2\F9\CDh\86\EF}\94\FE=[bA\ACk\C5?KP\D4\E2\8E\E8r\A1Q&#1993;=\00\BF\AC;2f(&#970;\9F'\F0\E0Cd\97,wp\FE\A8\9ER\BB>\C40Ie\91\B0u\EB\B7j\EB&#312;T&#603;\BA#\8E\E8\CDMX\C6?&#1387;\EAXre6\EC\F3\EF7&#1962;\873\C6¬\B4\AC\95\87\F9U};\9Dw\E1=\E3~\92\91\BD\9C q\EE\D4\F2\CB\F6J\CB4*\BB\DD1ts&#1407;\93o\D1&#1758;L\B27G

*Edit*
By the way no I didn't open it or edit the file with a text editor. However when I opened the folder to where the file it I noticed that it is a binary file instead of a text document like the others are.

---

### Post by Yougo on 2014-12-04
> **Impavidus said:**
> 
As to the second part, if you're just posting the contents of the file and not editing it yet, there's no need to open it as root. 

fair enough. t'was a force of habit to read /etc/... and go for root acces.

> has nasty side effects, like making it impossible to log in using the GUI.(...) **gksu** or its successor **pkexec** instead of sudo. 
again, fair enough. didn't know about pkexec though. is gksu going away?

> 
But I don't think there is much hope fixing this file. You may be able to delete it. Reinstalling chrome from the .deb you got from google should create a fresh google-chrome.list file.
+1

> **aaron-lowry said:**
> Couldn't upload the file becuase it says that it is an invalid file.

Here are the first few lines of the file.

&#997;"\99\C4v\A2\AA\EF<\A8Y\F54ø8\F5D\FA\94R\E9\C2&#612;\E0*\E8\8Fo\A9\FB\FF\853j\9A\BE\CDgK2\83\F0n\88\D4\FEe$P%-@!
    E\BA\85&#904;m5G\CB}\BE\9A\EDk\\F9\B2\F9\CDh\86\EF}\94\FE=[bA\ACk\C5?KP\D4\E2\8E\E8r\A1Q&#1993;=\00\BF\AC;2f(&#970;\9F'\F0\E0Cd\97,wp\FE\A8\9ER\BB>\C40Ie\91\B0u\EB\B7j\EB&#312;T&#603;\BA#\8E\E8\CDMX\C6?&#1387;\EAXre6\EC\F3\EF7&#1962;\873\C6¬\B4\AC\95\87\F9U};\9Dw\E1=\E3~\92\91\BD\9C q\EE\D4\F2\CB\F6J\CB4*\BB\DD1ts&#1407;\93o\D1&#1758;L\B27G

*Edit*
By the way no I didn't open it or edit the file with a text editor. However when I opened the folder to where the file it I noticed that it is a binary file instead of a text document like the others are.

apparently. like Impavidus said, it's no use trying to edit a binary file by hand, you'll just break it. by looking at the text i hoped to see something human readable, and spot the problem like a missing # or a typo.
remove the file (or at least move it away from /etc/apt/sources.list.d/) (you do need root for that action) and reinstall Chrome from google's  .deb file

---

### Post by aaron-lowry on 2014-12-04
> **Yougo said:**
> remove the file (or at least move it away from /etc/apt/sources.list.d/) (you do need root for that action) and reinstall Chrome from google's  .deb file

I've tried removing the file using the shred command but it doesn't remove the file. Unless there is another way to do it. And I can't reinstall chrome either... When it tries to read the lists it gives the error message that I posted originally.

F.Y.I. I am new to the Linux OS

---

### Post by Yougo on 2014-12-04
Please don't use ```
shred
``` unless you really want to securely destroy a file, say if you're a russian spy :P. for normal delete it's quite the overkill. it scrambles the data on the hard drive three times over to make sure it's completely unrecoverable.

for normal delete operation use ```
 rm 
```
read more about it [here]("http://www.cyberciti.biz/faq/howto-linux-unix-delete-remove-file/")

in this case you need to use it as root
```
sudo rm -f /etc/apt/sources.list.d/google-chrome.list
```

---

### Post by aaron-lowry on 2014-12-05
Cheers for the help guys. 

+1 for the above post it helped remove the file and now I can update again. I have chosen not to install chrome to watch netflix now... Too much mucking around and it doesn't seem to want to work anyway

---

