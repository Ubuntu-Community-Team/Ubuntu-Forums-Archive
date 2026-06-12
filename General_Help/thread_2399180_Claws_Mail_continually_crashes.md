---
title: "Claws Mail continually crashes"
date: 2018-08-22
forum: General Help
---

### Post by LeeU on 2018-08-22
I am using Claws Mail v.3.9.3, on Ubuntu 14.04 (32-bit). It has been working fine up until last week. Now, when I check an email account it shows it downloading the email and then, when done, it crashes, with no email downloaded.

These are the errors I receive in the "apport.log":

```
    ERROR: apport (pid 12562) Mon Aug 20 15:27:02 2018: called for pid 12536, signal 11, core limit 0, dump mode 1
    ERROR: apport (pid 12562) Mon Aug 20 15:27:02 2018: executable: /usr/bin/claws-mail (command line "claws-mail")
    ERROR: apport (pid 12562) Mon Aug 20 15:27:02 2018: debug: session gdbus call: (true,)

    ERROR: apport (pid 12562) Mon Aug 20 15:27:24 2018: wrote report /var/crash/_usr_bin_claws-mail.1000.crash
    ERROR: apport (pid 12708) Mon Aug 20 15:33:16 2018: called for pid 12694, signal 11, core limit 0, dump mode 1
    ERROR: apport (pid 12708) Mon Aug 20 15:33:16 2018: executable: /usr/bin/claws-mail (command line "claws-mail")
    ERROR: apport (pid 12708) Mon Aug 20 15:33:16 2018: debug: session gdbus call: (true,)

    ERROR: apport (pid 12708) Mon Aug 20 15:33:16 2018: this executable already crashed 2 times, ignoring
    [Started program from terminal:]
    ERROR: apport (pid 12787) Mon Aug 20 15:35:44 2018: called for pid 12775, signal 11, core limit 0, dump mode 1
    ERROR: apport (pid 12787) Mon Aug 20 15:35:44 2018: executable: /usr/bin/claws-mail (command line "claws-mail")
    ERROR: apport (pid 12787) Mon Aug 20 15:35:44 2018: debug: session gdbus call: (true,)

    ERROR: apport (pid 12787) Mon Aug 20 15:35:44 2018: this executable already crashed 2 times, ignoring
```

In the "syslog" I get this:

    ```
lee-desktop rtkit-daemon[1842]: Successfully made thread 12529 of process 4351 (n/a) owned by '1000' RT at priority 2.
    Aug 20 15:25:40 lee-desktop rtkit-daemon[1842]: Supervising 9 threads of 3 processes of 1 users.
    Aug 20 15:27:01 lee-desktop kernel: [21592.579522] claws-mail[12536]: segfault at f947894 ip b108b8d5 sp bfa36e80 error 6 in tnef_parse.so[b1085000+c000]
```

The "/var/crash/_usr_bin_claws-mail.1000.crash" file contents [are located here]("https://leeunderwood.org/downloads/claws-mail.crash.txt")

I reinstalled the program but to no avail.

Any ideas of what the problem is? I've been using Claws Mail for many years and really like it. I am now having to use Evolution; I've tried Thunderbird, and checking mail via browser -- none one of which I like.

---

### Post by TheFu on 2018-08-22
I would try using a new userid on the Ubuntu system and setting up Claws there to see if it is a system issue or just an issue with the personal settings for that 1 account.

---

### Post by LeeU on 2018-08-22
I am using a separate /home directory. Won't a new user/install overwrite the previous one?

---

### Post by TheFu on 2018-08-22
> **LeeU said:**
> I am using a separate /home directory. Won't a new user/install overwrite the previous one?

Nobody said anything about reinstalling anything.  Let me check ... nope.

Linux is multi-user.  Unless you did something very odd, adding a new userid (it must be different from the your current userid) will give that new user a different HOME. That's kinda the whole point of a multi-user system.  All Unix-like systems work in a similar way ... so your smartphone, tablet, and basically any non-Microsoft computer will work this way.

After you create the new userid, logout, then login using that new userid.  All the different settings will be "factory fresh".   Start Claws from the menu and setup the account using your normal login/password stuff.  How does that work?

---

### Post by LeeU on 2018-08-22
Nope, nothing about reinstalling anything. Okay, so Claws Mail works with the new user. (I don't use Linux as a multi-user system.) The problem happens with all the account on the original user. W/o trying to second guess, what would you suggest?

---

### Post by TheFu on 2018-08-22
> **LeeU said:**
> Nope, nothing about reinstalling anything. Okay, so Claws Mail works with the new user. (I don't use Linux as a multi-user system.) The problem happens with all the account on the original user. W/o trying to second guess, what would you suggest?

Seems the issue is with the claws data or config in the original user's HOME.  It could be corrupt or somehow a setting might have been changed to an incompatible value.  

What I would do is restore the claws mail files and settings from the backup made the night before I noticed the issue.  I have daily versioned backups. They come in handy for things like this.

Depending on whether it was the config or the data that was corrupted, I'd check and  watch the storage for any failures - starting with the SMART data that all spinning and SSD storage provides. Depending on the output from that, I'd take appropriate steps to swap cables, the disk or perhaps, do nothing.  But I'd ensure my automatic, daily, backups kept working.  They can solve all sorts of problems - corruption, security, break-ins, accidental deletion, and new stuff like crypto-malware, when performed well.

If you don't have backups, there isn't much we can do without very detailed knowledge about Claws settings and data storage. I simply don't have that expertise. Sorry.  The sad thing is that the entire issue could be 1 character in a setting somewhere and trivial to fix.

---

### Post by Yellow Pasque on 2018-08-23
```
segfault ... in tnef_parse.so
```

Could be: [http://www.thewildbeast.co.uk/claws-mail/bugzilla/show_bug.cgi?id=3457](http://www.thewildbeast.co.uk/claws-mail/bugzilla/show_bug.cgi?id=3457)

---

### Post by LeeU on 2018-08-23
After uninstalling and purging, I reinstalled Claws Mail and it seems to work fine now. Thanks for the help! (Not sure how to mark it 'solved'.)

---

### Post by TheFu on 2018-08-23
Solved ... I know what you mean!   Top right of the page "**Thread Tools**" ... there's a button.  

Would you mind going into the exact "purging" part?  sudo apt purge {package}  shouldn't touch any files in a user's home directory.  Did you manually do something in HOME?

---

### Post by LeeU on 2018-08-26
This is the method I used: [https://www.howtoinstall.co/en/ubuntu/precise/claws-mail?action=remove]("https://www.howtoinstall.co/en/ubuntu/precise/claws-mail?action=remove")

---

