---
title: "dash bashing"
date: 2006-12-14
forum: General Help
---

### Post by sefs on 2006-12-14
So the switch to dash has been causing me no end in grief.

So i finally gave in and did  the below.

```

rm -f /bin/sh
sudo ln -s /bin/bash /bin/sh 

```

Is this bad?  I am on Edgy.

---

### Post by chalex on 2006-12-14
> **sefs said:**
> So the switch to dash has been causing me no end in grief.
 Like what?
> 
So i finally gave in and did  the below.

```

rm -f /bin/sh
sudo ln -s /bin/bash /bin/sh 

```

Is this bad?  I am on Edgy.

The Bourne shell (sh) and the Bourne again shell (bash) are probably less similar than bash and dash (although I know nothing about dash).

---

### Post by sefs on 2006-12-14
well broken scripts preventing applications from starting

to name a few

parallels 
frostwire
custom scripts ect.

---

### Post by po0f on 2006-12-14
sefs,

A `[FONT="Courier New"]sudo dpkg-reconfigure dash[/FONT]` would have changed the symlinks for you.  Manually changing them like you did might lead to confusion when you go to change them back.  Some hapless user of these forums accidentally symlinked to a symlink that pointed to another symlink and was getting "too many symlink" errors or something of the like.  :)

I don't know if the "correct" way of changing Dash to Bash will fix your script errors though.

---

### Post by sefs on 2006-12-14
yes it did fix them perfectly.

I was just wondering if doing what i did was a step backward since edgy is supposed to be progressive and have moved to dash.

Thanks.

---

### Post by PilotJLR on 2006-12-14
I did the same thing as you, for similar reasons. So far, nothing bad as happened as a result. Bash is slightly slower than dash, but it's also pretty much universal.


> **sefs said:**
> yes it did fix them perfectly.

I was just wondering if doing what i did was a step backward since edgy is supposed to be progressive and have moved to dash.

Thanks.

---

