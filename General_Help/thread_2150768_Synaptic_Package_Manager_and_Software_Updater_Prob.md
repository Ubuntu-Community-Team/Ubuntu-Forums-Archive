---
title: "Synaptic Package Manager and Software Updater Problem"
date: 2013-06-02
forum: General Help
---

### Post by alanr4 on 2013-06-02
I am currently using Lubuntu 12.10 and I received the following message when starting Synaptic Package Manager:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried running the command 'dpkg --configure -a' in LXTerminal, however LXTerminal freezes and then I have to use the Off button to restart my system.

I have also tried to use Software Updater but that also freezes when checking for updates and my system then freezes.

Update: After rebooting many times over two days using the Off button, a Software Updater message eventually appeared asking me to reboot my system to allow the updates to take effect. The problem now appears to have sorted itself.

---

### Post by ibjsb4 on 2013-06-02
Thats 

```
[COLOR=#ff0000]sudo[/COLOR] dpkg --configure -a
```

If its fixed, thats great.  Try checking it out in terminal with this command:

```
sudo apt-get update
```

Get any errors?

---

### Post by alanr4 on 2013-06-02
Many thanks for your advice, both these commands now work in LXTerminal.

---

### Post by ibjsb4 on 2013-06-02
Something that may interest you

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

And don't forget

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And welcome to the forums :)

---

