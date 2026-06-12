---
title: "trying to install Chrome onto 64bit 17.04   but....   Help  !!!"
date: 2017-05-07
forum: General Help
---

### Post by Timmoore001 on 2017-05-07
Hi,

I get as far as the nice 'Install' button but nothing happens !

So I've tried various alternatives so I'm stuck...


Any thoughts anybody would be greatly appreciated !

[IMG]https://ubuntuforums.org/images/icons/icon4.png[/IMG]

Tim

---

### Post by howefield on 2017-05-07
Presumably you have downloaded the Chrome deb package and are trying to install it ?

Double clicking on the deb package should initiate the install process through the Ubuntu Software application but if that is not working as it should and you are not afraid of using hte terminal to install, please use the following command.

```
sudo apt install ~/Downloads/google-chrome-stable_current_amd64.deb
```

That command assumes that the package is in the ~/Downloads folder and is named google-chrome-stable_current_amd64.deb, if not then amend accordingly.

---

### Post by Timmoore001 on 2017-05-07
mega mega brillliant   !!!!    You are a hero !

That was quick and easy !

:  )))))

Tim

---

### Post by howefield on 2017-05-07
Cool, glad you got it.

Thanks for attempting to mark as solved, but better to use the "Thread tools > Mark this thread as solved.." option as it makes it easier for others searching the same thing.

---

### Post by vasa1 on 2017-05-07
Here's a wiki on how to mark your thread [SOLVED]: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

