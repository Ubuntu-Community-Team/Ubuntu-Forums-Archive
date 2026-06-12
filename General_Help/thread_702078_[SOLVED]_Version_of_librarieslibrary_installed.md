---
title: "[SOLVED] Version of libraries/library installed"
date: 2008-02-19
forum: General Help
---

### Post by gillza on 2008-02-19
Hi 

Before I ask:

I did search and could not find anything related to my question or quite possibly I missed a thread where this was mentioned. If so please point me in the right direction because I'm sure that question like that must have been asked before. 

Question:

Is there a command that I could use to check for a version of library/libraries currently installed? Or maybe is there a way to display a list of all libraries installed? I know that I can look up the version using synaptic manager but I'm trying to avoid using it.

Thanks in advance.

---

### Post by gillza on 2008-02-20
Bump

---

### Post by happyhamster on 2008-02-20
- You can get a lot of information on packages using "apt-cache". For example:

apt-cache show packagename

- If you want some specific info, use grep to narrow it down:

apt-cache show packagename | grep version -i

- That line will only show the package version (grep searches for lines with "version" in them).

For more info:
[https://help.ubuntu.com/community/AptGetHowto](https://help.ubuntu.com/community/AptGetHowto)
[http://linux.die.net/man/8/apt-cache](http://linux.die.net/man/8/apt-cache)

- And this command will show what's installed (or waiting to be removed) on your system:

dpkg --get-selections

- It will be a huge list, so it's probably better to redirect the output into a text file:

dpkg --get-selections > filename.txt

---

### Post by gillza on 2008-02-20
Thank you very much! I'll try it as soon I get to my computer at home!

---

### Post by gillza on 2008-02-20
> **happyhamster said:**
> - You can get a lot of information on packages using "apt-cache". For example:

apt-cache show packagename

- If you want some specific info, use grep to narrow it down:

apt-cache show packagename | grep version -i

- That line will only show the package version (grep searches for lines with "version" in them).

For more info:
[https://help.ubuntu.com/community/AptGetHowto](https://help.ubuntu.com/community/AptGetHowto)
[http://linux.die.net/man/8/apt-cache](http://linux.die.net/man/8/apt-cache)

- And this command will show what's installed (or waiting to be removed) on your system:

dpkg --get-selections

- It will be a huge list, so it's probably better to redirect the output into a text file:

dpkg --get-selections > filename.txt

Hi there,

Tried the commands, 

they did work but not exactly the way I need. I was trying to find a version of glibc installed but 
$apt-cache show glibc 
or 
$dpkg -s glibc

would not return any results. So, after digging a little I stumled upon the status file in /var/lib/dpkg
searched for "glibc" in it and found what I was looking for. Not the most elegant way to do it I'm sure but it did work. I know I could find out the version of glibc from synaptic or ubuntu release description but for something like this i prefer to use the terminal.

P.S.  $dpkg --get-selections > filename.txt     did create a list of libraries where I've found libc6.

---

