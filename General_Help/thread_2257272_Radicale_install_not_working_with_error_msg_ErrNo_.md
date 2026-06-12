---
title: "Radicale install not working with error msg ErrNo 2"
date: 2014-12-18
forum: General Help
---

### Post by keith30 on 2014-12-18
I have recently installed Radicale on our server running 14.04. The install seems to have gone fine but it will not run and all I get is the following Ubuntu error message:

Ubuntu 14.04 has encountered an internal error
Executable Path - /usr/bin/radicale
Package - radicale 0.8-1
Problem - crash
Title - radicale crashed with IO error in_open():[Errno 2]. No such file or directory: '/var/log/radicale/radicale.log'
ApportVersion - 2.14.1-Oubuntu3.6
Architecture - i386
Crash counter - 1
Interpreter path - /usr/bin/python 2.7

I'm hoping this means something to someone who can point me in the right direction. 

Thanks

---

### Post by schragge on 2014-12-19
The radicale log file name and location changed in Debian package from the upstream default at one point. Look at description of the change in [/usr/share/doc/radicale/NEWS.Debian.gz]("http://anonscm.debian.org/cgit/collab-maint/radicale.git/tree/debian/NEWS"). You'll need to adapt your radicale installation to this change. Run these commands:
```

sudo -i
service radicale stop
rm -rf /var/log/radicale
mkdir /var/log/radicale
touch /var/log/radicale/radicale.log
chown -R radicale:adm /var/log/radicale
service radicale start
exit

```

---

### Post by keith30 on 2014-12-20
Many thanks for the advice. I will give that a go and let you know how I get on.

---

### Post by keith30 on 2014-12-27
Thanks for the link to the changes and also the summary of commands to apply. 

It all went smoothly until the 'service radicale start' part where I get the response 'not starting radicale, disabled via /etc/default/radicale' I've looked in this file and can't see what if anything I should attempt to change.

---

### Post by schragge on 2014-12-28
You should uncomment the line
```
#ENABLE_RADICALE=yes
``` in that file (just remove the # character in front of it).

---

### Post by keith30 on 2014-12-29
Thank you. 

I wondered if it was as simple as uncommenting that line... and it was. All now seems to be running ok. I'm still on a steep ubuntu learning curve and can't afford to make any mistakes so thanks for you help.

---

### Post by keith30 on 2014-12-30
Perhaps I spoke a little too soon. Today I got another error message along the lines of permission denied to var/log/radicale/radicale.log. Strangely all seemed ok yesterday and I was able to create a shared calendar. What should I be checking?

---

