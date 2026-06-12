---
title: "How do I setup auto monitoring for my software raid?"
date: 2006-07-14
forum: General Help
---

### Post by fyleow on 2006-07-14
I have software RAID setup on my Ubuntu computer and I want it to automatically email me when a hard drive fails.  I know this can be done using mdadm but I'm not sure how to get it working.

I typed the following command in terminal:

mdadm --monitor --mail=myemailaddress --test /dev/md0

It successfully sends an email to my inbox as a test.

Then I used this command to start monitoring:

madadm --monitor --mail=myemailaddress --delay=1800 /dev/md0

Now my terminal just sits there and I don't get a confirmation or control back.  I have to terminate it using Ctrl-C.  Does that mean I have to keep this window open for it to work?  What happens if I restart Ubuntu?  Will the monitoring process stop?  Is there a way to get it running in the background and automatically start up when I reboot?

Thanks.

---

### Post by fyleow on 2006-07-14
Anybody know please?

---

### Post by racmar on 2007-07-04
I know this is quite an old thread, but I was looking for the same thing, so I figured I'd answer it anyway.

you can either edit /etc/default/mdadm directly or you can run:
```
dpkg-reconfigure mdadm
```

---

### Post by ihavenoideax2 on 2007-07-18
Hi

I can't even get it to mail me. I have gone though countless walk though and none worked. Please help me since i really want to set this up.

Thanks in advance.

---

### Post by racmar on 2007-07-18
can you actually send email?  some ISP's block outgoing on port 25.  I would open a telnet session to a known email provider ex:
```
telnet somehost.somedomain.com 25
```
If that works, then you probably have a setup issue with either your postfix install or your mdadm configuration.  Also note, postfix *can* be setup to use your ISP's email as a relay point, but that is a discussion for anther thread.

---

### Post by ihavenoideax2 on 2007-07-23
Nope doesnt work. I am using gmail by the way. Do you think that might be whats causing this to happen?

---

### Post by racmar on 2007-07-23
Sorry, but I didn't understand what doesn't work.  Did you try the telnet command?  What appeared when you did that?  To telnet gmail, I did;  this is what I found:

```
telnet gmail-smtp-in.l.google.com 25

Trying 66.249.83.114...
Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP h7si5561449wxd
quit
Connection closed by foreign host.

```


If you cannot telnet to an outside email provider, you *must* use your ISP as a relay point.  If you need help /w the ISP, contact them and/or open a separate thread.

---

### Post by Jimmy The Clown on 2007-09-08
> **racmar said:**
> I know this is quite an old thread, but I was looking for the same thing, so I figured I'd answer it anyway.

you can either edit /etc/default/mdadm directly or you can run:
```
dpkg-reconfigure mdadm
```

This worked quite well for me. Just reconfigured with my gmail address and then to test I ran:
```
mdadm --monitor --test /dev/md1
```

Though I did have to ctrl-c to end the command. Test email showed up in gmail with no issue. Thanks for the help.

-JTC

---

