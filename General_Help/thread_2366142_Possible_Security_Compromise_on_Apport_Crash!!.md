---
title: "Possible Security Compromise on Apport Crash!?!?"
date: 2017-07-14
forum: General Help
---

### Post by Rick St. George on 2017-07-14
Could not find anything related on a search.  Running UbuntuStudio v16.04 LTS, on 64bit 8core CPU with 32GB Ram and SSD.
Right after start up ...

Pop-up window:  System Program Problem Detected ...do you want to report the problem? (cancel / report problem)

Report Problem: Please enter your password to access problem reports of system programs.
    An application is attempting to perform an action that requires privileges. Authentication is required.
Details: 
  Action: com.ubuntu.apport.apport-gtk-root
  Vender: apport

=================

It seems this could be a Security Problem as this could upload our Login Password. Link to Apport shows it can upload private data such as passwords, credit card, and other sensitive info.

So how can we determine if this is safe or not ? ? ? Any ideas or suggestions appreciated for all concerned.

Thanks!
Rick

---

### Post by SeijiSensei on 2017-07-14
I don't see anything perfidious here.  It's asking for your password because the system needs root ("sudo") privileges to send the report.  I can't imagine anything like passwords would be included in that document.

---

### Post by Rick St. George on 2017-07-14
From: [https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

Why Apport is Disabled by Defualt:
Apport collects potentially sensitive data, such as core dumps, stack  traces, and log files. They can contain passwords, credit card numbers,  serial numbers, and other private material. 

-----------------

So you can see my logic for caution!!!

---

### Post by vasa1 on 2017-07-14
I think there's an off-line mode as well. You maybe able to vet the report and then submit it.

See if jeremy31's post here helps: [https://ubuntuforums.org/showthread.php?t=2364875&p=13662904#post13662904](https://ubuntuforums.org/showthread.php?t=2364875&p=13662904#post13662904)

Although I went through that process, I can't remember whether the process generated a human-readable file. I trust Canonical ;)

---

### Post by Rick St. George on 2017-07-14
Thanks "vasa1", but that is utilizing apport-cli.  You will notice in my first post, the crash is apport!

---

### Post by vocx on 2017-07-14
> **Rick St. George said:**
> Could not find anything related on a search.  Running UbuntuStudio v16.04 LTS, on 64bit 8core CPU with 32GB Ram and SSD.
Right after start up ...

Pop-up window:  System Problem Detected ...do you want to report the problem? (cancel / report problem)

Report Problem: Please enter your password to access problem reports of system programs.
    An application is attempting to perform an action that requires privileges. Authentication is required.
Details: 
  Action: com.ubuntu.apport.apport-gtk-root
  Vender: apport

=================

It seems this could be a Security Problem as this could upload our Login Password. Link to Apport shows it can upload private data such as passwords, credit card, and other sensitive info.

So how can we determine if this is safe or not ? ? ? Any ideas or suggestions appreciated for all concerned.

Thanks!
Rick
It seems you have some misconceptions. I'll explain.

Maybe you think that Apport is some sort of malware, and that it is trying to upload and steal your personal information? It is not.

Apport is a program created by the developers of Ubuntu (Canonical). When your system crashes, in fact, when any program crashes, it is used to collect information in order to create a bug report for [https://bugs.launchpad.net/](https://bugs.launchpad.net/). A proper bug report will contain information on your system, so Apport automatically collects some information that would be useful for the developers to investigate the cause of the crash. In theory, the data that Apport collects "could" include sensitive information, but that is not its main purpose. Basically what it collects is technical system information, like the type of processor you are using, the version of you video card, the kernel modules under use, and so on. It does not go into your "/home" folder searching for your passwords and things like that.

You do not need to run Apport after a crash. It is totally optional. In past versions of Ubuntu, maybe 9.04, and around that time, Apport was active by default, so whenever there was a crash many new users would click "yes" on every dialogue, and they would create many bug reports. Probably this generated many duplicate bug reports in [https://bugs.launchpad.net/](https://bugs.launchpad.net/) that it became hard to actually investigate the problems. So nowadays it seems Apport is not active by default, to prevent people from creating too many, unnecessary bug reports.

In summary, Apport is a "safe" program, created by the developers of Ubuntu themselves, with good intentions. The "apport-cli" command is the same program, it's just a command line version, instead of the graphical dialogue that you get.

So, if you don't have experience reporting bugs, or have not even heard of [https://bugs.launchpad.net/](https://bugs.launchpad.net/), then just don't worry. When you see the Apport dialogue simply decline to run it, and move on. Of course, if you get the dialogue every time, that means something is crashing constantly in your system, so you should probably seek a solution to that.

---

### Post by Rick St. George on 2017-07-14
Thanks "vocx", but notice in Post #1, it is apport that crashed. Notice also the URL next to ACTION [com.ubuntu.apport.apport-gtk-root]("http://com.ubuntu.apport.apport-gtk-root"). Does that look valid to you? Perhaps that is the problem! How did that get corrupted?

---

### Post by vocx on 2017-07-14
> **Rick St. George said:**
> Thanks "vocx", but notice in Post #1, it is apport that crashed. Notice also the URL next to ACTION [com.ubuntu.apport.apport-gtk-root]("http://com.ubuntu.apport.apport-gtk-root"). Does that look valid to you? Perhaps that is the problem! How did that get corrupted?
Yes, it looks perfectly valid.

Apport is a program too. It can crash too. I don't see any problem. What problem do you see exactly? Actually, your first post does not say that Apport crashed. It only asks for your permission to launch Apport.

Apport, since it collects system information, probably needs root access to get some kernel files that normally are not accessible to the regular user, so that is probably why it needs to launch an "apport-gtk-root" function.

So, my point is, do you have a valid reason to think there is a problem? Or is this just speculation on your part? Are you experienced in security matters in Linux?

Computers work in mysterious ways, sometimes the system crashes, and you just reboot and everything continues working fine again. There is no such thing as a bug-free system.

---

### Post by Rick St. George on 2017-07-14
> **vocx said:**
> Yes, it looks perfectly valid.

So, my point is, do you have a valid reason to think there is a problem? Or is this just speculation on your part? Are you experienced in security matters in Linux?

No - except for the post about what Apport may upload. Was not sure what program was asking for my SYS PASSWORD as it could upload it to whomever. Any "auto reporting" that asks first for your System Password is suspect. That doesn't take a genious ... just a little normal precautionary skepticism.

I'll just hit "CANCEL" rather than take any chances.

Thanks!
Rick

---

### Post by vocx on 2017-07-14
> **Rick St. George said:**
> No - except for the post about what Apport may upload. Was not sure what program was asking for my SYS PASSWORD as it could upload it to whomever. Any "auto reporting" that asks first for your System Password is suspect. That doesn't take a **genious** ... just a little normal precautionary skepticism.

I'll just hit **"CANCEL"** rather than take any chances.

Thanks!
Rick
Correct. Being skeptic is good. But there is no need to go overboard and cry "security problem!!!" without really knowing what is happening. This just spreads misinformation, which is bad, especially for new users who may come across your thread in the future.

As I mentioned, you can just hit cancel, and move on, and no information will be collected or transmitted anywhere.

---

