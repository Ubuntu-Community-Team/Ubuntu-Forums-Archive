---
title: "mkdir redirction"
date: 2007-11-11
forum: General Help
---

### Post by LinuxGEEK7288 on 2007-11-11
Hi all,
Heres my problem, what i want to do is to take a text document that has line after line of titles for example, call this A.txt
and in A.txt is the following text


One title
Another title
One more title

I then want to be able to pass this text document to mkdir and have it make directories with the names of the list items and i've tried a bunch of stuff but ever time the text gets passed to mkdir it breaks it up word by word so i get some thing like this.

username@user-desktop:~/Desktop/test$ ls -l
drwxr-xr-x 2 user user 4096 2007-11-11 11:26  One
drwxr-xr-x 2 user user 4096 2007-11-11 11:26 title
drwxr-xr-x 2 user user 4096 2007-11-11 11:26 Another
drwxr-xr-x 2 user user 4096 2007-11-11 11:26 more
drwxr-xr-x 2 user user 4096 2007-11-11 11:26 A.txt


Ok so heres what i've tried now if my syntax is off at all, please tell me. i want to learn all i can

So fist i thought i would cat the file and pass that to mkdir

username@user-desktop:~/Desktop/test$ cat A.txt | mkdir
mkdir: missing operand

Try `mkdir --help' for more information.


no luck so i tried


username@user-desktop:~/Desktop/test$mkdir $(cat A.txt)

i got one word directories

then i thought i'd try a for loop


username@user-desktop:~/Desktop/test$for i in $(cat A.txt) ; do mkdir $i ; done

same

username@user-desktop:~/Desktop/test$for i in $(awk '{print $0}') ; do mkdir $i ; done

again same



then i thought i should put the list items in quotes as such

"One title"
"Another title"
"One more title"

so i tired the same commands again this time i get for the output of each one.

drwxr-xr-x 2 user user 4096 2007-11-11 11:26  "One
drwxr-xr-x 2 user user 4096 2007-11-11 11:26 title"
drwxr-xr-x 2 user user 4096 2007-11-11 11:26 "Another
drwxr-xr-x 2 user user 4096 2007-11-11 11:26 more
drwxr-xr-x 2 user user 4096 2007-11-11 11:26 A.txt

and whats driveing me crazy is that if i were to do this command 


username@user-desktop:~/Desktop/test$mkdir "One title" , "Another title" 
it works but the actually text file is about 1000 entrys long.....and i don't want to do that

so any suggestions or any help at all would be great

thanks in advaced

---

### Post by cwaldbieser on 2007-11-11
```

$ cat A.txt | while read line; do mkdir "$line"; done;

```

---

### Post by LinuxGEEK7288 on 2007-11-11
Thank you so, so, so much

I knew it had to be something simple just couldn't find it, just out of curiosity do you know where i can go to look this kind of thing up in the future that way i don't have to bug any one else :). i tried google and such, but it doesn't help when you don't really know what your looking for, and reading the manuals on bash scripting can be about as bad as pulling teeth, but any way.

once again....thank you so very much

:guitar:

---

### Post by cwaldbieser on 2007-11-12
> **LinuxGEEK7288 said:**
> Thank you so, so, so much

I knew it had to be something simple just couldn't find it, just out of curiosity do you know where i can go to look this kind of thing up in the future that way i don't have to bug any one else :). i tried google and such, but it doesn't help when you don't really know what your looking for, and reading the manuals on bash scripting can be about as bad as pulling teeth, but any way.

once again....thank you so very much

:guitar:

Many people like this site: [http://linuxcommand.org/]("http://linuxcommand.org/") for shell scripting tutorials.

---

