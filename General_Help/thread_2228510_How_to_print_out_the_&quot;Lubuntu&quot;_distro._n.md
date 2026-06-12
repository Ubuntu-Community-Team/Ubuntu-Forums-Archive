---
title: "How to print out the &quot;Lubuntu&quot; distro. name for bug reports"
date: 2014-06-07
forum: General Help
---

### Post by scott092707 on 2014-06-07
When I file a bug, naturally I include the output of  "uname -a"  and "lsb_release -a",
but they only use the term "Ubuntu", and each time I need to qualify "[actually, this is Lubuntu]". Is 
there some command or command option that will output "Lubuntu"?
Perhaps it is the contents of some file or other that I could "print" in the terminal (if so, would one cp the file (or portion of it) to standard output (how?) (perhaps I should just google "linux print file command"...).

Thank you for your input.

---

### Post by vasa1 on 2014-06-07
Related: [http://askubuntu.com/questions/335695/why-does-etc-issue-show-me-ubuntu-and-not-lubuntu](http://askubuntu.com/questions/335695/why-does-etc-issue-show-me-ubuntu-and-not-lubuntu)

---

### Post by deadflowr on 2014-06-07
What about simply adding Lubuntu to the title of your crash reports?

---

### Post by TheFu on 2014-06-08
more /etc/lsb-release

---

### Post by scott092707 on 2014-06-09
> **TheFu said:**
> more /etc/lsb-release

Uh, no...

"scott@scott-AsusM2N68-AM-Plus:~$ more /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04 LTS"

"

---

### Post by TheFu on 2014-06-09
I suppose a query of which DEs was installed could be used. The non-GUI stuff should be the same between desktop distros .... in my theory. I haven't any proof.    Or the default login screen is different ... hum ... /etc/X11/default-display-manager ?  But even with that, a different DE/UI could be run.

---

### Post by scott092707 on 2014-06-10
The link above from vasa1 ([http://askubuntu.com/questions/33569...nd-not-lubuntu]("http://askubuntu.com/questions/335695/why-does-etc-issue-show-me-ubuntu-and-not-lubuntu")) gave me the answer: 
"echo $DESKTOP_SESSION"

scott@scott-AsusM2N68-AM-Plus:~$ echo $DESKTOP_SESSION
Lubuntu

Thank you!

---

### Post by vasa1 on 2014-06-10
> **scott092707 said:**
> The link above from vasa1 ([http://askubuntu.com/questions/33569...nd-not-lubuntu]("http://askubuntu.com/questions/335695/why-does-etc-issue-show-me-ubuntu-and-not-lubuntu")) gave me the answer: 
"echo $DESKTOP_SESSION"

scott@scott-AsusM2N68-AM-Plus:~$ echo $DESKTOP_SESSION
Lubuntu

Thank you!
You're welcome!

---

### Post by TheFu on 2014-06-10
> **scott092707 said:**
> The link above from vasa1 ([http://askubuntu.com/questions/33569...nd-not-lubuntu]("http://askubuntu.com/questions/335695/why-does-etc-issue-show-me-ubuntu-and-not-lubuntu")) gave me the answer: 
"echo $DESKTOP_SESSION"

scott@scott-AsusM2N68-AM-Plus:~$ echo $DESKTOP_SESSION
Lubuntu

Thank you!

Environment variables can easily be modified or cleared.  I don't think this works always. 4 different machines:
```

user@lubuntu:~$ echo $DESKTOP_SESSION

user@c720:/etc/csf$ echo $DESKTOP_SESSION
LXDE

user@hadar:~$ echo $DESKTOP_SESSION

user@romulus:~$ echo $DESKTOP_SESSION


```
Empty turned up more often than anything. Perhaps I'm doing it wrong - using an ssh connection --  doesn't work with X-forwarding either.

---

