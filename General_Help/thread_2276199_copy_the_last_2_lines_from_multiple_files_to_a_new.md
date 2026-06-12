---
title: "copy the last 2 lines from multiple files to a new_file.txt"
date: 2015-04-30
forum: General Help
---

### Post by sohlinux on 2015-04-30
How can I copy the last 2 lines from all files in a folder to a new_file.txt and at the top of each 2 lines in the new_file.txt show the name of the file which the lines were taken from?

eg.

/home/me/file1.txt 
/home/me/file2.txt

new_file.txt will show the following

/home/me/file1.txt 
tom freda john bla 
apple orange banana

--

/home/me/file2.txt
house bla gearge 
january yes no tommy fred bla

thanks

---

### Post by steeldriver on 2015-04-30
How picky are you about the header format? the `tail` command will basically do that for you e.g.

```

$ tail -n2 file1.txt file2.txt > new_file.txt
$
$ cat new_file.txt
==> file1.txt <==
Y
Z

==> file2.txt <==
9
10

```

---

### Post by sohlinux on 2015-05-01
thanks and for all log files in /var/log  I figured

tail -n10 /var/log/*log > /var/log/log.txt

mail -s "tail of /var/log/ 10 lines" [email]me@mail.com[/email] < /var/log/log.txt

but it attaches it as a file called noname
how do I put the text in the body of the mail?

thanks

---

### Post by btindie on 2015-05-01
Try using the 'mailx' command instead. I've found that it often works differently depending on which client is installed.

You can find that out by running
```
update-alternatives --query mailx
```

e.g. ```
$ update-alternatives --query mailxLink: mailx
Status: auto
Best: /usr/bin/heirloom-mailx
Value: /usr/bin/heirloom-mailx


Alternative: /usr/bin/heirloom-mailx
Priority: 60
Slaves:
 Mail /usr/bin/heirloom-mailx
 Mail.1.gz /usr/share/man/man1/heirloom-mailx.1.gz
 mail /usr/bin/heirloom-mailx
 mail.1.gz /usr/share/man/man1/heirloom-mailx.1.gz
 mailx.1.gz /usr/share/man/man1/heirloom-mailx.1.gz
```

That one works fine for me and has an '-a' option to include an attachment. I think bsd-mailx may be the default one? So you may want to replace it with 'heirloom-mailx'.

You could of course just do
```
$ tail -n10 /var/log/*log | MAILRC=/dev/null mailx -n -s "tail of /var/log/ 10 lines" me@mail.com
```

---

### Post by sohlinux on 2015-05-01
perfect. thanks :)

---

