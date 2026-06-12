---
title: "Help with basic rsync command"
date: 2016-03-01
forum: General Help
---

### Post by mehdi_azzad on 2016-03-01
A quick newbie question about a linus command.
I am trying to move the /home folder to 2nd HDD and little confused, the below command has two periods, (.), are these needed? Both after /home .

"sudo rsync -aXS --exclude='/*/.gvfs' /home/. /media/home/."

---

### Post by mcgess on 2016-03-01
Hi and welcome

I'm not an expert but I'm pretty sure the . are not needed and have no effect.
Does the command do what you are expecting, if not what does it do and how is that different to what you expect?

Try using the -nv options to perform a dry run (-n) with a verbose (-v) listing of the files that will be transferred while you work out the command you want.

```
sudo rsync -nvaXS --exclude='/*/.gvfs' /home/ /media/home/
```

Is your 2nd HDD mounted at /media/home? On my installation it would be /media/*yourusername*/home

Martin

---

### Post by SeijiSensei on 2016-03-01
Rsync can be fussy about how the local and remote directories are named.  I recommend reading the [man page]("http://linux.die.net/man/1/rsync") ("man rsync") which gives examples of the syntax.

---

### Post by kjohri on 2016-03-02
> ```
sudo rsync -aXS --exclude='/*/.gvfs' /home/. /media/home/.
```

Both the dots are superfluous. Possibly, whosoever wrote the command wanted to stress that only the contents of /home need to be copied and directory home should not be created at the destination. For instance if you write the command as,

```
sudo rsync -aXS --exclude='/*/.gvfs' /home /media/home
```

a home directory would be created under /media/home and all the contents of /home would be copied to /media/home/home. But if you put a slash at the end of SRC directory the contents of SRC  are copied to the destination directory and your command can be written as,

```
sudo rsync -aXS --exclude='/*/.gvfs' /home/ /media/home/
```

For more details, refer the link, [http://www.softprayog.in/tutorials/rsync]("http://www.softprayog.in/tutorials/rsync")

---

