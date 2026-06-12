---
title: "Can I ftp using the terminal?"
date: 2007-12-02
forum: General Help
---

### Post by enchance on 2007-12-02
I'm currently using filezilla to transfer files to my remote server at [johnimbong.com]("http://johnimbong.com"), but I have grown to like the terminal and would like to use it more often. Is there a way for me to transfer files using the terminal to my remote server?

---

### Post by bwald on 2007-12-02
Yes, you can use the command line program "ftp."  Use it like this:

```
ftp user@host.tld
```

Once you've logged in to your remote host, type "help" to see all of the options.  The most common ones are "get" and "send" which have obvious meanings.

---

### Post by enchance on 2007-12-03
> **bwald said:**
> Yes, you can use the command line program "ftp."  Use it like this:

```
ftp user@host.tld
```

Once you've logged in to your remote host, type "help" to see all of the options.  The most common ones are "get" and "send" which have obvious meanings.

What is "tld"?

---

### Post by bwald on 2007-12-03
Oh, sorry, that just means "top level domain."  Either .com, .org, or whatever your location is. 

In your example you would use johnimbong.com.

---

### Post by dagnabit dang doohickey on 2007-12-03
ftp is not secure. You should consider using sftp instead.

---

### Post by enchance on 2007-12-04
> **dagnabit dang doohickey said:**
> ftp is not secure. You should consider using sftp instead.

So I simply replace "ftp" with "sftp" right?

---

### Post by dagnabit dang doohickey on 2007-12-04
Assuming your host accepts sftp connections, yes.

---

### Post by enchance on 2007-12-04
A list of commands come out when I type
```
ftp> ?
```
How do I know how to use these commands? What are their options?

---

### Post by sethvath on 2007-12-04
[http://linux.about.com/od/commands/l/blcmdl1_ftp.htm](http://linux.about.com/od/commands/l/blcmdl1_ftp.htm)

---

### Post by enchance on 2007-12-05
> **sethvath said:**
> [http://linux.about.com/od/commands/l/blcmdl1_ftp.htm](http://linux.about.com/od/commands/l/blcmdl1_ftp.htm)

Thanks. Also, I don't think sftp works on my server. I keep getting this error
```
Received message too long 1416128883
```

---

### Post by sethvath on 2007-12-05
So long as your webhost supports ssh, you can try scp to securely copy over files.

---

### Post by enchance on 2007-12-05
> **sethvath said:**
> So long as your webhost supports ssh, you can try scp to securely copy over files.

How do I use scp?

---

### Post by dagnabit dang doohickey on 2007-12-05
> Thanks. Also, I don't think sftp works on my server. I keep getting this error
Actually, it appears that you can connect with sftp. (Also: any host that doesn't have sftp access is subpar and should be avoided.)

The sftp and scp (secure copy) programs are part of ssh (secure shell). If you have not previously logged in to your host with ssh, then the host may be trying to send you a message asking if you will accept the host key. Once you accept the host key, you won't be asked for this confirmation on subsequent logins. The problem is sftp is not capable of handling this message/interaction, thus:
> Received message too long

So, login with ssh:
```
ssh username@somehost
```

Then read the message and accept the host key. You can then logout of the ssh connection:
```
logout
```

Now try sftp.

[Note: some hosts may require that you turn on shell (ssh) access in your webhosting control panel.]

---

### Post by psusi on 2007-12-05
The answer to most questions that start with "how to use xxxx" is RTFM.  Start with man xxxx and you can usually answer your own question, or at least formulate more specific questions and better understand the answers.

---

### Post by dagnabit dang doohickey on 2007-12-05
Once you get past this hurdle, there is even more goodness awaiting if you wish: sshfs.

sshfs will allow you to mount your remote directories on your local filesystem, which you can then manipulate as you would any other local files.

---

### Post by enchance on 2007-12-05
> **dagnabit dang doohickey said:**
> Once you get past this hurdle, there is even more goodness awaiting if you wish: sshfs.

sshfs will allow you to mount your remote directories on your local filesystem, which you can then manipulate as you would any other local files.
I can't ssh! I keep getting
```
Last login: Wed Dec  5 10:42:12 2007 from 203.177.220.150
This account is currently not available.
Connection to johnimbong.com closed.

```
What's happening?

---

### Post by psusi on 2007-12-05
That account is not allowed to log in on the server?

---

### Post by dagnabit dang doohickey on 2007-12-05
Connecting to ```
username@johnimbong.com
``` is probably wrong. More likely its in the form ```
username@servername.yourhost.com
```

You should check your webhost control panel, as the information you need may be there. Otherwise, check you host's support faq or even email them asking to clear up some of this information.

---

