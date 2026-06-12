---
title: "Linux Newbie - Drive Access"
date: 2007-11-01
forum: General Help
---

### Post by dpayment on 2007-11-01
This question has probably been asked a million times, but once more...

I'm a relative newbie to Linux, I've lots of experience with the "other" operating system, but that's another thing... Anyway, I created a new Ubuntu 7.10 system on my laptop the other evening. I partitioned my 160GB drive into 3 partitions, 80 GB for root, 5gb for swap and about 75Gb for a data drive, called /data.

Again, remembering that I'm new to this, I can't write to the data drive. I know this is a permissions problem, but I don't know how to fix it. I've tried finding more info in the online documentation, but most of what I've found isn't that intuitive.

I know there's a way to do this by using the 'su' account to do this, but isn't there anything else I can do?

Thanks,
Dan Payment
[email]dpayment@hotmail.com[/email]

---

### Post by rich.bradshaw on 2007-11-01
Did you format data?

Post the output of 

cat /etc/fstab

so we can see how it's setup.

(Don't know how new you are, but if you need it, you have to type the above command into the terminal, found in the accessories menu.)

You can copy and paste then by selecting the results and middle clicking where you want to paste it.)

---

### Post by fdv1 on 2007-11-01
[Is the problem anything like this]("http://ubuntuforums.org/showthread.php?t=598785")?

---

### Post by dpayment on 2007-11-01
Sorry, guess I should have explained better. I can access the drive, I can see the "lost" folder on the drive, but I can't write to the drive. All the write options in the file manager menu are greyed out. It literally is a matter of permissions. The drive is formatted I think it's "EXF???" or something like that (new file system to me, haven't learned all the vernacular yet.) 

Dan

---

### Post by fdv1 on 2007-11-03
Unfortunately, there is no su login in any *ubuntu based distro. I won't give reasons because someone will engage me in a debate about it.

Anyway, there are ways to fix it but we need to see your /etc/fstab file.

---

