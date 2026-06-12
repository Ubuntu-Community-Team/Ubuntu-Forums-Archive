---
title: "Can't get bash script to output utf-8 characters"
date: 2016-05-14
forum: General Help
---

### Post by senhorarca on 2016-05-14
[FONT=arial]Hi, I'm new to Ubuntu and Linux and I'm running a minimal installation of Ubuntu 16.04. I'm having trouble running some software that uses bash script and according to the developer this is probably because of utf-8 not being fully enabled. 

For the software to work it needs to be able to print special characters with echo, however, if I do these commands:

[/FONT][FONT=arial]echo -e '\xe2\x82\xac'will print out \xe2\x82\xac

sudo echo -e '\xe2\x82\xac' will print out &#8364;[/FONT][FONT=arial]

So apparently it works for my root user, but not for my non-root user. The problem is I am running this software as my non-root user.

I have been going through the usual solutions 

[/FONT][FONT=arial]In ~/.profile or ~/.bash_profile I have already set the following:

export LANG=en_US.UTF-8
export LOCALE=UTF-8

And the output of "locale", as well as of "sudo locale" is the same:

```
LANG=en_US.UTF-8
LANGUAGE=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=en_US.UTF-8
```

And it's weird, because it seems that it understands UTF-8, as if I do:

 "echo -n &#8364; | hexdump" it will output the hex code. But the opposite doesn't 
work (I tried with both echo and printf).

How is it possible that it only works with sudo and how could I possibly fix this?
[/FONT]

---

### Post by Impavidus on 2016-05-14
I'm guessing here...

Usually echo is a shell build-in. When you run echo, the executable in /bin/echo is not called, but the shell handles the command internally, which is more efficient. When you use sudo echo, the shell build-in is not used and the executable /bin/echo is used. And it now seems that /bin/echo correctly handles the -e option, whereas the build-in does not. A few commands to check it:```
# Which shell do you use?
echo $SHELL

# Is echo a build-in?
type echo

# What are the accepted options for the build-in echo?
help echo

# What are the accepted options for /bin/echo?
/bin/echo --help
```

---

### Post by steeldriver on 2016-05-14
^^^ +1

Specifically, with dash as /bin/sh

```

$ readlink -f $(which sh)
/bin/dash

```
then
```

$ sh -c '/bin/echo -e "\xe2\x82\xac"'
€

```
but
```

$ sh -c 'echo -e "\xe2\x82\xac"'
-e \xe2\x82\xac

```

---

### Post by Impavidus on 2016-05-14
And as you stated that this is in a script, I guess that the script begins with the line```
#!/bin/sh
```This will run the script using the shell /bin/sh, which on a default Ubuntu system is a symlink to /bin/dash. In other words, the script designed as a bash script fails to indicate this to the system and is interpreted as a dash script instead. Changing the first line to```
#!/bin/bash
```may fix the issue.

**Background:** /bin/sh can be assumed to be present on all UNIX-like systems, so when writing shell scripts /bin/sh is a safe bet as the script can be interpreted on every system. It is known as the [Bourne shell]("https://en.wikipedia.org/wiki/Bourne_shell"). Of course, this only works if the script is indeed compatible with the Bourne shell. Many systems no longer have the original Bourne shell, but have replaced it with a [backward compatible]("https://en.wikipedia.org/wiki/Backward_compatibility") replacement like [bash]("https://en.wikipedia.org/wiki/Bash_%28Unix_shell%29") or, on Ubuntu, [dash]("https://en.wikipedia.org/wiki/Almquist_shell"). The author of your script may have made the false assumption that on your system /bin/sh is a symlink to /bin/bash, where he should have stated explicitly that the script is designed for the bash shell.

---

