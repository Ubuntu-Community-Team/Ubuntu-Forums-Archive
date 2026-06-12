---
title: "Have any script does a command when a software loaded ?"
date: 2021-11-11
forum: General Help
---

### Post by aug7744 on 2021-11-11
I want change cpu power profile when a software is loaded in OS memory and return to previous cpu power profile when the same software was unloaded in OS memory.
A script does command when a software is loaded ?

Thanks for reply.

---

### Post by Impavidus on 2021-11-11
I would use a wrapper around that software. The wrapper first changes your settings, then starts the software, waits for the software to terminate and finally restores the settings. If you want to be able to run multiple instances at the same time, add a counter and a lock so that only one instance at a time can check and update the counter.

You could also use a script that checks for the presence of a particular process and run that script every minute, but that's a bit wasteful and slow.

---

### Post by ActionParsnip on 2021-11-11
Sure. If you can find the BASH command to do it then make a script
```

command to change CPU power profile
comamnd you want to run
command to change CPU power profile back

```

Each command waits for the previous to finish so once you close the command you want to run then the CPU power profile will be set back.

Seems a bit excessive though and the kernel will assign more CPU to applications that need it. You could just set a lower nice value to the application to make the CPU scheduler give more time to the process you like. There isn't much detail about the exact process so I cannot give more granular advice, personally

---

### Post by aug7744 on 2021-11-12
Where see information about how create a wrapper or script ? What lines to add in script ?

---

### Post by TheFu on 2021-11-12
> **aug7744 said:**
> Where see information about how create a wrapper or script ? What lines to add in script ?

A script is just commands that you'd type into a terminal window, but put inside a file.  Then **chmod u+x filename** and you have a basic script.
There are millions of example bash scripts on the internet. Millions.
There are lots of how-to bash script guides on the internet. Thousands.

Most of the programs on your computer are located in /usr/bin/ or /bin/ or /sbin/ or /usr/sbin/ directories.  Each of those programs does something different AND they have a manpage for how to use them for the exact version installed on your system. The manpage for each is on your system  IF you will be scripting, you'll need to read the manpages. Sorry.  There's no way to skip that.

If you want to browse manpages, use the **xman** command.  There are more efficient methods, but start there.

This is a 4-line script, so you should be able to figure it out for your needs specific to your CPU and your version of the OS.  I honestly don't know the commands. If it was me, I'd use **nice** to prevent a long running command taking priority of the CPU.  nice has a manpage, BTW.  But this isn't the question you asked, so ... you'll have to look for that yourself.

---

