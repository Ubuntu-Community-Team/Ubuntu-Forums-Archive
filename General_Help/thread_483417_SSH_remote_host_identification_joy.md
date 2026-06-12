---
title: "SSH remote host identification joy"
date: 2007-06-24
forum: General Help
---

### Post by peterx14 on 2007-06-24
I have recently reinstalled my laptop and I would now like to SSH to it, but ssh is saying:

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
```
blah blah blah.

I had a look in my ~/.ssh/known_hosts file, but the remote host address appears to be encoded so I can't see which line relates to my laptop.

So, I thought I'd be clever and create an SSH config file (~/.ssh/config) for my user which contains the following:

```

Host 192.168.0.*
    StrictHostKeyChecking ask

```

But for some reason, ssh still responds with the same message as above!!

I have also tried forcing it to use the user config file with:

```
ssh -F ~/.ssh/config 192.168.0.31
```

but it *still* didn't want to know!  So I guess I'm doing something wrong... but what is it?!

Any help appreciated!! :D

---

### Post by wildkarde on 2007-06-24
Quick and Painless way

```
cd ~/.ssh/
rm *
```

*OPPS: forgot slash*

---

### Post by peterx14 on 2007-06-25
That's "Plan-B" -- I'll use that if I can't get it to work "properly"!! ;)

---

### Post by ikonia on 2007-06-25
the hostnames/ip should be at the start of each line in the known_hosts file.

if you can't work it out, zero the known_hosts file.

---

### Post by peterx14 on 2007-06-25
I now know why I can't read my host names/IPs; it's because I have "HashKnownHosts yes" in my /etc/ssh/ssh_config file (note: it was enabled by default, so I guess thats the norm these days?). So my known_hosts file is largely gibberish. :(

I'd still like to understand why my user config file doesn't seem to work. I'm saving the "delete the entire known_hosts file" plan as a last resort!

---

### Post by wildkarde on 2007-06-25
The remote host key changed.  Just delete the file.  No big deal.  You're not really in the middle of a man in the middle attack.

---

### Post by peterx14 on 2007-06-25
At risk of my appearing pedantic, if I just delete the entire file, doesn't that mean that if any other machine that I connect to were compromised (or the connect inbetween), then I'd not know 'cos I've deleted the identification I've currently got?
If not, then why bother with the known_hosts file at all?

And at risk of my sounding like a scratched record, I'd still love to know why (ooh why) my user config (~/.ssh/config) isn't working as I'd expect! Anyone? Pleeeease?! :D

---

### Post by stylishpants on 2007-06-25
ssh is behaving exactly as it should.  I think you need to re-read the ssh_config man page. 
>      StrictHostKeyChecking
             If this flag is set to “yes”, ssh will never automatically add host keys to the ~/.ssh/known_hosts file, and
             refuses to connect to hosts whose host key has changed.  This provides maximum protection against trojan horse
             attacks, however, can be annoying when the /etc/ssh/ssh_known_hosts file is poorly maintained, or connections
             to new hosts are frequently made.  This option forces the user to manually add all new hosts.  If this flag is
             set to “no”, ssh will automatically add new host keys to the user known hosts files.  If this flag is set to
             “ask”, new host keys will be added to the user known host files only after the user has confirmed that is what
             they really want to do, and ssh will refuse to connect to hosts whose host key has changed.  The host keys of
             known hosts will be verified automatically in all cases.  The argument must be “yes”, “no” or “ask”.  The
             default is “ask”.


You set it to "ask".  Since "ask" is the default, it's no wonder that there's no change in the observed behaviour.

---

### Post by peterx14 on 2007-06-25
You're absolutely right! I should've read the man page properly. So, in the end, I had to delete my known_hosts file... which irritates me no end! :D

Anyways, thanks to *everyone* for your help!!

---

