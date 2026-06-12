---
title: "Shell Scripting Strings  and Password Manipulation"
date: 2008-07-06
forum: General Help
---

### Post by idipous on 2008-07-06
Hello to all,

I have a couple of questions.

I have written a shell script that requires to excecute a
```

sudo make install
``` 

and I do not want it to prompt for a password as I intend to make it execute automatically at boot time. How is this done?

The second question this: In the same script I want to automate the unistallation of older kernels so as to have only the last two installed. 

```
CURRENT_KERNEL="`uname -r | awk '{print $1}' `"
echo $CURRENT_KERNEL
OLD_KERNELS="`ls /boot/ | grep vmlinuz*`"
echo $OLD_KERNELS
```

I cannot figure out how to manipulate the strings so as to have identify the older kernels and keep the last two.

Essentially what I need is to compare the values stored in the two variables and identify the newest two kernels.

Thanks in advance
idipous

---

### Post by kuja on 2008-07-06
With regards to the first, if that script is going to exec automatically at boot up, it should execute with root privileges so sudo shouldn't be necessary. Just put it in /etc/init.d and run ```
sudo update-rc.d {thescriptname} defaults
```

---

### Post by idipous on 2008-07-31
Thank you for your reply. I will try this and report back with results.

---

### Post by geirha on 2008-07-31
Let's make a one-liner, step by step

```
aptitude search ^linux-image
```

Lists all packages starting with linux-image. This includes packages like linux-image-386 which we don't want to match

```
aptitude search ^linux-image-[0-9]+\.[0-9]+\.[0-9]+.*$
```

This only lists actual kernel-packages

```
aptitude -F "%p" search ~i^linux-image-[0-9]+\.[0-9]+\.[0-9]+.*$
```

The added ~i will limit the search to only installed packages, and -F "%p" changes the output format to only display the package name.

```
aptitude -F "%p" search ~i^linux-image-[0-9]+\.[0-9]+\.[0-9]+.*$ | sort -r
```

Now we sorted them in reverse order, of which the top two are the ones we want to keep. 

```
aptitude -F "%p" search ~i^linux-image-[0-9]+\.[0-9]+\.[0-9]+.*$ | sort -r | awk '(NR > 2) {print $1}'
```

This awk basically says, when the line count (NR) is greater than 2, start printing. Effectively this removes the two kernels we want to keep, leaving us with the kernels we want to remove. Let's pass them on to aptitude remove

```
aptitude -F "%p" search ~i^linux-image-[0-9]+\.[0-9]+\.[0-9]+.*$ | sort -r | awk '(NR > 2) {print $1}' | xargs -r sudo aptitude -s -y remove
```

xargs passes the input as arguments to the following command. With the -r switch it will not run the command if the input is empty (i.e. nothing to remove). The -s option to aptitude means simulation. It will not remove anything, just print out what will be done. Obviosly the -s should be removed when you're satisfied it does what it should. The -y assumes yes to all questions.

---

### Post by kuja on 2008-07-31
Which reminds me ... I've got another one liner that I used the other day ... mine only keeps one though (but if that one is working it should be fine) - mine takes out the linux-headers, l-r-m and such too though.  ```
sudo apt-get remove $(dpkg --list | grep ^ii.* | grep .*-2.6\..*-.*-generic.* | grep --invert .*$(uname -r).* | cut -d ' ' -f 3 | tr '\n' ' ')
```

---

### Post by idipous on 2008-08-01
Thank you a lot for your answers. They are really helpfull and helped me a lot to learn a couple of things I searched for a long time.

Cheers!!!

---

