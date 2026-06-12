---
title: "Im having problems with Scilab, its in arabic, I think."
date: 2006-07-13
forum: General Help
---

### Post by slimdog360 on 2006-07-13
First I tried compiling Scilab by source but I had an error
```
configure: error: X Window not found
```
I didnt know how to fix that so I ended up finding it in synaptic in the multiverse repositories.
So I installed it with synaptic and all seemed to go well.
 After it installed I checked the applications menu but it wasnt there so I typed 'scilab' into a terminal and first I get this message coming up
```
nick@nick-desktop:~$ scilab
/usr/bin/scilab: line 31: /usr/lib/pvm3//lib/pvmgetarch: No such file or directory

```
then this window comes up
[IMG]http://img138.imageshack.us/img138/141/screenshot3to.png[/IMG]
I dont know if thats what its supposed to look like but I cant read Arabic, Im pretty sure its Arabic but like I said I cant read it so I dont know.
Can someone help me. If at least I can change the language that would be great. 
But also I thought that there was supposed to be a bit more of an interface. Maybe I was wrong??
Thanks

edit: Make that I think its in Hindi rather than Arabic (thanks Matthew) but I cant read Hindi either so its still the same question.

---

### Post by matthew on 2006-07-13
I'm afraid I have no idea what the problem is as I have no experience with scilab. However, I can read Arabic and can tell you that is not Arabic. I think it's Hindi, but I could be mistaken.

---

### Post by tjansson on 2006-07-27
I have the exact same problem on my Thinkpad X30 with kubuntu 6.06 and the 686 kernel. It very strange and hard to debug hindi! :-(

---

### Post by megadodo on 2006-07-27
If you download and install the latest version from the scilab website (version 4.0) it works fine and you can read the writing! I think its a bug with the package. If you stick "scilab" into the forum search doodah then there are some threads discussing it in more detail, but the conclusion of most of them is just to install the latest version from the website
Hope this helps
Richard

---

### Post by tjansson on 2006-07-27
Maybe I should do that, but it is just such a shame that is broken. I did search the site, which resulted in me trying to install mstcorefonts and uninstalling the tamil fonts, which somebody said worked. Installing the mstcorefonts didn't help and not to happy about removing the tamil font, since aptitude tells me that it depends on ubuntu-desktop package.

---

### Post by megadodo on 2006-07-28
Yes, it is a shame. From what i can gather this bug has been around a long time and hasn't been fixed. Although from the bug report on launchpad, it appears to be a debian thing rather than an ubuntu thing. But still, its a major piece of software for many people, and its an old version that doesnt even work. But i expect it will get fixed in time if enough people mention it!
As for the ubuntu-desktop package, its just a 'meta' package that has all the required ubuntu desktop packages as dependencies of it, so you can quite happily remove it. 
There is a binary version on the scilab website so you dont have to compile anything. Just unpack it and read the readme or install file, or whatever its called and it tells you how to run it.
Have fun,
Richard

---

### Post by tjansson on 2006-08-08
For the interested here is another screenshot of the problem:
[IMG]http://www.tjansson.dk/phpAlbum/billeder/screenshots/strange-scilab.png[/IMG]

Now I did install scilab 4.0 from their site, since the script I was running had some problems - and debugging hindu output is just not my cup of tea :D

Does anybody know if there are any one at Ubuntu working on the problem?

---

