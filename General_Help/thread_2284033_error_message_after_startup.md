---
title: "error message after startup"
date: 2015-06-26
forum: General Help
---

### Post by rybnik on 2015-06-26
Whenever I log in, I get two occurrences of [this error message]("http://i.imgur.com/zc73SZE.png").  But I don't see any reason for that message.  Any way to get rid of it?

---

### Post by grahammechanical on 2015-06-26
If you choose to report the problem a dialog will appear and the system will start to collect various system logs. This information will not be sent off without your approval. The dialog will also have a Details button. Click that and you will get information as to what is causing the problem.

The best way to get rid of error messages like this is to find out what is causing the problem and correct the cause. If we can.

---

### Post by v3.xx on 2015-06-26
Thats apport

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

And it can give a false report at times.

[https://www.google.com/search?client=ubuntu&channel=fs&q=false+positive+Apport&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=false+positive+Apport&ie=utf-8&oe=utf-8)

---

### Post by cariboo on 2015-06-26
You can check out what application crashed, by having a look at /var/crash. Open a terminal and type the following command:

```
ls -l /var/crash
```

Earlier in the wily development cycle I was seeing the same thing, once nautilus was updated, the error message disappeared. Just to be sure, I deleted the contents of /var/crash.

---

### Post by matt_symes on 2015-06-27
Hi

I get this error message if I forget to unencrypted my encfs folder that contains most of my sensitive application settings.

As caribou suggested, the easiest way to remove the message is to open a terminal and type

```
sudo rm /var/crash/*
```

If you want to see what crashed type

```
ls /var/crash/
```

As has been highlighted, it's used by Apport to upload crash reports to Canonical so they can fix the software.

Windows has a similar mechanism.

Kind regards

---

### Post by rybnik on 2015-06-28
@[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323")

I see what you're saying, but I'm typically hesitant to report anything, especially when I'm pretty sure it's a false positive.

@[**[COLOR=#000000]v3.xx[/COLOR]**]("http://ubuntuforums.org/member.php?u=1937239")
okay

@cariboo, matt symes
That fixed it.
[URL="http://ubuntuforums.org/member.php?u=77104"][B][COLOR=#990303][B]
[/B][/COLOR][/B][/URL]

---

