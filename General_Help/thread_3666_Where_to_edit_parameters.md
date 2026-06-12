---
title: "Where to edit parameters?"
date: 2004-11-08
forum: General Help
---

### Post by MattOnTheNet on 2004-11-08
I feel totaly ashamed to ask, but then again, nobody knows my face in this virtual place!  Here goes nothing: once in while someone will reply with: "So you set "NoDoThisAndThat=False" then you'd change "SetVideoStuf=True", boot and all is working. But what file is refered to and where is it located?!

---

### Post by TravisNewman on 2004-11-08
That really all depends on the specific topic being discussed. Whenever in doubt, just ask "Hey what file are you talking about?" That's what the forum is for, to get your questions answered :)

---

### Post by sparkx on 2004-11-08
[QUOTE=MattOnTheNet]I feel totaly ashamed to ask, but then again, nobody knows my face in this virtual place!  Here goes nothing: once in while someone will reply with: "So you set "NoDoThisAndThat=False" then you'd change "SetVideoStuf=True", boot and all is working. But what file is refered to and where is it located?![/QUOTE]
 It is probably worth mentioning the man command here too. When you are wondering about a given issue in linux, it is always worth trying man(your thing) to see if there is a man page to help you out. 
For example: 

$man apache

there is a lot of information, such as where config files reside, inside of those man pages. hope it helps.

---

### Post by wallijonn on 2004-11-08
Here's a Linux primer:

[http://www.fortunecity.com/skyscraper/y2k/60/primer/primer.html](http://www.fortunecity.com/skyscraper/y2k/60/primer/primer.html)

One of my favourite sites:

[http://www.mozillaquest.com/indexes/Linux4Windows_index.html](http://www.mozillaquest.com/indexes/Linux4Windows_index.html) (Scroll down to article number 1, first).

---------------------------------------------------------------------------------------------------------------------------------------

The moderator has stated that he wants as complete instructions as possible, so it'll start to change. But even if we said ```
# ls
``` someone may ask if we are supposed to include the "#". I try to leave that out. I've started putting it outside the code box. 

What is harder to explain is why certain things are done - that is usually an individual personality, like making backups of config files before editing them. Then there are personal preferences with editors, some like pico, nano, VIM, emacs, etc. I try to use what is default in the Ubuntu distro and in the application menu. 

There are a lot of different levels of expertise here. I've probably forgotten more Unix than I know in Linux. I still use "cpy" instead of "cp", and if I am editing a file like /etc/apt/sources._list_ my mind reads /etc/apt/sources._lst_. Every distro is different and we have to learn the intricacies of each.  

Personally I hate MAN pages - it's so dry. It's what I would like to read in bed if I have insomnia. The only MAN pages I'd be presently interested in reading is on dpkg (Debian Package).

.

---

### Post by HungSquirrel on 2004-11-09
A good alternative to reading the "dry" man pages is the "--help" parameter.  While not available for all commands, it generally gives you a short and sweet synopsis of how to use a command.  I wish someone had told me about "--help" when I was a newbie.

For example:

```
$ ifup --help
Usage: ifup <options> <ifaces...>

Options:
        -h, --help              this help
        -V, --version           copyright and version information
        -a, --all               de/configure all interfaces marked "auto"
        -i, --interfaces FILE   use FILE for interface definitions
        -n, --no-act            print out what would happen, but don't do it
                                (note that this option doesn't disable mappings)        -v, --verbose           print out what would happen before doing it
        --no-mappings           don't run any mappings
        --force                 force de/configuration
```

---

