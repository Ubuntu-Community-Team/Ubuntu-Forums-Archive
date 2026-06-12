---
title: "Installed packages have unmet dependancies"
date: 2024-12-01
forum: General Help
---

### Post by chris-burmajster on 2024-12-01
Hello Everybody,

My software updater doesn't work. Instead, a red like a no entry sign has appeared in the top right hand corner with the text *E:Malformed entry 1 in sources file /etc/apt/sources.list.d/third-party.sources (URI parse), E:The list of sources could not be read.* What can I do about it, please? I've read about the previous thread which doesn't help in any way. I've tried the terminal with the commands and it comes to nothing. 

Chris

---

### Post by deadflowr on 2024-12-01
post back what 
```
cat /etc/apt/sources.list.d/third-party.sources 
```
shows.
It says the error relates to the URI.
?

---

### Post by grahammechanical on 2024-12-01
1Did the error message mention a particular third party source? Open Software and Updates>Other Software tab and disable the offending third party source. The Other Software tab will also list third party sources.

Regards

---

### Post by chris-burmajster on 2024-12-01
cat /etc/apt/sources.list.d/third-party.sources
Types: deb
URIs: cdrom:[Ubuntu 22.04.2 LTS _Jammy Jellyfish_ - Release amd64 (20230223)]/
Suites: jammy
Components: main restricted
 That's what I got from the terminal.

Chris

---

### Post by chris-burmajster on 2024-12-01
The error message was in full, opening the cache (E malformed entry 1 in sources file / etc/apt/sources.list.d.third-party.sources(URI parse), E:the list of sources could not be read.

Chris

---

### Post by deadflowr on 2024-12-01
You can delete the file
```
sudo rm /etc/apt/sources.list.d/third-party.sources
```

It has to do with the system thinks you want to use the installer ISO repo.
The installer has a couple packages included in a repo.
Like some wifi drivers (i think???) in case the installation doesn't install them properly.

---

### Post by chris-burmajster on 2024-12-02
Hello,

I can't remove it! The system won't let me.

Chris

---

### Post by chris-burmajster on 2024-12-02
Sorry, it was removed!

Thank you for all your help.

Chris

---

