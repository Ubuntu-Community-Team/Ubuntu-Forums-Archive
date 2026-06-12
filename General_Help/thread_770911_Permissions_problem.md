---
title: "Permissions problem"
date: 2008-04-27
forum: General Help
---

### Post by Kakteed on 2008-04-27
First, let me say that I am a *very* new Ubuntu user, and have previously only used Windows XP, and Macs at work. So please forgive my ignorance; I'm trying as hard as I can to learn how this works.

So the problem I'm having is that for whatever reason my Desktop has decided that I don't have the right permissions to delete things from it, or save things to it. It says "cannot move /home/[username]/[file] because you do not have permissions to change it or its parent folder". I tried using 'sudo chown [username] /home' in the terminal, but it didn't fix the permissions.

I have no idea what I'm doing wrong, and I would *love* to be able to save things to my desktop again.

I am using Ubuntu Gutsy.

---

### Post by fullmetalgerbil on 2008-04-27
Sorry I can't be more helpful, but for what its worth I'm having the same problem with Hardy Heron.

---

### Post by Kakteed on 2008-04-27
I'm relieved to know that it's not just me; I thought I had done something absolutely stupid (which I still may have -- urgg).

---

### Post by MaindotC on 2008-04-27
One quick solution is to launch Nautilus with root permissions.  In a command prompt, type:

```

sudo nautilus&

```

The & sign will allow you to keep using the command prompt while Nautilus is open.

---

### Post by fullmetalgerbil on 2008-04-27
Don't worry, its not you. I never had that problem with Gutsy, however when I posted here about the same problem with Hardy (however, I could still save files just not delette them) I got very little help. 
Usually though, any hitches will be quickly addresssed here. Ubuntu has awesome community support. You might also want to try the Ubuntu forum at [http://linuxquestions.org]("http://linuxquestions.org").
:)Don't sweat being new to this, I only came onboard five months ago and everybody here has been quite patient with me.

---

### Post by Kakteed on 2008-04-27
I put that into terminal (which I assume is the command prompt? Gosh, I feel stupid) and got this:

[1] 5990
[username]@[computer]:~$ [sudo] password for [username]:

except it did not give me a chance to enter my password, and I still cannot modify files on my desktop.

What did I do wrong?

---

### Post by knutschr on 2008-04-27
You won't see that you type.
Just type it and press [Enter].

Btw. I think you should rather type
gksu instead of sudo when you opens a GUI program as root.

---

### Post by Kakteed on 2008-04-27
If I use gksu instead of sudo, it opens up the root's desktop/home .. can I navigate through to my own files? I am not on the root user account.

---

### Post by MaindotC on 2008-04-27
Yeah - navigate to /home/<username> folder.

---

### Post by Kakteed on 2008-04-27
Thank you! I'm sorry for having so many questions -- I wish that I knew more.

Also, I hope that there is some way to fix this so that I don't have to do this to be able to modify files, but I'm very glad to at least be able to modify them.

Thanks! :)

---

### Post by MaindotC on 2008-04-27
> **Kakteed said:**
> Thank you! I'm sorry for having so many questions -- I wish that I knew more.

Also, I hope that there is some way to fix this so that I don't have to do this to be able to modify files, but I'm very glad to at least be able to modify them.

Thanks! :)

You could try going to System -> Administration -> Users And Groups, selecting your user name, and then selecting the "Permissions" tab and seeing what is and is not enabled.

---

### Post by Kakteed on 2008-04-29
The only things I do not have permission to do are "allow use of fuse filesystems", "send and receive taxes", and "use tape drives". I don't think that would matter-?

Also, if I am not being clear, it is just my desktop that is not letting me modify files. If the files are in my home folder or a subfolder of that, I can modify them just fine.

---

### Post by knutschr on 2008-04-29
> **Kakteed said:**
> 
Also, if I am not being clear, it is just my desktop that is not letting me modify files. If the files are in my home folder or a subfolder of that, I can modify them just fine.
If I understand you right, it is all perfectly as it should be!
In Linux only root can modify files not being in a user's home folder.
In Ubuntu that is done by switching to root for special tasks like you just did.
After using Linux for some time I am sure you will appreciate this permission politics :-)

---

### Post by Nunu on 2008-04-29
> **Kakteed said:**
> Thank you! I'm sorry for having so many questions -- I wish that I knew more.

Also, I hope that there is some way to fix this so that I don't have to do this to be able to modify files, but I'm very glad to at least be able to modify them.

Thanks! :)

Hang in there buddy, it takes time to find your feet in this new world but once your there you will never want to go back.

---

### Post by MaindotC on 2008-04-29
You know what I can't believe this totally flew right over my head.  Dude, if you're trying to modify files via command line, just precede each command with "sudo".  If you're trying to do it in nautilus you'll have to launch nautilus as I specified earlier.  Give me a star please.

---

### Post by Nunu on 2008-04-29
> **strAlan said:**
> You know what I can't believe this totally flew right over my head.  Dude, if you're trying to modify files via command line, just precede each command with "sudo".  If you're trying to do it in nautilus you'll have to launch nautilus as I specified earlier.  Give me a star please.

:KS

Here you go :D

---

### Post by knutschr on 2008-04-29
> **strAlan said:**
> if you're trying to modify files via command line, just precede each command with "sudo".  If you're trying to do it in nautilus you'll have to launch nautilus as I specified earlier.  Give me a star please.
Use 'sudo' and 'gksu' only when you have to.
You can modify all files in your home directory from command line without using 'sudo'.
We come all from Windows, I think, being used to that OS, and were once confused by these 'root' and 'permission' problems, untill we, after some time understood that 'the Linux way' is far better.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Nunu on 2008-04-29
It adds more security to your system. Nothing can be installed without your permission which makes it very close to a hardened OS. something only seen in hi tech security devices like Iron Port. 

So at the moment it might be something to get use to one day you will thank it.

---

### Post by Kakteed on 2008-04-30
I'm sorry, I am not being clear. I mean 'Desktop' as in the Desktop directory in my Home folder. It has listed as the owner '671' and I am '1001'. This is why I can't modify it? How do I change the owner? With chown?

Thank you very much for all your help, and I can certainly use your advice to modify files, I just would like to be able to modify files on my own desktop 'normally'. Of course it is fine to do it the way you've shown me, it is just that then I cannot save files directly to the Desktop if I am downloading them and this is annoying.

---

### Post by knutschr on 2008-05-01
> **Kakteed said:**
>  How do I change the owner? With chown?

Yes, you do:
```
sudo chown [name] /home/[name]/Desktop
```
Check also that you have write permission to the directory.

---

