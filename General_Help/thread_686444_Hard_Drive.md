---
title: "Hard Drive?"
date: 2008-02-03
forum: General Help
---

### Post by Phantom2099 on 2008-02-03
Ok, So basically I downloaded Ubuntu last night, installed fine. But now when I'm using XP{master} I cannot see my other hard drive anymore[has linux on it{Slave}]. Wondering why I cannot see my slave drive anymore while running XP, I have my movies and things on there...

---

### Post by Phantom2099 on 2008-02-03
Sorry for double post, I'm not 100% sure which section  of the forum this should have ended up in. Been up all night fooling around with Linux. I'm a tad tired. Would like to fix this problem before I sleep though. Need to know anymore info about my computer and or problem please ask away.

---

### Post by Holy-Fire on 2008-02-03
Windows is not smart enough to recognize Linux filesystems, so this could be the problem. How did you partition your drives? Does your slave contain now only one partition with Linux, or do your files reside on a previously (and currently!) existing Windows partition? Can you find all your files under Linux?

---

### Post by Phantom2099 on 2008-02-03
I had XP on my master, decided id install Linux on the other drive last night, had some movies and other such files on the secondary drive at the time. Now when I'm using Linux, I can see a "lost and found" folder that I cant open... Thinking maybe there in there? Either case I'd still like to be able to use that space while Using XP[Downloading, ect.].

---

### Post by seventyeights on 2008-02-03
Just a tidbit of info about the "lost & found" folder taken from [http://www.cs.wayne.edu/labPages/Unix_T/file_organ.html]("http://www.cs.wayne.edu/labPages/Unix_T/file_organ.html")

> When files are recovered after any sort of problem or failure,they are placed in the lost + found directory, if the kernel cannot ascertain the proper location in the system.

I don't have xp so I can't help you with that, but I think it's worth searching here regarding xp/linux files because I think it's quite possible.

---

### Post by Phantom2099 on 2008-02-03
It's no so much the files, I can get those back easily. It's the fact that I cannot save anything to it from XP now. I'd just like to be able to access my hard drive while using XP.

Thanks so far ^_^

---

### Post by Phantom2099 on 2008-02-03
Fixed my problem, Sorry for the post now. Future reference: "http://news.softpedia.com/news/Access-Linux-partitions-files-under-Windows-48292.shtml"

---

### Post by Phantom2099 on 2008-02-03
Just tried "EXT2 IFS"

Works flawlessly =]

---

### Post by Tyke91 on 2008-02-03
nice :)

some warning though, if you somehow contract a nasty file-deleting virus on windows, your linux will now be vulnerable. It shouldn't  be  that big of a problem, but it's good to  know.

also, if you had music on the hard drive that you installed linux on, they are probably not there anymore (installing an operating system formats a drive)

---

### Post by Phantom2099 on 2008-02-03
> **Tyke91 said:**
> nice :)

some warning though, if you somehow contract a nasty file-deleting virus on windows, your linux will now be vulnerable. It shouldn't  be  that big of a problem, but it's good to  know.

also, if you had music on the hard drive that you installed linux on, they are probably not there anymore (installing an operating system formats a drive)

Yea I noticed all my missing files :P 

I have my tera external still full, I was stupid and put some files temperately on that raptor of mine, then decided for fun to put Ubuntu on it as well. Forgot they were on there. I'm not to worried about XP, I run a nice firewall/anti virus. Scanned the files after installing them too. Softpdia doesn't normally lie either. Respected site, sorta. 

Thanks Tyke.

---

### Post by Phantom2099 on 2008-02-03
> **Tyke91 said:**
> nice :)

some warning though, if you somehow contract a nasty file-deleting virus on windows, your linux will now be vulnerable. It shouldn't  be  that big of a problem, but it's good to  know.

also, if you had music on the hard drive that you installed linux on, they are probably not there anymore (installing an operating system formats a drive)

OH, also. You can install XP without over writing files, you can select "leave system files intact" when installing Windows. :)

---

