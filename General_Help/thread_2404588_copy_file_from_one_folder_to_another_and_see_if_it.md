---
title: "copy file from one folder to another and see if it was no error"
date: 2018-10-25
forum: General Help
---

### Post by cazz on 2018-10-25
I was first thinking about use the cp command to copy files from one folder to another folder.
I also going to use crontab to make a schedule


but is that any better way if I want to make sure that everything is ok.
some kind of check that everything was copy ok and if not try again.
Why I ask that if first I got a error first time I copy the file.
somekind of "Input/output error".
When I did run it again it was fine??

---

### Post by Impavidus on 2018-10-25
Check the return value of your copy command. You can access it in the shell script using the variable $?. If successful,the return value should be 0, if an error occurred non-zero. That works for pretty much every command you can use in a shell script.

I wouldn't blindly retry a copy command on failure.

---

### Post by HermanAB on 2018-10-26
You should use rsync instead of cp.   It will do a checksum and ensure that the files are copied correctly.

---

### Post by cazz on 2018-10-26
I did look at rsync, does it mean it always do a checksum?

---

### Post by cazz on 2018-10-27
rsync looks nice but still I have to run it more then one time manual to make sure Everything is over and I have no error.
Is that any good script or command to make it run by it self if not Everything is over??

---

