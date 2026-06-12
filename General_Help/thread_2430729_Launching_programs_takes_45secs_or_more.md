---
title: "Launching programs takes 45secs or more"
date: 2019-11-06
forum: General Help
---

### Post by ldurfee on 2019-11-06
Can anyone tell me how to eliminate these error messages:

```
NameError: global name EXTENSIONS is not defined
NameError: global name SEPARATOR is not defined
RuntimeError: object at 0x7f12805fb500 of type CopyPasteImagesMenuProvider is not initialized
```

Either they are causing the launch time problem OR the messages themselves (100's per hour) are clogging the message buffers. I would like to know how to eliminate the source of the message.

When I first login OR just after running *Ubuntu software updater* requests, everything works fast (as it should). However, after an hour or so, launching programs (any program: *Firefox*, *OpenOffice*, etc.) will take 45secs or longer.

Can anyone help?

[Acer Aspire 5 Laptop (model A515-51-50RR); Processor: Intel Core i5-7200U at 2.50GHz (8GB RAM; 1TB HDD); O/S: 64-bit Ubuntu 18.04 LTS]

---

### Post by Impavidus on 2019-11-07
Where do you get those messages?

---

### Post by dragonfly41 on 2019-11-07
I see that this question has been raised in a number of forums ([AskUbuntu]("https://askubuntu.com/questions/1186735/resolve-error-messages")   and  [others]("https://answers.launchpad.net/ubuntu/+question/682356")) and OP seems anxious to solve it.
I can only observe that this error stream might be python related - but that is a guess.
Do these symptoms persist if a new user account is created?

[Later edit] Try [i]("https://github.com/oguzhaninan/Stacer")[nstalling Stacer]("https://github.com/oguzhaninan/Stacer") to monitor your resources. You can inspect, for example, the services started at boot.
Or explore usage of memory.

[Yet later edit] [Others responding]("https://www.linuxquestions.org/questions/linux-software-2/problem-taking-45-secs-or-longer-to-launch-a-program-e-g-openoffice-qpdfview-gedit-etc-4175658086/") to this reported issue have suggested a clean start by installing a fresh Ubuntu. But you could try running a LiveUSB before that step. Or trying a new user profile as suggested earlier might yield some clues. Errors refer to Nautilus.  Nautilus python extensions?

---

