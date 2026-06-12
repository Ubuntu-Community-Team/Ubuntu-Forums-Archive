---
title: "Problems verifying .deb of ClamTk from official site"
date: 2021-11-19
forum: General Help
---

### Post by thefrenchchef on 2021-11-19
Hi All,

I recently installed the version 6.13.deb of clamtk on ubuntu 18.04 from:

[LIST]
[*][https://gitlab.com/dave_m/clamtk/-/wikis/Downloads](https://gitlab.com/dave_m/clamtk/-/wikis/Downloads) 
[/LIST]

Prior to installation, I checked the sha256, and it was fine. I subsequently learned about signatures, so I went to recheck my download.

I followed the instructions at [https://gitlab.com/dave_m/clamtk/-/wikis/ClamTk-Hashes](https://gitlab.com/dave_m/clamtk/-/wikis/ClamTk-Hashes)
```

dpkg-sig --verify clamtk_6.13-1_all.deb clamtk_6.13-1_amd64.changes
Processing clamtk_6.13-1_all.deb...
NOSIG

```

As such, I'm concerned about the integrity of the package I installed, although I realize I may just be making a mistake or the instructions are lacking in verifying the .sig.

Is this something to be concerned about re system security?

Next time, I'll check the .sig **first** before installing from outside the repos.

---

### Post by KBar on 2021-11-20
As long as checksums match, you should be fine. Verifying keys and signatures is just extra, but you don't have to check them as an ordinary end-user. This is also mentioned in the instructions:
> No gpg key is necessary for checking the hashes.

---

### Post by ActionParsnip on 2021-11-20
You could contact the maintainer to let him know his signature is off (do retry the download to make sure you have a good file). You could even use clamav in command line to scan the file first

---

### Post by monkeybrain20122 on 2021-11-20
Or you can just forget about it. You don't need antivirus on Linux, moreover clamtk scans for Windows virus and is crappy to boot.

---

### Post by ActionParsnip on 2021-11-20
> **monkeybrain20122 said:**
> Or you can just forget about it. You don't need antivirus on Linux, moreover clamtk scans for Windows virus and is crappy to boot.

You don't know the use case here so can't actually say. The user may have a file share with Windows clients. Having antivirus running will help protect the Windows systems from each other. The system may also be an email server.... Wouldn't you want yscan email as it comes in? I certainly would... And do! You cannot say what a user does or doesn't need until you know about the system and what it is used for. Presently, all you know is that the person wants to install a GUI application to scan files and so forth for viruses... Unless you have had previous interactions with the user and are familiar....

---

### Post by thefrenchchef on 2021-11-20
Thanks for the replies.

My reason for opening this thread is  concerns about security of my system given the .deb I already installed does did not seem signed. The sha256 matched a fresh download, and  clamav and virustotal had no problems with the file. I will contact the  maintainer, who seems to be in the process of a new release as we speak (EDIT: there 6.14 version does have a GOODSIG, however I must be running the commands fine).

> **ActionParsnip said:**
> You don't know the use case here so can't actually say. The user may have a file share with Windows clients. Having antivirus running will help protect the Windows systems from each other. The system may also be an email server.... Wouldn't you want yscan email as it comes in? I certainly would... And do! You cannot say what a user does or doesn't need until you know about the system and what it is used for. Presently, all you know is that the person wants to install a GUI application to scan files and so forth for viruses... Unless you have had previous interactions with the user and are familiar....

I am running clamav mainly for compliance, but I also share files with Windows boxes. My understanding of clamav is that it does check for some Linux malware/viruses/etc., however obscure. I haven't checked in depth (aka which particular ones and when they were added to the definitions), so I stand to be corrected. Of course, it is also another additional surface.

I did install via the software centre, and I have a follow up. Are mandatory access control (apparmor) profiles configured via the software centre for .debs not from the repos? For example, a default one that is conservative.

---

### Post by monkeybrain20122 on 2021-11-20
> **ActionParsnip said:**
> You don't know the use case here so can't actually say. The user may have a file share with Windows clients. Having antivirus running will help protect the Windows systems from each other. The system may also be an email server.... Wouldn't you want yscan email as it comes in? I certainly would... And do! You cannot say what a user does or doesn't need until you know about the system and what it is used for. Presently, all you know is that the person wants to install a GUI application to scan files and so forth for viruses... Unless you have had previous interactions with the user and are familiar....

Well shouldn't Windows clients take care of their own security? There are tons of antivrus apps on Windows and better than clamtk. If they don't know how to or don't care then they are exposed to a lot more risks than from OP. why should Linux users be babysitting Windows users?

---

### Post by ActionParsnip on 2021-11-20
Yes but it all helps. I work with Linux and deploy Symantec Endpoint Protection to all systems. It's just good practice

---

