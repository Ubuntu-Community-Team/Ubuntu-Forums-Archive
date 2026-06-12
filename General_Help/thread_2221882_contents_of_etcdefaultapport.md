---
title: "contents of /etc/default/apport"
date: 2014-05-04
forum: General Help
---

### Post by vasa1 on 2014-05-04
Mine was```
# set this to 0 to disable apport, or to 1 to enable it
# you can temporarily override this with
# sudo service apport start force_start=1
enabled=1

```
According to [https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport), stable releases ship with apport disabled.

I'm wondering if mine was enabled because I installed a release candidate and not the actual release?

---

### Post by ibjsb4 on 2014-05-04
> I'm wondering if mine was enabled because I installed a release candidate and not the actual release?

In your case I would say yes, but I also think it happens with a release upgrade.  I have seen a lot of this in the forums.

---

### Post by Bashing-om on 2014-05-04
vasa1; Well.

Just do not know, but mine:
> 
sysop@1310mini:~$ cat /etc/default/apport
# set this to 0 to disable apport, or to 1 to enable it
# you can temporarily override this with
# sudo service apport start force_start=1
enabled=1
sysop@1310mini:~$ 

I have had no occasion to alter it from a 13.04 install (minimal) upgraded to 13.10.

[INDENT][INDENT]a bit of help ?
[/INDENT][/INDENT]

---

### Post by deadflowr on 2014-05-04
You need to go further down the wiki to read that apport is running on releases 12.04 and newer, but the crash interception component is not
[https://wiki.ubuntu.com/Apport#Ubuntu_12.04_and_later](https://wiki.ubuntu.com/Apport#Ubuntu_12.04_and_later)

Whatever that means.

---

### Post by bapoumba on 2014-05-04
> **deadflowr said:**
> You need to go further down the wiki to read that apport is running on releases 12.04 and newer, but the crash interception component is not
[https://wiki.ubuntu.com/Apport#Ubuntu_12.04_and_later](https://wiki.ubuntu.com/Apport#Ubuntu_12.04_and_later)

Whatever that means.

I'm learning something here.. To enable the "crash interception component", you need to add # in front of the line. I'll have a look, is it that common to use the symbol that is usually dedicated to comment out lines this way ?

---

### Post by Bashing-om on 2014-05-04
et al ;

Uohh, do I love it when we all get in a learning mode.

[INDENT][INDENT]good for the head
[/INDENT][/INDENT]

---

### Post by bapoumba on 2014-05-04
[http://www.tldp.org/LDP/abs/html/special-chars.html](http://www.tldp.org/LDP/abs/html/special-chars.html)
Looks like there is no exception to # being a comment, except for #! that does not apply here.
So could it be that the line disables the thingy and commenting out enables it ?

---

### Post by vasa1 on 2014-05-04
> **Bashing-om said:**
> ...
I have had no occasion to alter it from a 13.04 install (minimal) upgraded to 13.10.
...
As I said, mine is a full and clean install. My only crime is starting off with the RC rather than wait for the formal release.

**@Bashing-om**, I'm asking because apport kicked in with 100% CPU usage. Fortunately, I was at the keyboard and so could kill it.

I've found one other mention of apport running in a release version: [http://askubuntu.com/questions/454187/apport-gtk-100-cpu-usage-on-startup-on-ubuntu-14-04-lts](http://askubuntu.com/questions/454187/apport-gtk-100-cpu-usage-on-startup-on-ubuntu-14-04-lts)

@deadflowr, thanks for pointing out the apport/crash bit. After reading:
> Starting with 12.04, Apport itself is running at all times because it collects crash data for whoopsie (see ErrorTracker). However, the crash interception component is still disabled.
and after a reboot, ```
pgrep apport
``` comes back empty. So I don't understand the "Apport itself is running at all times" bit :(

@bapoumba,
maybe 
        'problem_types': ['Bug', 'Package'],
as it stands means "exclude" bug and package and that by commenting out the line we're asking to report everything? (I'm not a coder and so that's just a context-based guess.)

---

### Post by bapoumba on 2014-05-05
> **vasa1 said:**
> 
@bapoumba,
maybe 
        'problem_types': ['Bug', 'Package'],
as it stands means "exclude" bug and package and that by commenting out the line we're asking to report everything? (I'm not a coder and so that's just a context-based guess.)

Thanks!
To note, I have the same file after a fresh lubuntu install.

---

