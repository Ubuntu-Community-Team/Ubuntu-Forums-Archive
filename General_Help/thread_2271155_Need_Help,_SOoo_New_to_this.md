---
title: "Need Help, SOoo New to this"
date: 2015-03-27
forum: General Help
---

### Post by theofficialkoolkidklub on 2015-03-27
Ok so i am just barely getting into Ubuntu because my computer broke from long ago, some things are the same from windows but i am extremly lost on the how to install with Sudo command, can anyone teach me?

---

### Post by slickymaster on 2015-03-27
Hey theofficialkoolkidklub, welcome to the forums.

Please check these two links:[URL="http://askubuntu.com/a/575161/344926"]
How to install software when you're a Windows user![/URL]
[Installing Software]("https://help.ubuntu.com/community/InstallingSoftware")

---

### Post by Bashing-om on 2015-03-27
theofficialkoolkidklub; Hi ! Welcome to the forum.

Great, you have an interest in linux, be aware the thought process and how things are done in Windows is not the way of linux.
This operating system is a different concept in all ways.

You want to install something in ubuntu, well, the 1st line of approach, and best for the new user is the ubuntu software repository. Thousands of packages ready built for you.
There are a number of ways to install onto your system these packages that are available in the software repository.
The GUI way is "Software Center", you asked about the 'sudo' way.
That entails the (C)ommand (L)line (I)interface. Not at all scary - just a linux-wide tool - to communicate with your system.

Some background, if using the CLI, you need to know or find out the package of interest:
```

apt-cache search <search_term>

```
in that listing you see the package of interest, and want to know more:
```

apt-cache show <package_name>

```

Yepper, that is the one you want to install. 
Install the package:
```

sudo apt-get install <package_name>

```

OH No; do not want it. Take it to the bit bucket
```

sudo apt-get remove <package_name>

``` which removes the package, but leaves the config files - in the event you re-install the package and like the configs you have made.
To completely remove the package and it's config files:
```

sudo apt-get purge <package_name>

```

That is a quick intro to installing software, there is a lot more to learn. This, does serve to get you started.

[INDENT][INDENT]package management
[INDENT][INDENT][INDENT]we are blessed that they developed it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

