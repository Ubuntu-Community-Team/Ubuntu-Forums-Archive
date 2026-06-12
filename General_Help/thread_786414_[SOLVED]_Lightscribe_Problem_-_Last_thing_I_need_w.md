---
title: "[SOLVED] Lightscribe Problem - Last thing I need windows for!!!"
date: 2008-05-08
forum: General Help
---

### Post by pbeesley on 2008-05-08
OK right so I have an LG lightscribe drive and I'm running the 32bit version of Hardy Heron. I have installed the lightscribe software (official) and then after that installed the LaCie 4L software (although it didn't make a link on the applications menu but...whatever)

I can get the software working but it can't detect my lightscribe drive. :(

What am I doing wrong and how can I fix it :(

Thanks everyone for the help I know I'll get :)

OTHER INFO:
I'm new to linux
I've got the drive set up as a writable drive using DVD_RAM discs.
It works in windows 
Yes I do have a lightscribe DVD in the drive
and Yes it is label side down

---

### Post by eladamri on 2008-05-08
Here is the solution thread: [http://ubuntuforums.org/showthread.php?t=623251]("http://ubuntuforums.org/showthread.php?t=623251")

---

### Post by pbeesley on 2008-05-09
Ok that link didn't help :( I did everything it said but I'm still stuck. Someone please help. I don't want to use windows anymore

---

### Post by pbeesley on 2008-05-11
anyone :(

---

### Post by eladamri on 2008-05-11
My problem was related to the fact that I'm running a 64-bit processor. From the above thread here is the pertinent information that fixed my problem. Also, this was in Gusty. When I installed lacie on Hardy it just worked.

> 2) I am using 64bits Gutsy, so as I exit 4L-GUI from the terminal, I received this errors:
4L-cli: error while loading shared libraries: liblightscribe.so.1: cannot open shared object file: No such file or directory

And that, caused my DVD-ROM unable to detect at the print dialog box.

So to fix it I copied both:
liblightscribe.so
liblightscribe.so.1

from /usr/lib to /usr/lib32

After, it worked for me.

---

### Post by pbeesley on 2008-05-12
hmm I copied those files in but no luck

---

### Post by pbeesley on 2008-05-12
Ok someone please help this is how far I've got :(

[IMG]http://www.tng3.co.uk/Lightscribe_Woe.png[/IMG]

---

### Post by pbeesley on 2008-05-13
ok I just reinstalled hardy so I've got a fresh start. What steps should I be taking because I no longer have a windows partition so I REALLY need this to work.

Thanks

---

### Post by eladamri on 2008-05-13
Are you still having the exact problem?

---

### Post by pbeesley on 2008-05-13
i was holding off on doing anything cause I didn't want to mess it all up again :(

---

### Post by pbeesley on 2008-05-16
ok fixed, I needed to run the app as root.

---

