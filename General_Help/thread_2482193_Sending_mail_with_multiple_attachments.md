---
title: "Sending mail with multiple attachments"
date: 2022-12-23
forum: General Help
---

### Post by bomberb17 on 2022-12-23
I want to send an email with mailutils with multiple (image) attachments.

For a single image attachment, the command is

```
echo -e "Test mail body" | mail -s "Test mail header" myemail@mail.com -A img1.png
```

But for two (or more) attachments, I can't find a way to make something like the below work

```
echo -e "Test mail body" | mail -s "Test mail header" myemail@mail.com -A img1.png img2.png
```

I also don't want to tar the files since I want the images to be displayed directly on the receiver phone without needing to decompress them each time.

Is there a way to achieve this?

---

### Post by philhughes on 2022-12-24
I don't have the mailutils version of mail installed to test if it supports this, but typically to specify multiple options of the same type, you need to provide the argument each time ie

```
echo -e "Test mail body" | mail -s "Test mail header" [email]myemail@mail.com[/email] -A img1.png -A img2.png
```

---

### Post by HermanAB on 2022-12-24
What version of mail is that?  I have never been able to send attachments with mail at all and used mutt to do that.

A google search for “man mail” shows the -A option is used for the account name.

---

### Post by philhughes on 2022-12-27
This is the GNU mailutils version. There are various mail programs that can be called with the "mail" command (usually via symlinks). eg heirloom-mailx (deprecated on Ubuntu), bsd-mailx. Heirloom-mailx uses "-a" to send attachments, bsd-mailx does not support attachments.

---

