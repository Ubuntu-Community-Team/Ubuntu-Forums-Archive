---
title: "How can I find the packages I have manually installed?"
date: 2017-04-07
forum: General Help
---

### Post by Bobby_James on 2017-04-07
is there a way to find the names (and dates) of packages I have manually installed with apt install?

I do not mean the packages installed by default but ones the user has specifically installed?

Thanks!

---

### Post by vasa1 on 2017-04-07
See [https://ubuntuforums.org/showthread.php?t=2355157&p=13618570#post13618570](https://ubuntuforums.org/showthread.php?t=2355157&p=13618570#post13618570)

---

### Post by ajgreeny on 2017-04-07
It is very easy to see what has been installed, at least recently, and depending on how many log files are retained as .gz archive files in /var/log/ with command similar to```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
```
If you extract the logs in the dpkg.log.#.gz files you should be able grep them similarly to go back a long way, I think, and by using the time stamps of all the output lines from the grep command you can discard everything that was installed by the OS installer.

---

### Post by Habitual on 2017-04-07
```
sudo dpkg --get-selections 
```

---

### Post by Dennis N on 2017-04-07
> is there a way to find the names (and dates) of packages I have manually installed with apt install?

Yes, to find packages installed with "apt install" (but with no dates): 

```
dmn@Roxanne:~$ history | grep "apt install"
    1  sudo apt install mousepad libreoffice-writer geany
    2  sudo apt install libreoffice-gtk3
   19  sudo apt install gthumb
   24  sudo apt install apt-file
   31  sudo apt install gimp
   35  sudo apt install gparted
   53  sudo apt install tree

```

But, this is accurate only if you haven't outgrown the size of the bash history list - I think default is 2000 lines, but that can be changed by the user in .bashrc. The numbers in front are the history list line number of each command, so installing gimp was my 31st terminal command.

Alternate method:
If you want transaction dates, you need to search /var/log/apt/history.log (or /var/log/dpkg.log) as well as the archived copies in that same directory, for the package. Then you will see the transaction dates as well.

---

