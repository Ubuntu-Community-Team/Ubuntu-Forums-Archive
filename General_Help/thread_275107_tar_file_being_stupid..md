---
title: "tar file being stupid."
date: 2006-10-10
forum: General Help
---

### Post by puccaso on 2006-10-10
i am trying to decompress a 2g tar file i have.
forsome reason, its being stupid
when i try to uncompress it
this is what i get on the command line output (via file-roller, if i do it in term, it just does nothing and waits for a ctrl+c)

```
mv: cannot stat `/home/mahir/Desktop/Photos.tar_FILES/Photos.tar_FILES/*': No such file or directory
```


what does this mean?

---

### Post by TigerWolf on 2006-10-10
It means the command you typed as incorrect. Could you paste the command you typed?

---

### Post by kiddo on 2006-10-10
It means that the path you wrote is wrong :) try using quotes (" ") around it, and/or using the "tab" key on the keyboard to automatically complete the path for you while you type it. By the way, you seem to have written "Photos.tar_FILES" twice at the end, I doubt you have two folders of the same name one into each other...

Edit: oh noes. I just realized that it's fileroller that told you that. Forget what I just said up here O_O weird.

---

### Post by puccaso on 2006-10-11
i didnt type a command,
i right clicked on the file - and clicked extract here..

as started before
if i run from command line with tar -xv nothing happens.

---

### Post by flyingbrass on 2006-10-11
On the command line I'm pretty sure the f is mandatory and needs to precede the filename:

tar -xvf whatever.tar

---

### Post by puccaso on 2006-10-11
ok, so i forgot about that. duh, sorry

but now i get nothing eithr.
i mean its a 2 gig file, so says all of us. nautilus/ls they all confirm
but there seems to be nothing in the file?! how is tha tpossible.

---

### Post by utab on 2006-10-11
Can you see what is in the archieve by

tar -t file.tar

If the file is a big file, this ,may take some time.

Regards

> **flyingbrass said:**
> On the command line I'm pretty sure the f is mandatory and needs to precede the filename:

tar -xvf whatever.tar

---

### Post by puccaso on 2006-10-11
well
yes, it takes a long time, seeing as the file is 2G, but there is NO DISK ACTIVITY.

its like a 2g paperweight, but how is this possible?!

tar -t just sits there,

---

### Post by MWAAAHAAA on 2006-10-11
I've been testing somewhat and a tar -t on my 4GB file has been running for over half an hour already and still just sits there. At this moment I'm inclined to say that you just need to have patience.
Do you know what is supposed to be in your file? Lots of small files, one big large file?

---

### Post by puccaso on 2006-10-11
lots of small files..
yes but, do unot think, that seeing as there is no activity from the tar pid (check top) then u are waiting for paint to dry.. i mean, it sno tthat we have t be pateint, we have to be radicial, if there was hd activity - then im all with u - but do u have any hd activity?

---

### Post by MWAAAHAAA on 2006-10-11
I implore you, PLEASE USE PROPER SPELLING, a wot ur ritin no riedible i s. Thank you.

No, nothing is happening when I perform a tar -t either. However unpacking works flawlessly, could you post *exactly* *letter for letter* what you are writing into the console? Seeing as your spelling on the forum sucks, you might just be making a typo on the command line. Try the following:

tar -xvf <filename>

And then also post everything it spits out at you.

---

### Post by puccaso on 2006-10-11
ok
i do that now
thank you please.

> login as: mahir
mahir@pu#####'s password:
Linux jt 2.6.17-10-386 #2 Tue Oct 10 19:41:48 UTC 2006 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have new mail.
Last login: Wed Oct 11 16:24:34 2006 from #####215.bethere.co.uk
cd Dmahir@jt:~$ cd Desktop/Photos.tar_FILES/
[EMAIL="mahir@jt:%7E/Desktop/Photos.tar"]mahir@jt:~/Desktop/Photos.tar[/EMAIL]_FILES$ ls
a.tar  find_tar_headers.pl  Photos.tar
[EMAIL="mahir@jt:%7E/Desktop/Photos.tar"]mahir@jt:~/Desktop/Photos.tar[/EMAIL]_FILES$ tar -xvf Photos.tar
[EMAIL="mahir@jt:%7E/Desktop/Photos.tar"]mahir@jt:~/Desktop/Photos.tar[/EMAIL]_FILES$



thats exactly, WORD for (the) WORD it writes.

---

### Post by flyingbrass on 2006-10-11
Are you sure it's actually a tar file?  Try:

file Photos.tar


The result should be:

Photos.tar: POSIX tar archive

---

### Post by puccaso on 2006-10-11
ok
we're getting somewhere.
it says to me 

Photos.tar: data


whats going on?!
i have all my photos saved here!! :(
it WAS a tar file, what the hell happened?

---

### Post by flyingbrass on 2006-10-11
Not good.  "Data" means it doesn't recognize the file type.  Perhaps someone else can offer some suggestions.

---

### Post by puccaso on 2006-10-11
thanks for your help!

can someone else help me! please!!!

---

### Post by towsonu2003 on 2006-10-11
try copying it to your desktop and untarring it there -maybe it's having weird difficulties with the folder name-
```

cd
cd Desktop
cp Photos.tar_FILES/Photos.tar ./ 
tar xvvf Photos.tar

```

copying will take some time. 

do you have a copy of this tar file somewhere else -may have been corrupted during a transfer-? if so, compare the md5sum of the two 
md5sum file1
md5sum file2

output should be same for both.

---

### Post by towsonu2003 on 2006-10-11
> **utab said:**
> 
tar -t file.tar

apart from my previous post above, I believe this should have been
```

tar -tvf Photos.tar

```
f specifies the file name, v makes it verbose.

---

