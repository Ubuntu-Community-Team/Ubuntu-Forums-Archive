---
title: "Disable ssh warranty message"
date: 2013-05-29
forum: General Help
---

### Post by phailyoor on 2013-05-29
How do I disable the warranty message when logging in through ssh?

```
The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
```

---

### Post by HiImTye on 2013-05-30
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
is that part of the motd?
```
cat /etc/motd
```

---

### Post by phailyoor on 2013-05-30
no.  Ubuntu seems to dynamically generate the motd, but even so, it's not there.

---

### Post by HiImTye on 2013-05-30
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
is it part of the banner?
```
cat /etc/ssh/sshd_config | grep -i banner
```

---

### Post by CaptainMark on 2013-05-31
Unfortunately these days most of the ssh messages are dynamically created on login or reboot, and there is no set place where each bit comes from, it varies from distro to distro.  I've just spent two days digging out all the different files that create the ssh banner on my raspberry pi so I can create my own one and there was about 5 different parts to it.  I don't run Ubuntu anymore so cant tell you exactly where to start but if you use the command ```
sudo find / -iname *motd*
``` it will give you some good places to start looking.

EDIT: It's usually safe to assume that dynamic scripts wont exist inside your home directory so you can rule that out with```
sudo find / -type f ! -path */home* -iname *motd*
```

---

### Post by Lars Noodén on 2013-05-31
> **HiImTye said:**
> [CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
is it part of the banner?
```
cat /etc/ssh/sshd_config | grep -i banner
```

On 13.04 it is produced by Banner.  That can be turned off in sshd_config, but printmotd is already set to 'no' yet it prints the motd on successful login anyway.  Not sure how to stop that.

---

### Post by mikeym on 2013-05-31
I found [this post]("http://ubuntuforums.org/showthread.php?t=1661626&p=10328706#post10328706") on the forums that suggests that it can fix the issue, something to do with *pam* printing the motd so commenting it out of **/etc/pam.d/login** and/or **/etc/pam.d/sshd**.

---

### Post by Lars Noodén on 2013-05-31
> **mikeym said:**
> I found [this post]("http://ubuntuforums.org/showthread.php?t=1661626&p=10328706#post10328706") on the forums that suggests that it can fix the issue, something to do with *pam* printing the motd so commenting it out of **/etc/pam.d/login** and/or **/etc/pam.d/sshd**.

Good find.  Remming out the motd lines in /etc/pam.d/sshd and it got rid of the motd.

---

