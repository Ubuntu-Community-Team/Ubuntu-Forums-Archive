---
title: "apt-get error - can't install anything"
date: 2007-01-01
forum: General Help
---

### Post by m.musashi on 2007-01-01
I have a relatively clean install of edgy. It was just reinstalled several days ago. I have added in the stuff I like (beryl, automatix) but it was working fine. However, today I tried to install scrot and I got this error:
```
dpkg: syntax error: unknown user `postfix' in statoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)
```
I searched around a bit and found some dpkg commands (dpkg --configure -a) that sounded like it might fix it but no luck. anything with apt-get (upgrade, install) returns the same error.

Any idea what caused it and how to fix it? It worked a few days ago when I installed xchat and I don't think I did any other installs since then.

Thanks.

---

### Post by raul_ on 2007-01-01
Did you add a new user and then deleted it?

---

### Post by raul_ on 2007-01-01
Anyway...just try 
```

sudo gedit /var/lib/dpkg/statoverride

```

and comment the lines that say postfix , and then try again. If it works i think it's a pretty safe choice. My file only has 2 lines:

```

@raul:~$ cat /var/lib/dpkg/statoverride
hplip root 755 /var/run/hplip
root fuse 4750 /usr/bin/fusermount

```

---

### Post by m.musashi on 2007-01-01
> **raul_ said:**
> Did you add a new user and then deleted it?

Well, sort of. I have /home on a separate partition and after reinstalling I had to add back the rest of the family as users. Some of them wouldn't load so I copied and deleted the contents of their /home and then deleted and readded the users and then copied back the contents of /home. I don't know why it was giving me troubles with the users but it sounds like that might have had something to do with my problem.

> **raul_ said:**
> Anyway...just try 
```

sudo gedit /var/lib/dpkg/statoverride

```

and comment the lines that say postfix , and then try again. If it works i think it's a pretty safe choice. My file only has 2 lines:

```

@raul:~$ cat /var/lib/dpkg/statoverride
hplip root 755 /var/run/hplip
root fuse 4750 /usr/bin/fusermount

```

I tried what you suggested but it didn't help. I still get the same error. Here is what the statoverrride file contains now after commenting one line.

```
root postdrop 02555 /usr/sbin/postqueue
hplip root 755 /var/run/hplip
#postfix postdrop 02710 /var/spool/postfix/public
root postdrop 02555 /usr/sbin/postdrop
```

Should I make mine look like yours?

---

### Post by raul_ on 2007-01-01
I find that copying other users config files can be somewhat risky :-k you can always do a backup of your file, and then copy my contents to your file and then try to run it. Just to be safe, try logging out and in again, and then trying again, leaving the file as you have it, i.e, with that line ommited

---

### Post by m.musashi on 2007-01-02
I did try logging in and out but the comment didn't help. I'll try your file contents but I assume there are some username bits that need to change. It's possible that the copying of the other user /home directory could have set the user permissions to root since I had to use sudo to move them. I don't know what that would have to do with apt-get but I could try and reset all the permissions.

I'll try a couple things and report back. In the meantime, if anyone has any other thoughts I'd be happy to listen.

Thanks.

EDIT: okay, I reset all permissions but that didn't help. I then copied your file contents and changed @raul to @jim (my user name and now I get a similar but different error.
```
dpkg: syntax error: unknown user `@jim:~$' in statoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)
```
How can I be an unknown user? What is this file supposed to contain?

---

### Post by m.musashi on 2007-01-02
Okay, I did a bit more digging and I found a suggestion to delete everything in the statoverride file except
```
hplip root 755 /var/run/hplip
```
and that seemed to fix it. I ran an upgrade with no problems and was able to instal scrot without the error so that seemed to fix it.

However, I would like to userstand what exactly went wrong and why this worked. As far as I can tell, when I chaned permissions of other user folders it had something to do with this. Other than that I really don't know what happened or why.

Thanks for the help.

---

### Post by raul_ on 2007-01-02
Just to say that you weren't supposed to copy the ```
@raul:~$ cat /var/lib/dpkg/statoverride
``` part ;)

---

### Post by m.musashi on 2007-01-02
Yeah, I tried changing the @raul thinking that was your username and it should be mine but it didn't work. Deleting everything but the one "hplip" line did work. Yours had one more line below that. Is that important? I noticed on a live cd that only the "hplip" line is there.

If you have a moment, can you look at [this](http://www.ubuntuforums.org/showthread.php?p=1956988#post1956988) thread. I have a problem on a different computer that surfaced after using chown to change file permissions and I'm starting to think that problem is realted to this problem but I can't even boot that computer.

Thanks.

---

### Post by russell.h on 2007-07-02
Hmm... for anyone who has this problem in the future, never put a newline at the end of the file.

---

### Post by rillip on 2007-07-03
postfix is a mail program kind of like sendmail, only it was designed with security in mind (sendmail kind of added it as an afterthought and it shows).  I don't know what you're doing that you have it installed, but something obviously went wrong with a configuration therein.

---

### Post by Makaai on 2007-07-15
I had the same error.I commen line postfix and now it gives me this:

```
dpkg: syntax error: invalid uid in statoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2
```)

any help?

---

### Post by Makaai on 2007-07-15
up.
any help?

---

### Post by outlaw686 on 2007-08-27
I just 

sudo apt-get remove postfix and it worked fine

sure there are plenty of other ways to delicacy do this but I prefer the hack and slash method.

Note, I do remember I installed mailx and yes I did also happen to make a user before having this problem, could be one of the two.

---

### Post by rahul_bhise on 2007-09-15
i also had a same error and i delete everything in the statoverride file except the line hplip root 755 /var/run/hplip

and it worked

though i did not know what does this mean but it work

---

### Post by svalding on 2007-10-25
I'm having a an issue related to this as well. I got rid of all the contents but that hplip line, but now I am getting an error stating the file contains an empty line.

opening the file up in text editor shows that there is indeed NO blank lines in the file. Any ideas? This one is stumping me. 

All I want is mysql server!!! hahaha

---

### Post by russell.h on 2007-10-25
You don't have a blank line at the end of the file do you? Thats what gave me troubles.

---

