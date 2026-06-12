---
title: "Giving a user access to run a program from command line?"
date: 2007-06-19
forum: General Help
---

### Post by squinter on 2007-06-19
Hi,

what is the command line to give a user access to run a program? For example I just logged in as root and installed lynx, how do I give user1 the permission to use it?

Cheers

---

### Post by dreadlord_chris on 2007-06-19
> **squinter said:**
> Hi,

what is the command line to give a user access to run a program? For example I just logged in as root and installed lynx, how do I give user1 the permission to use it?

Cheers

Actually, unless you installed the app into **root's** $HOME, users should already be able to use it.
Otherwise, if it really is a privilages issue:
```

chmod o+x /location/of/lynx

```
That turns on the eXecute bit for *others*
You'll either need to already be root or sudo that chmod, though.

---

### Post by kevinlyfellow on 2007-06-19
All users should be able to use it by default.  Is that not the case?

For info on file permission (such as the permission to execute a file) you can refer here [http://www.linuxforums.org/security/file_permissions.html](http://www.linuxforums.org/security/file_permissions.html) or google something like linux file permissions.

---

### Post by squinter on 2007-06-19
Hmm, yes you are right, I installed lynx using root, but other users can use it too. I must have confused myself with file access. :confused:

---

### Post by Qu4k3R on 2007-06-19
You want to **root access** the program file (giving to it permissions to change your whole OS)  or just **access** the file?

---

### Post by squinter on 2007-06-21
No, I installed lynx as root, then I was trying to use it when logged in as normal user, and I thought I was having problem, but apparently not. I must have confused myself with something else.

---

### Post by puckstopper9 on 2007-06-28
I actually am having a similar problem, and hopefully this is not off-topic. I have installed programs and plug-ins under my account, which has full access rights; however, my father's account, which is restricted, does not have these programs and/or plug-ins available. As on example, I installed the Flash plug-in for Firefox, but when he logs in and uses Firefox, he cannot see any flash apps embedded on websites. How would I push the install to his account without giving him install rights?

---

### Post by kevinlyfellow on 2007-06-29
> **puckstopper9 said:**
> I actually am having a similar problem, and hopefully this is not off-topic. I have installed programs and plug-ins under my account, which has full access rights; however, my father's account, which is restricted, does not have these programs and/or plug-ins available. As on example, I installed the Flash plug-in for Firefox, but when he logs in and uses Firefox, he cannot see any flash apps embedded on websites. How would I push the install to his account without giving him install rights?

Make sure that all users can read the plugins in both /usr/lib/flashplugin-nonfree and its links in /usr/lib/firefox/plugins.  I'm under the assumption that you installed flash through synaptic or apt.

---

### Post by puckstopper9 on 2007-06-29
Thank you for replying so quickly! I checked both locations, and the flashplugin-nonfree is empty (checked for hidden files). The Firefox plugins folder only has a linuxprintplugin.so. I had originally installed it through just Add/Remove under Applications, but just now, I went through synaptic and reinstalled, and nothing new showed up under either folder. This is when I'm viewing while logged in under my account, so it's weird that it's working for me, but there's nothing being displayed in either of the folders.

---

### Post by limbourg31 on 2007-06-29
squinter, search through your file manager for a lynx binary, it should be in /usr/bin or /bin and then do a sudo chmod in the terminal to that binary

---

### Post by kevinlyfellow on 2007-06-29
> **puckstopper9 said:**
> Thank you for replying so quickly! I checked both locations, and the flashplugin-nonfree is empty (checked for hidden files). The Firefox plugins folder only has a linuxprintplugin.so. I had originally installed it through just Add/Remove under Applications, but just now, I went through synaptic and reinstalled, and nothing new showed up under either folder. This is when I'm viewing while logged in under my account, so it's weird that it's working for me, but there's nothing being displayed in either of the folders.

I think (not sure) that there is now a way to have local firefox plugins.  I may have installed mine through a different repository (therefor may act differently).  Maybe we can find the files
```
locate  libflashplayer.so flashplayer.xpt
```

If you do find them, link them in /usr/lib/firefox/plugins (warning, not a copy and paste command)
```
sudo ln -s /flash/plugin/directory/here/pluginname /usr/lib/firefox/plugins/pluginname
```

After that we may need to set the permissions
```
sudo chmod 744 /usr/lib/firefox/plugins/*flash*
```

Edit: Just out of curiosity, are you a hockey goalie?

---

