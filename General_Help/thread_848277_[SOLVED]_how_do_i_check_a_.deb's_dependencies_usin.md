---
title: "[SOLVED] how do i check a .deb's dependencies using terminal?"
date: 2008-07-03
forum: General Help
---

### Post by bluepowder7 on 2008-07-03
[color=blue]**(for the impatient ones, just skip to the very last paragraph)**[/color]

so, in my XMMS saga, i found the .deb package for it.  and since i'm forcing myself to learn as much about the CLI as possible, i hopped into the terminal and punched in

```

sudo dpkg -i xmms.whatever.deb

```

up until that point, i had always and only used the sudo aptitude install method to load up new software (never apt-get, never synaptic).  i'm weird that way. :)

anyhoo, the installer came back and told me that there were 3 unmet dependencies, and it aborted the install.  when i went to manually

```

sudo aptitude install <first-missing-dependency-package>

```

it came back and said XMMS is broken, and to resolve this it would need to remove XMMS (i'm ok with that) as well as Streamtuner (whoa!  um, no!  please leave that alone...)

what i did in order to install the dependencies cleanly was

```

sudo dpkg --purge xmms

```

and then one by one

```

sudo aptitude install <first-missing-dependency-package>

```

which installed them cleanly with no complaints and no removing of other stuff.  after that, i once again ran

```

sudo dpkg -i xmms.whatever.deb

```

which worked perfectly fine, did the install, yada yada yada.

SO, having said ALL of that - is there a way i can have the system check the dependencies and tell me which ones are not satisfied and stop there?  i mean, don't even TRY to install the .deb, just tell me what i'm missing so that i can skip the --purge step and install the missing pieces myself.

thanks for any advice, and sorry for the long-winded post!

---

### Post by sdennie on 2008-07-03
1) If you install a .deb file and it's missing dependencies, you can usually use apt-get to resolve them for you.  After you got your first unmet dependency error message, you should be able to do:

```

sudo apt-get install -f

```

Which will download everything you need to fix the dependency problems.

2) You can do a dry run before installing from a .deb with:

```

sudo dpkg -i --dry-run name_of_package.deb

```

---

### Post by bluepowder7 on 2008-07-03
2) ok, that dry-run seems like it would do just what i need!  sweet!  gonna do that next time.

1) so, if i forget to do a dry-run and jump right to **sudo dpkg -i whatever.deb**, and it spits out that i've got dependencies missing, do i then run **sudo aptitude install -f**, and that's it?  or after it's finished do i need to run **sudo dpkg -i whatever.deb** again?

---

### Post by shae on 2008-07-03
After running that apt-get command you are good to go, you should not need to reinstall the package.

---

### Post by bluepowder7 on 2008-07-03
cool, thanks!  solved!

---

