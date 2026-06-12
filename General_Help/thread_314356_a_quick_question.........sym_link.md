---
title: "a quick question.........sym link???"
date: 2006-12-07
forum: General Help
---

### Post by slyjelly on 2006-12-07
hi, 

could some one just explain this command to me:

quote: then had to sym link /usr/lib/libslang.so to /home/smack/DropTeam/lib/libslang-utf8.so.1.

what does sym link mean? is this some kind of shortcut? is it for terminal?

its to run this new drop team demo, below are some links if my explanation needs  more specifics. basically it would be good for a guide in lamens terms of the above quote. its the last step i need for playing this demo....

[http://ubuntuforums.org/showthread.php?t=206889](http://ubuntuforums.org/showthread.php?t=206889)             (thread 2 + 3)
[http://tjwhaynes.googlepages.com/dropteamreview-part5](http://tjwhaynes.googlepages.com/dropteamreview-part5)

thanks for any replies/interest

p.s anyone interested in feedback for new games can contact me if u wish

---

### Post by esaym on 2006-12-07
[http://en.wikipedia.org/wiki/Symbolic_link](http://en.wikipedia.org/wiki/Symbolic_link)

its a shortcut so to speak

Also not to hijack the thread but since we are on the same subject..

When I first installed ubuntu I created a 500mb partition for the /var directory.  At the time I did not know that all the apt-get downloads are stored in /var/cache/apt/archives.  As you can imagine I quickly ran out of space on the /var partition.  So what I did is moved the archives directory to my big /home partition and made a sym link back to /var/cache/apt/archives

Is there anything bad about doing that?

---

### Post by Sarisar on 2006-12-07
Sym links are just a way of stopping having the same file copied over and over again.

In windows, for example, there are _major_ issues with having multiple DLLs around.  Linux tries to get around this by having one file in one place, but where you would have the other copies, you make a sym link.

I believe that linux handles this just like having a file in that directory so no, doing a sym link with var shouldn't matter.

Look at the /media/cdrom where they have symlinks to /media/cdrom0 on mine anyway) to save you having to go to /media/cdrom every single time.

---

### Post by feathers on 2006-12-07
Or, if you want to get rid of all the old .deb files, you can type "sudo apt-get clean" and they are deleted.

---

### Post by esaym on 2006-12-07
Yea I do apt-get clean.  I still like knowing that I won't ever run out of space though.

The sym link "fix" seems to work fine /var usage went from 450mb to about 98mb.  But in the console "df" still shows 450mb used out of 500mb.  Strange.  I guess it sees the size of the directory in the /home partition for too?

---

### Post by slyjelly on 2006-12-07
hi, thanks for the info, very useful, i fully understand now

my problem still stands though (now with greater depth)

basically im trying to create a link to a file called libslang-utf8.so.1
however i can only find this file as a link itself

i'll try to explain but it is difficult, 

it seems as though the file i need to link to, is actually linked to an archive called (libslang.so.1-UTF8.4.9) rather than the correct file i need (libslang-utf8.so.1) 

sorry if it makes no sense but plz help, im at the end of a long stint of failed methods, any questions about my system or methods i will answer if it helps you figure it out, because i have'nt got a clue. by the way, the links on the first thread in this page may help this problem, these guys seemed to get it working, but that was in july (i doubt they could remember how 5 months down the line)

---

