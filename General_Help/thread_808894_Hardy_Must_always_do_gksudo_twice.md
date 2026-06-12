---
title: "Hardy: Must always do gksudo twice"
date: 2008-05-26
forum: General Help
---

### Post by Johnny K on 2008-05-26
I'm not so much concerned about my own particular issue as I am concerned about the bug status of this issue.

Has anyone else encountered a problem in Hardy Heron where you must launch a gksudo app twice before it works? For example, Synaptic, Update Manager, and Software Sources will not actually begin running unless I attempt to launch the program twice. The first time, an item appears in the taskbar which states "X is starting...", which then disappears. When I try to launch the program again, I am prompted for my password and the program starts normally.

Has anybody else had this problem?

---

### Post by sdennie on 2008-05-26
I had that problem when I configured the fingerprint reader to work for various authentications on my laptop.  Could that be your problem?

---

### Post by Johnny K on 2008-05-26
> **vor said:**
> I had that problem when I configured the fingerprint reader to work for various authentications on my laptop.  Could that be your problem?

No, I don't have a fingerprint reader so the cause must not be that. I only noticed this problem within the last few days. When did you first notice it?

---

### Post by drs305 on 2008-05-27
I have several shortcuts on my panel that invoke sudo commands and some of them have been requiring two attempts to get them started. It was irritating but I hadn't thought about it much until you mentioned it. Thanks for destroying what would have been a good night's sleep ;-)

No fingerprint reader here either...

---

### Post by sdennie on 2008-05-27
I just threw that out there as a possible cause.  If you aren't using a fingerprint reader, the only other thing I can think of would be to check the pam configs.  Have you changed anything in /etc/pam.d?  If so, I can PM the default files from a clean VM for Gutsy or Hardy if you can't remember how to revert your changes.

Of course, it could be a completely different problem...

---

### Post by Johnny K on 2008-05-27
> **vor said:**
> I just threw that out there as a possible cause.  If you aren't using a fingerprint reader, the only other thing I can think of would be to check the pam configs.  Have you changed anything in /etc/pam.d?  If so, I can PM the default files from a clean VM for Gutsy or Hardy if you can't remember how to revert your changes.

Of course, it could be a completely different problem...

I don't remember ever manually changing the pam.d file.

So, is it safe to say this bug has not yet been reported?

---

### Post by sdennie on 2008-05-27
Well, it may not be a bug but something you've installed that has changed something that semi-breaks gksudo.  One way to check that would be to run the following just after hitting a gksudo app and seeing nothing come up:

```

ps aux | grep gksudo

```

If you are seeing a gksudo running, I would check /var/log/dpkg.log and see if you can pinpoint what you installed around the time this problem started happening.

---

### Post by sjhilton on 2008-05-27
I have this problem too. It's intermittent and mostly a nuisance for update-manager where if you hit check for updates the administrator password dialog doesn't pop up (it appears in the task bar but then disappears). The only way I can get around it is by killing the process in system monitor. I thought I had solved it by fixing the 'sudo can't resolve host name' (this appears when you run sudo in a terminal window), but it's happening again for some reason.

I'll try the suggestion in the last post and report back.

---

### Post by Johnny K on 2008-05-27
> **vor said:**
> Well, it may not be a bug but something you've installed that has changed something that semi-breaks gksudo.  One way to check that would be to run the following just after hitting a gksudo app and seeing nothing come up:

```

ps aux | grep gksudo

```

Here is my result of the command you posted. I'm not familiar with ps, so I'm not quite sure what it means:
```
john      9178  0.0  0.0   5164   848 pts/0    S+   13:27   0:00 grep gksudo
```



> **sjhilton said:**
> I have this problem too. It's intermittent and mostly a nuisance for update-manager where if you hit check for updates the administrator password dialog doesn't pop up

I've been having the same problem with update manager, and am equally annoyed when it happens. A workaround is to (for now at least) do upgrades in terminal with the following command:
```
sudo apt-get upgrade
```

---

### Post by Johnny K on 2008-05-28
I submitted a bug report which can be found [here]("https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/235637").

If you would like to continue the discussion on this issue, it is probably best that you do so there. I would also appreciate if someone could change the status of this bug to "Confirmed".

Thanks!

---

### Post by Johnny K on 2008-05-29
I think I may have found a solution while reading [this thread]("http://ubuntuforums.org/showthread.php?t=729690").

I navigated to **System > Administration > Network** and clicked the **Hosts** tab. The second host in the list was the following:
```
127.0.1.1 | [computername].[networkname]
```

I removed the **.[networkname]** from that entry, and now I can launch gksu applications without a problem. I also no longer get the error "unable to resolve host" when doing sudo from terminal.

Before I post this update to the bug report, can anybody confirm that this solution works for you? Also, can you comment on whether or not you had modified network settings in the past? I know I had, and I have a feeling that the **.[networkname]** was one of my own misguided modifications.

---

### Post by gusdefrog on 2008-05-31
I had this bug as well.  I was bothered by having to start it twice, but then after I did a manual network setup to be able to use the internet from a hotel's free network, suddenly no gksu or gksudo prompts would come up at all.  I could still sudo things from the command line though.  Even though I went back to my usual settings of automatically detecting my home network, my prompts would not return.

Finally it is fixed, I edited my system > network > hosts so that the entry for 127.0.1.1 matched the name that was being listed by sudo: unable to resolve host xxx

---

