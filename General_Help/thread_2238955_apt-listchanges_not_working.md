---
title: "apt-listchanges not working"
date: 2014-08-11
forum: General Help
---

### Post by project722 on 2014-08-11
trying to figure out what I am doing wrong using this command. MAN says the correct usage is this:

apt-listchanges [options] {--apt | package.deb}

So as a test I used apt-listchanges -c --apt | "packagename"

and I got this: 

[4]+  Stopped                 sudo apt-listchanges -c --apt | "packagename"

tried sudo'ing - no luck. tried with and without the .deb on the end of "packagename". in my case "packagename" = the name of the package w/out the quotes in the command.

---

### Post by steeldriver on 2014-08-11
The syntax 

```

{--apt | package.deb}

```

means **either** -apt **or** package.deb

You probably need something like

```

apt-listchanges -c /path/to/packagefile.deb

```

e.g.

```

apt-listchanges -c ~/Downloads/apt-listchanges_2.85.8ubuntu2_all.deb

```

---

### Post by project722 on 2014-08-11
Ok I don't think this is going to work for me, the man pages say:

 **apt-listchanges** is a tool to show  what  has  been  changed  in  a  new
       version  of  a  Debian  package,  as  compared to the version currently
       installed on the system.

What I am wanting to do is see the changelog for a package currently installed without doing any comparison. Just for kicks I went into /usr/share/doc/yum and found a "changelog.debian.gz" file but I am not sure if the tool was designed to look through a gz file. I ran the command against it but it failed.

---

### Post by steeldriver on 2014-08-11
You should be able to view the changelog.gz directly using 'less'

```

less /usr/share/doc/yum/changelog.debian.gz

```

The 'less' program *should* decompress the file automatically - if for some reason it doesn't, you can use

```

gzip -dc /usr/share/doc/yum/changelog.debian.gz | less

```

If you want to search for particular text you can either do so in 'less' or use zgrep

---

### Post by project722 on 2014-08-11
Well that was easy! Thanks we can close this one out :)

---

