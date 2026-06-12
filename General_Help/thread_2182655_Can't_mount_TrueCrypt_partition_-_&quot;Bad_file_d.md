---
title: "Can't mount TrueCrypt partition - &quot;Bad file descriptor&quot;"
date: 2013-10-21
forum: General Help
---

### Post by bofak2 on 2013-10-21
Running TrueCrypt 7.1a on Ubuntu 12.04 64bit.

I have an encrypted partition on my hard drive and a backup copy on a USB flash-drive.

This has worked fine for more than a year, but suddenly I am unable to mount either of these.  I get the error "Bad file descriptor".

 Volume tools >Restore Volume Header just gets me the same message.

I can find no explanation for this in any of the documentation.

Any suggestions?

---

### Post by bofak2 on 2013-10-22
Perhaps I should have been more precise in my previous post.

I am able to open TrueCrypt.  I click Select Device and choose the appropriate partition from the list.  I click Mount and enter the appropriate password.  I enter my user password when asked, and after a delay the TC window darkens for a few moments.  Then comes the message "Bad file descriptor".

I have followed the above Mount routine for over a year and it worked fine, then from one day to the next comes this.

---

### Post by impeer on 2013-11-08
I had same issue and I didn't have recent backup which meant huge  disaster for me, fortunately it turned out that the problem was in bad  chmod for var/lib/sudo ( I was playing with chmods a bit) which I  accidentally changed when trying to configure folder sharing, so for me 

```
sudo chmod 755 /var -R


```

Let me know if that helped, I found multiple people on the web complaining about this problem with no answer

---

### Post by bofak2 on 2013-11-19
No, I'm afraid this didn't help.  Always the same error:  "Bad file descriptor."

Problem is I can't mount my backups either -- same message.  I tried installing TC 7.1a on another computer (a netbook) also running Ubuntu 12.04, and tried to mount my backup.  Same message.

I can't even get an explanation of what this message means:  "Bad file descriptor."

---

