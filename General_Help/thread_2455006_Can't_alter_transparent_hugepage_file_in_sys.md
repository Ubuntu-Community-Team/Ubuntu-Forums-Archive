---
title: "Can't alter transparent_hugepage file in sys"
date: 2020-12-10
forum: General Help
---

### Post by FlintL on 2020-12-10
Redis asks that you disable transparent huge pages. It gives the following command to do so:
```
echo never > /sys/kernel/mm/transparent_hugepage/enabled
```

I ran this and got permission denied. Then I did

```
echo "never" | sudo tee /sys/kernel/mm/transparent_hugepage/enabled
```

And check the file, and it was not altered.

The redis command uses '>', so I think it wants to replace the entire file (I am new to unix commands), which is why I did not use the -a (append) flag with tee.

How can I accomplish the command redis is asking me to do? 
```
echo never > /sys/kernel/mm/transparent_hugepage/enabled
```

---

### Post by SeijiSensei on 2020-12-10
You can only write to /sys as root.  Run the command with sudo.

```
sudo echo never > /sys/kernel/mm/transparent_hugepage/enabled
```

That said, I believe /sys is rebuilt on every reboot so the command won't persist. You could add the command to /etc/rc.local (without sudo as it runs as root) which is run at the end of the bootup process. Recent versions of Ubuntu no longer seem to have an /etc/rc.local file so you may have to create it yourself.  Again you'll need to be root (via sudo) to do this.

---

### Post by Doug S on 2020-12-10
> **SeijiSensei said:**
> You can only write to /sys as root.  Run the command with sudo.

```
sudo echo never > /sys/kernel/mm/transparent_hugepage/enabled
```


Actually, that command will not work, because the redirection portion ends up without elevated privileges:

```
doug@s18:~/test_kernels$ sudo echo never > /sys/kernel/mm/transparent_hugepage/enabled
-bash: /sys/kernel/mm/transparent_hugepage/enabled: Permission denied
```

the second command listed by the OP should have worked, but maybe didn't because it was quoted or something:

```
doug@s18:~/test_kernels$ ls -l /sys/kernel/mm/transparent_hugepage/enabled
[COLOR="#FF0000"]-rw-r--r--[/COLOR] 1 root root 4096 Dec 10 07:48 /sys/kernel/mm/transparent_hugepage/enabled
doug@s18:~/test_kernels$ cat /sys/kernel/mm/transparent_hugepage/enabled
always [COLOR="#FF0000"][madvise][/COLOR] never
doug@s18:~/test_kernels$ [COLOR="#FF0000"]echo never | sudo tee /sys/kernel/mm/transparent_hugepage/enabled[/COLOR]
never
doug@s18:~/test_kernels$ cat /sys/kernel/mm/transparent_hugepage/enabled
always madvise [COLOR="#FF0000"][never][/COLOR]
doug@s18:~/test_kernels$ echo madvise | sudo tee /sys/kernel/mm/transparent_hugepage/enabled
madvise
doug@s18:~/test_kernels$ cat /sys/kernel/mm/transparent_hugepage/enabled
always [COLOR="#FF0000"][madvise][/COLOR] never
```

I suppose I could try exactly the way the OP did:

```
doug@s18:~/test_kernels$ [COLOR="#FF0000"]echo "never" | sudo tee /sys/kernel/mm/transparent_hugepage/enabled[/COLOR]
never
doug@s18:~/test_kernels$ cat /sys/kernel/mm/transparent_hugepage/enabled
always madvise [never]

```Hmmm... works for me. OP are your read/write permissions the same as mine (highlighted in red above)? And, does it list "never" as an option?

Note: tested on kernels 4.4.0-179-generic and 5.10.0-rc6 (devleopement kernel).

---

### Post by SeijiSensei on 2020-12-10
Sorry, I forgot that the redirection would not have sudo privileges and that tee is needed.

---

### Post by FlintL on 2020-12-11
Thanks for the help from both of you!

I made the mistake of not looking at the file contents before running the command, so it is possible the command worked! Sorry.

But I thought it didn't work because I read that the tee command, when using >, should overwrite the file entirely, meaning it should only have the contents

```
never
```

not

```
always madvise [never]
```

Unless the something is automatically writing the "always madvise" part and adding the brackets?

I am also running Ubuntu 20.04.1 LTS.

---

### Post by Impavidus on 2020-12-11
> **FlintL said:**
> 
Unless the something is automatically writing the "always madvise" part and adding the brackets?


It is. /sys is not a real filesystem; it's a pseudo-filesystem. It allows you to communicate with the running kernel.

---

### Post by FlintL on 2020-12-12
> **Impavidus said:**
> It is. /sys is not a real filesystem; it's a pseudo-filesystem. It allows you to communicate with the running kernel.

I had no idea! Is there a place that lists the pseudo-file systems so I can predict this behavior in the future? Or is it just /sys?

---

### Post by Impavidus on 2020-12-13
/sys and /proc mostly. /dev isn't entirely real either. You can read about them on Wikipedia.

---

### Post by SeijiSensei on 2020-12-13
I don't think /run is persistent either since it uses tmpfs.

---

