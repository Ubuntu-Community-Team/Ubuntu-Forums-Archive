---
title: "Virus located, but file will not delete"
date: 2015-04-17
forum: General Help
---

### Post by elvis6 on 2015-04-17
I did a virus scan with ClamTk, and it found something called **PUA.Win.Exploit.CVE_2012_0110**
The path/folder and file location is **usr/share/mime/mime.cache**.
But it says that it cannot quarantine, nor delete the file.
I cannot even manually delete the file either, when I go into that folder.

When I right-click the file, the only options are

- Open with Other Applications
- Send To Mail Recipient (or other locations)
- Copy
- Create Archive
- Properties

Is the reason it can't delete, because the virus scan gave a "false  positive" and it's actually a necessary file for the system or a program to  operate, or is it because it's actually a virus which is so malicious that it  cannot be cleaned up ?

I searched and I could not find anything helpful or understandable anywhere on the internet.

---

### Post by Topsiho on 2015-04-17
It is a Windows vulnerability, your Ubuntu is immune to it, I think. Question is: how did you get it?

Search using Duckduckgo (or Google) for PUA.Win.Exploit.CVE_2012_0110, and for the CVE_2012_0110 part after that.

As it is in a system map (/usr/etc...) you need to be root to remove it (using sudo and your password). This to avoid the risk of infecting Windows computers that you connect to, which ARE vulnerable. Connection may be by wan, lan, or by USB-sticks, among others.

Topsiho

---

### Post by Holger_Gehrke on 2015-04-17
The file is a system cache of MIME type information - a binary database made from data that's available in text form from sources all over your system. It should only be writeable for the system administrator aka root. It's highly unlikely that a **P**otentially **U**nwanted **A**pplication  for Windows hides in a non-executable linux system file. I would treat it as a false positive.

---

### Post by Topsiho on 2015-04-18
Holger_Gehrke,

Thank you very much for correcting me on this subject. I think you are right!

Topsiho

---

### Post by stomiposen on 2015-04-18
[B]PUA.Win.Exploit.CVE_2012_0110.
I have it too. It wasn't there yesterday.
To find out what it is, I have made a fresh install, updated it, and scanned. (The other install was kinda old, so it was about time anyway). And bingo! Though the new install hasn't had a chance to be "contaminated" it's there again. This has come with the latest update, and is a false positive. I bet it will be fixed by the next update.
[/B]

---

### Post by Bucky Ball on 2015-04-19
Open a file manager as root and attempt to delete perhaps. Open a terminal and:

gksudo nautilus

You are in a file manager as root so delete that file and ONLY that file, then close the file manager.

---

### Post by Topsiho on 2015-04-19
Maybe in stead of deleting the file, you can rename it, and see what happens. If necessary you can rename it to the original name again.

My 2 cents :)

Topsiho

---

### Post by Topsiho on 2015-04-19
I have this file too:

-rw-r--r-- 1 root root 147156 apr 17 13:49 /usr/share/mime/mime.cache

and scanned it with clamscan, it was clean:

clamscan /usr/share/mime
/usr/share/mime/icons: Empty file
...
...
/usr/share/mime/aliases: OK
/usr/share/mime/mime.cache: OK
/usr/share/mime/types: OK
...
...
 
So if the file size of your mime.cache is the same (147156 bytes) then you should not delete or rename it.
Oh, it's a cache file, so might be different for you.

Topsiho

---

### Post by Habitual on 2015-04-20
3 suggestions:
Don't scan using PUA option enabled.
Don't scan system directories like /usr
Upload any suscpicious file to [https://www.virustotal.com/](https://www.virustotal.com/)

---

### Post by elvis6 on 2015-04-20
Thanks for all the helpful suggestions.
What I ended up doing was re-installing the entire Ubuntu OS - which fortunately is very easy, and takes a fraction of the time that it takes other major OS's to re-install.
I then looked for the file and found the same exact file.
And then I scanned that file again, after the OS re-install, and the anti-virus t gave that same report for that file.
So, I concluded that it was actually a false positive.

---

### Post by Habitual on 2015-04-21
> **elvis6 said:**
> Thanks for all the helpful suggestions.
What I ended up doing was re-installing the entire Ubuntu OS - which fortunately is very easy, and takes a fraction of the time that it takes other major OS's to re-install.
I then looked for the file and found the same exact file.
And then I scanned that file again, after the OS re-install, and the anti-virus t gave that same report for that file.
So, I concluded that it was actually a false positive.

Next time let's do it in a Virtual Machine! (re-install that is).
but otherwise, good job!

---

### Post by courseinmiracles2 on 2015-05-07
I also found this file through CLAM. I did a search of CVE_2012_0110 but I still don't know how it got there.

https://[web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2012-0110]("http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2012-0110")

Any updates on whether or not it should be deleted?

---

### Post by sotiris2 on 2015-05-07
You mean mime.cache? It's not infected it is a false positive. If you delete it you could maybe have problems with your OS identifying what type of file your files are. 
The original poster did reinstall the whole OS from scratch and Clam still detects it as a possible virus.

---

### Post by robert48 on 2015-05-17
I deleted mime.cache and now cannot get back into my user account (administrator). At login it simply reverts back to the login screen after less than a second. How can I get back into my files?

---

### Post by Bucky Ball on 2015-05-18
> **robert48 said:**
> I deleted mime.cache and now cannot get back into my user account (administrator). At login it simply reverts back to the login screen after less than a second. How can I get back into my files?

You'd greatly improve your chances by starting a new thread with a title descriptive of your issue and as much info about the problem as you can. Burying yourself two pages deep on a month old thread that is solved and has a title not related to your issue does not give you the best chance of getting support. 

Good luck with it. ;)

---

